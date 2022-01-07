---
title: Stateless invoices

## Optional.  Shorter name to use for reference style links e.g., "foo"
## will allow using the link [topic foo][].  Not case sensitive
# shortname: foo

## Optional.  An entry will be added to the topics index for each alias
#aliases:
#  - Foo

## Required.  At least one category to which this topic belongs.  See
## schema for options
categories:
  - Lightning Network

## Optional.  Produces a Markdown link with either "[title][]" or
## "[title](link)"
primary_sources:
    - title: Stateless invoices with proof-of-payment
      link: https://lists.linuxfoundation.org/pipermail/lightning-dev/2021-September/003236.html

## Optional.  Each entry requires "title" and "url".  May also use "feature:
## true" to bold entry and "date"
optech_mentions:
  - title: Stateless invoices to avoid tracking unused payment requests
    url: /en/newsletters/2021/09/29/#stateless-ln-invoice-generation

  - title: "Rust-Lightning #1177 implements stateless payments using the payment secret field"
    url: /en/newsletters/2022/01/05/#rust-lightning-1177

  - title: "BOLTs #912 adds a new optional field to BOLT11 invoices to enable stateless payments"
    url: /en/newsletters/2022/01/12/#bolts-912

## Optional.  Same format as "primary_sources" above
# see_also:
#   - title:
#     link:

## Optional.  Force the display (true) or non-display (false) of stub
## topic notice.  Default is to display if the page.content is below a
## threshold word count
#stub: false

## Required.  Use Markdown formatting.  Only one paragraph.  No links allowed.
## Should be less than 500 characters
excerpt: >
  **Stateless invoices** are LN invoices whose payment preimage is
  generated deterministically from payment metadata.  This allows the
  receiver of a payment to avoid storing any data about the invoice
  until the spender submits a copy of the metadata along with the
  payment.

---

{% include references.md %}
{% include linkers/issues.md issues="" %}