---
title: The Internet is for End Users
docname: draft-nottingham-for-the-users-07
date: 2019
category: info

ipr: trust200902
area: General
workgroup:
keyword: constituent
keyword: constituency
keyword: relevant parties
keyword: end users
keyword: endpoint
keyword: stakeholder

stand_alone: yes
pi: [toc, tocindent, sortrefs, symrefs, strict, compact, comments, inline]

author:
 -
    ins: M. Nottingham
    name: Mark Nottingham
    organization:
    email: mnot@mnot.net
    uri: https://www.mnot.net/

informative:
  CODELAW:
    target: http://harvardmagazine.com/2000/01/code-is-law-html
    title: "Code Is Law: On Liberty in Cyberspace"
    author:
      -
        ins: L. Lessig
        name: Lawrence Lessig
        organization: Harvard Magazine
    date: 2000


--- abstract

This document explains why, when a conflict cannot be avoided, the IETF considers end users as
its highest priority concern.


--- note_Note_to_Readers

The issues list for this draft can be found at <https://github.com/mnot/I-D/labels/for-the-users>.

The most recent (often, unpublished) draft is at <https://mnot.github.io/I-D/for-the-users/>.

Recent changes are listed at <https://github.com/mnot/I-D/commits/gh-pages/for-the-users>.

See also the draft's current status in the IETF datatracker, at
<https://datatracker.ietf.org/doc/draft-nottingham-for-the-users/>.

--- middle

# Introduction

The IETF, while focused on technical matters, is not neutral about the purpose of its work in
developing the Internet; in "A Mission Statement for the IETF" {{?RFC3935}}, the definitions include:

> The IETF community wants the Internet to succeed because we believe that the existence of the Internet, and its influence on economics, communication, and education, will help us to build a better human society.

and later in Section 2.1, "The Scope of the Internet" it says:

> The Internet isn't value-neutral, and neither is the IETF. We want the Internet to be useful for communities that share our commitment to openness and fairness. We embrace technical concepts such as decentralized control, edge-user empowerment and sharing of resources, because those concepts resonate with the core values of the IETF community. These concepts have little to do with the technology that's possible, and much to do with the technology that we choose to create.

However, many in the IETF are most comfortable making what we believe to be purely technical
decisions; our process is defined to favor technical merit, through our well-known bias towards
"rough consensus and running code".

Nevertheless, the running code that results from our process (when things work well) inevitably has
an impact beyond technical considerations, because the underlying decisions afford some uses while
discouraging others; while we believe we are making purely technical decisions, in reality that may
not be possible. Or, in the words of Lawrence Lessig {{CODELAW}}:

> Ours is the age of cyberspace. It, too, has a regulator... This regulator is code — the software and hardware that make cyberspace as it is. This code, or architecture, sets the terms on which life in cyberspace is experienced. It determines how easy it is to protect privacy, or how easy it is to censor speech. It determines whether access to information is general or whether information is zoned. It affects who sees what, or what is monitored. In a host of ways that one cannot begin to see unless one begins to understand the nature of this code, the code of cyberspace regulates.

This impact has become significant. As the Internet increasingly mediates key functions in
societies, it has unavoidably become profoundly political; it has helped people overthrow
governments and revolutionize social orders, control populations and reveal secrets. It has created
wealth for some individuals and companies, while destroying others'.

All of this raises the question: For whom do we go through the pain of gathering rough consensus
and writing running code?

There are a variety of identifiable parties in the larger Internet community that standards can
provide benefit to, such as (but not limited to) end users, network operators, schools, equipment
vendors, specification authors, specification implementers, content owners, governments,
non-governmental organisations, social movements, employers, and parents.

Successful specifications will provide some benefit to all of the relevant parties, because
standards do not represent a zero-sum game. However, there are sometimes situations where there is
a need to balance the benefits of a decision between two (or more) parties.

In these situations, when one of those parties is an "end user" of the Internet -- for example, a
person using a Web browser, mail client, or other agent that connects to the Internet -- the IETF
tends to protect their interests over those of parties such as network operators or equipement
vendors.

This document explains what is meant by "end users" in {{who}}, why they tend to be prioritised in
IETF work in {{why}}, and how that is done in {{how}}.


# Who Are "End Users"? {#who}

In this document, "end users," means the billions of people whose activities IETF protocols are
designed to support, sometimes indirectly. An end user could be an individual, or it could be a
collection of them; whether that be a social movement, a business, or a government that represents
a large number of people.  An end user might be a doctor using an IP-enabled X-Ray machine, or
a first responder with other first responders in an emergency, or a student practicing a foreign
language.  An end user might be the home owner using an Internet-enabled security system, or the
people who run a large financial institution.  We are all, in one way or another, end users.

