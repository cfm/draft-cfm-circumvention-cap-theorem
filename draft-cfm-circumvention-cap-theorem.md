---
title: Towards a CAP Theorem for Censorship Circumvention
category: info

docname: draft-cfm-circumvention-cap-theorem-latest
submissiontype: independent
number:
date:
v: 3
venue:
  group: BIAS
  type: Workshop
  github: cfm/draft-cfm-circumvention-cap-theorem

author:
 - fullname: Cory Myers
   organization: ARTICLE 19
   email: cfm@acm.org

normative:

informative:
  biasws:
    title: "Workshop on Barriers to Internet Access of Services"
    target: https://datatracker.ietf.org/group/biasws/about/
    author:
      organization: Internet Architecture Board
    date: 2023-09-20
  cap-theorem:
    title: "CAP theorem"
    target: https://en.wikipedia.org/wiki/CAP_theorem
  tor-relays-2022-07:
    title: "We're trying out guard-n-primary-guards-to-use=2"
    target: https://lists.torproject.org/pipermail/tor-relays/2022-July/020686.html
    author:
      name: Roger Dingledine
    date: 2022-07-06
  tor-relays-2022-10:
    title: "DoS attacks -- status update"
    target: https://lists.torproject.org/pipermail/tor-relays/2022-October/020858.html
    author:
      name: Georg Koppen
    date: 2022-10-28
  tor-status:
    title: "Network DDoS"
    target: https://status.torproject.org/issues/2022-06-09-network-ddos/
    author:
      organization: Tor Project
    date: 2022-06-09


--- abstract

This Internet-Draft is a submission to the IAB Workshop on Barriers to Internet
Access of Services {{biasws}}.


--- middle

# Research Proposal

Between June 2022 and April 2023 {{tor-status}}, the Tor network was the target
of a sustained distributed denial-of-service (DDoS) attack, apparently targeting
the relays and directory servers that coordinate introductions to Tor hidden
services {{tor-relays-2022-07}} {{tor-relays-2022-10}}.  This attack impeded the
performance and threatened the security of the Tor network for all users.  It
especially obstructed Web sites and services that had gone out of their way to
be accessible to Tor users via Tor hidden services, which usually improve the
performance of the Tor network by bypassing the "exit nodes" that interface with
the clearnet Internet.

Although the origins and motivations of this attack remain unknown, it is a
useful case study in the D/DoS vulnerability of overlay networks such as Tor,
which users may seek out to protect their anonymity, circumvent censorship, or
both.  The CAP theorem {{cap-theorem}} is instructive: like a database, a
censorship-circumvention system is useful to the extent that it is:

1. **consistent:** returns accurate and current data;

2. **available:** returns data at all; and

3. **partition-tolerant**: routes around failures, which by definition include
   active censorship.  In this case, they also include active *attacks*
   on circumvention infrastructure that lessen its overall availability,
   whether or not intended as an act of censorship.

For the workshop, I propose to explore further whether formalisms such as the
CAP theorem are useful models and/or measures for the utility and resilience of
a censorship-circumvention system such as Tor.
