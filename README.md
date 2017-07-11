# tinfoil
TLS Is Not For Obligatory Interception Lovers

This reposotiry is a place to collect together arguments
for not breaking TLS.

At some point it may be worth turning this into an
Internet-draft to save us all time for when the next
crappy break-TLS proposal comes along.

PRs that add to (really, record) those arguments are
welcome, especially if they identify problems with specific 
proposals to break TLS.

## Meta-Points

In this section we call out some generic issues that all
cause all "break-TLS" proposals fail.

- As with most of these break-TLS attempts, the proponents
have apparently only analysed the deployments about which
they care, and ignore all other uses of TLS. There are
many other uses of TLS, for example the TLS1.2 RFC is
currently (20170711) [referenced by](https://datatracker.ietf.org/doc/rfc5246/referencedby/) 434 other IETF specifications, and 
is [cited](https://scholar.google.com/scholar?q=http%3A%2F%2Fwww.hjp.at%2Fdoc%2Frfc%2Frfc5246.html&btnG=&hl=en&as_sdt=0%2C5) by 3,281 publications
in Google Scholar. Screwing around with such a protocol without
due dilligence is utterly unwise.


## [draft-green-tls-static-dh-in-tls13-01](https://tools.ietf.org/html/draft-green-tls-static-dh-in-tls13-01)

This is one of the current proposals for breaking TLS.
It fails in the following ways:

- The [TLS working group charter](https://tools.ietf.org/wg/tls/charters)
dated 2017-03-30 calls for improving the security of TLS, and 
this proposal involves leaking private key material and hence
falls outside the charter.

- This draft is targeted as being an IETF standards track document
but is a wiretapping scheme that meets the definition in
[RFC2804](https://tools.ietf.org/html/rfc2804) and therefore
cannot be a standards-track work item in the IETF.

- This draft aims to provide wiretapping only "within"
enterprise networks, but there is no way (and cannot be a way)
to constrain the use of this scheme to such networks.
Figure 3 of the draft clearly describes a generic 
wiretapping architecture for TLS that could (and would)
be used in many other circumstances that the authors
have apparently not envisaged.

- This draft tries to standardise broken crypto - forward
secrecy is a goal of cryptographic protocols and this 
draft deliberately aims to not provide forward secrecy
and indeed to break forward secrecy without the TLS
client being aware of that.

- This draft doesn't allow TLS clients and applications
above or behind the TLS server to know that wiretapping
is occurring.

### Why is this wiretapping?

Some of the authors have denied that this is a wiretapping
propospal, based on not matching the definitions in RFC2804.
However, with SMTP/TLS and with any intermediate MTA, this
clearly allows that intermediate MTA to renege and leak
their private values and hence senders and recipients will
not get the confidentiality they expect. Note that SMTP/TLS
is almost ubiquituous today and that 2-TLS session setups
are common, e.g. if the intermediary MTA does AV scanning.



## Feel free to add older/other break-TLS proposal debunking text below here.

For example, about mcTLS, if you have the energy to
consider that nonsense.


