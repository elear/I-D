---
title: The application/proxy-explanation+json media type
abbrev: Proxy Explanations
docname: draft-nottingham-proxy-explanation-01
date: 2016
category: info

ipr: trust200902
area: General
workgroup: 
keyword: Internet-Draft

stand_alone: yes
pi: [toc, tocindent, sortrefs, symrefs, strict, compact, comments, inline]

author:
 -
    ins: M. Nottingham
    name: Mark Nottingham
    organization: 
    email: mnot@mnot.net
    uri: https://www.mnot.net/

normative:
  RFC2119:
  RFC3986:
  RFC6838:
  RFC7159:
  RFC7230:
  RFC7231:
  RFC7234:

informative:


--- abstract

This specification defines the application/proxy-explanation+json media type, to allow HTTP proxies to explain to clients why a request is unsuccessful.

--- note_Note_to_Readers

The issues list for this draft can be found at <https://github.com/mnot/I-D/labels/proxy-explanation>.

The most recent (often, unpublished) draft is at <https://mnot.github.io/I-D/proxy-explanation/>.

Recent changes are listed at <https://github.com/mnot/I-D/commits/gh-pages/proxy-explanation>.


--- middle

# Introduction

HTTP requests {{RFC7230}} to a proxy might not succeed variety of reasons; the request itself might violate a policy, or the requested content might be deemed unacceptable (e.g., it contains a virus, or itself violate a policy being imposed by the proxy).

For HTTP URLs, information about the reason is often injected into the HTTP response, so that the user understands what has happened, even if the message is only an HTML "Access Denied." This practice is problematic, because both users and non-browser clients can become confused about the source of the information, mistaking content from the proxy as being from the origin.

Furthermore, for HTTPS URLs, there is no way for the proxy to inform the end user about its actions. Proxies could provide HTML content in a 403 (Forbidden) response, but browsers are unwilling to show this to end users, since doing so would subject them to a potential man-in-the-middle attack.

This specification defines a new response format with a constrained vocabulary, so that proxies can communicate basic information about why a request has not succeeded, and browsers can provide that information to users without risking it being mistaken for an authoritative response from the origin server.


## Notational Conventions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT",
"RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in
{{RFC2119}}.

# The application/proxy-explanation+json Media Type

The "application/proxy-explanation+json" media type denotes a JSON {{RFC7159}} format whose root is an object containing the following members:

* **name** - A short string identifying the party operating the proxy
* **title** - A short string title for the explanation
* **description** - A string explaining why the request wasn't successful
* **moreinfo** - A string containing an absolute URL {{RFC3986}} which the user can find relevant information.

The "name" and "title" members MUST be present; all other members are OPTIONAL.

This media type MUST NOT be generated by origin servers and gateway servers (i.e., "reverse proxies" and "content delivery networks"); it is only intended to be generated by proxies. It MAY be generated by interception proxies (so-called "transparent proxies"), although as per below, it might be ignored by clients in this case.

It MUST NOT be used with a 2xx or 3xx status code, and clients MUST ignore its presence on them. Typical status codes that it will be used with include 403 (Forbidden), 451 (Unavailable For Legal Reasons), 502 (Bad Gateway), and 504 (Gateway Timeout).

Proxies SHOULD carefully consider what caching metadata {{RFC7234}} is appropriate to include in such responses.

Clients MAY selectively support this media type. For example, an implementation might deem it only useful (or safe) in CONNECT requests.

Clients SHOULD indicate that they support this media type by including it in the field-value of the Accept request header field {{RFC7231}} of all supported requests.


## Example

For example:

~~~ example
    CONNECT www.example.net:80 HTTP/1.1
    Host: www.example.net
    Accept: application/proxy-explanation+json
    Accept-Language: en-us

    HTTP/1.1 403 Forbidden
    Content-Type: application/proxy-explanation+json
    Cache-Control: no-cache
    
    {
      "name": "Acme Networks"
      "title": "Policy Violation"
      "description": "This content is above your pay grade."
      "moreinfo": "https://acme.example.com/why?https://www.example.net"
    }
~~~

A browser might display this to the end user in a manner similar to this:

~~~ example
    Policy Violation
    
    The proxy "Acme Networks" says:
    
      This content is above your pay grade.
    
    For more information, see: 
      "https://acme.example.com/why?https://www.example.net"
~~~


# IANA Considerations

This specification defines a new Internet Media Type {{RFC6838}}:

* Type name: application
* Subtype name: proxy-explanation+json
* Required parameters: None
* Optional parameters: None; unrecognised parameters should be ignored
* Encoding considerations: Same as {{RFC7159}}
* Security considerations: See {{security}}
* Interoperability considerations: None
* Published specification: [this document]
* Applications that use this media type: HTTP
* Fragment identifier considerations: Same as {{RFC7159}}
* Additional information:
  * Deprecated alias names for this type: N/A
  * Magic number(s): N/A
  * File extension(s): N/A
  * Macintosh file type code(s): N/A
* Person & email address to contact for further information: Mark Nottingham <mnot@mnot.net>
* Intended usage: COMMON
* Restrictions on usage: N/A
* Author: Mark Nottingham <mnot@mnot.net>
* Change controller: IESG

# Security Considerations {#security}

The approach taken in this specification precludes a proxy presenting itself as the origin, provided that, when presented to the user, the information is sufficiently contextualised as being from the proxy. 

This approach does not preclude an origin server presenting itself as a the proxy, in cases where the client supports the media type on requests other than CONNECT. 

Likewise, it does not prevent a man-in-the-middle from presenting itself as a proxy, in cases where the connection is unencrypted.

Because the payload can contain a URL, it could be used by an attacker (either a hostile origin or MitM, as above) to direct users to an origin under their control. For example, an attacker could convince users that they need to provide payment before the network is available. 

An attacker could also include a URL in the textual content of its message (e.g., in the `description` member), to encourage the user to copy the link and follow it.

However, both origins and cleartext MitMs can misrepresent their identities on the Web currently, without the benefit of this mechanism. These risks are introduced only when users trust the "proxy" interface more than they would trust a "normal" Web site.

They can be mitigated in a few ways:

* Not displaying the `moreinfo` member in situations when this is possible (i.e., on any response other than that to a CONNECT on an encrypted connection).
* Not supporting the `application/proxy-connection+json` media type when the method is not CONNECT and the connection is not encrypted.
* Cautioning the user that the content might not be trustworthy. 


--- back


# Acknowledgements

Thanks to Thomas Mangin for his suggestions.