While those who build and operate networks and services are users to, our focus is on those to
whom we deliver these network functions, and not ourselves.

End users are not necessarily a homogenous group; often, but not always, interactions on
the Internet are characterised by a seller/buyer, publisher/reader, or service provider/consumer
relationship.

End users do not always have a necessarily have a passive relationship with the Internet;
someone producing content, selling goods or providing a service is equally a user of the Internet. 
The emphasis here is on "end" -- as in endpoint {{?RFC3724}}.

Similarly, a person whose interests we need to consider might not directly be an end-user of
a specific system connected to the Internet. For example, if a child is using a browser, the
interests of that child's parents or guardians may be relevant; if a person is pictured in
a photograph, that person may have an interest in systems that process that photograph, or
if a person entering a room triggers sensors that send data to the Internet than that person's
interests may be involved in our deliberations about how those sensor readings are handled.

While such less-direct interactions between people and the Internet may be harder to evaluate
compared to those involving people with accounts on some web service, such people are nonetheless
included in this document's concept of end-user.


# What does it mean to prioritise end users?  {#why}

When we design protocols and create architectural frameworks, we do so for end users, considering
their diverse, and often conflicting, needs.  Is there privacy properly protected?  Are we offering
secure mechanisms for critical infrastructure?  Conversely, are we opening end users up to either
cyber- or physical attacks?  We might in some instances be doing all of the above.  We must be
always mindful of our impact.  When our works negatively certain users, we should consider mitigations we
can recommend.

Prioritising end users helps the IETF achieve its mission, and also helps to assure the long-term
health of the Internet. By prioritising their concerns, we assure that the Internet reaches the
greatest number of people, thereby delivering greater utility by maximising its network effect.

Prioritising end users' needs also helps to assure that the Internet itself retains end users'
trust, preserving the benefit its network effect brings.

# How End Users are Prioritised {#how}

The IETF community does not have any specific insight into what is "good for end users"; to help
make decisions involving them, it interacts with the greater Internet community. Because end users
are typically not technical experts, the IETF has a responsibility to consider their interests, and
engage with those who understand the impact of our work, such as civil society
organisations, as well as governments, businesses and other groups representing some aspect of end
user interests.

When we've identified a conflict between the interests of different groups of end users, we will
be hard pressed to choose one group over another.  In this case, we should document the risks and
benefits to the different groups, and inform these groups in some manner of the potential impact
so that we can make decisions that cause the least harm.

Note that "harm" is not defined in this document; that is something that must be considered on a
case-by-case basis.

The IETF has already established a body of guidance for situations where this sort of conflict is
common, including (but not limited to) {{?RFC7754}} on filtering, {{?RFC7258}} and {{?RFC7624}} on
pervasive surveillance, {{?RFC7288}} on host firewalls, and {{?RFC6973}} regarding privacy
considerations.

When such advice is not yet available, we try to find a different solution, or another way to frame
the problem, distilling the underlying principles into more general advice where appropriate.

When the needs of different end users conflict; for example, between governments and individuals,
we again try to minimise harm -- this time, to the greatest number and most specific of end users.
In other words, when a decision improves the Internet for end users in one jurisdiction, but at the
cost of potential harm to others elsewhere, that is not a good tradeoff.

There may be cases where genuine technical need requires compromise. However, such tradeoffs are
carefully examined, and avoided when there are alternate means of achieving the desired goals. If
they cannot be, these choices and reasoning ought to be carefully documented.


## Examples

* IPv6 {{?RFC8200}} can be used to assign a client with a unique address prefix -- even though this provides a way to track end user activity and helps identify them -- because it is technically necessary to provide networking (and despite this, there are mechanisms like {{?RFC4941}} to mitigate this effect, for those users who desire it).

* Different network operator communities have, from time to time, asked for a mechanism that would allow them to insert themselves into HTTPS {{?RFC7231}} connections to interpose caching and other performance optimisations. This was rejected for a number of reasons, including that end users' conception of HTTPS as an encrypted end-to-end protocol had already formed, so that changing it would harm user security.

TODO: more examples.


# IANA Considerations

This document does not require action by IANA.

# Security Considerations

This document does not have direct security impact; however, failing to prioritise end users might
well affect their security negatively in the long term.


--- back

# Acknowledgements

Thanks to Edward Snowden for his comments regarding the priority of end users at IETF93.

Thanks to the WHATWG for blazing the trail with the Priority of Constituencies.

Thanks to Harald Alvestrand for his substantial feedback and Mohamed Boucadair, Stephen Farrell,
Joe Hildebrand, Lee Howard, Russ Housley, Niels ten Oever, Mando Rachovitsa, Martin Thomson, and
Brian Trammell for their suggestions.
