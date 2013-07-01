Tools for Funding Software Development
======================================

Funding software development should be easier. This project contains a suite 
of software tools to help make it easier to donate funds to a variety of
open source software developers and organizations.

How it Works
============

The simplest way to understand how this software suite works is to check out
a few examples.

To donate $5 to the Apache Software Foundation:

    > donate 5 apache

To donate $5 to a person with an e-mail address:

    > donate 5 jane@example.org

To donate to a project that has a git repository:

    > git clone git@github.com:project/example.git
    > cd example
    > donate 5

The DONATE file format
======================

The examples above are powered by a file format that lists how the donation
should be processed. The file format is pretty simple, having one or more
entries that follow the format below:

    payment_method details
    
Valid values are:

    payment_method := 'payswarm' | 'url' | 'bitcoin'
    details := url | percentage WHITESPACE url
    percentage := integer or decimal number
    url := any valid URL (technically, any valid IRI)
    WHITESPACE := \t | ' '

All percentages for the same payment type should add up to 100.
Any line that does not match the pattern above is ignored, which
means that a DONATE file can also be used to explain what the
funds are typically used for.

PaySwarm Donations
==================

If you are using PaySwarm, entries look like the following:

    payswarm 70 https://meritora.com/i/joe-example/accounts/open-source
    payswarm 30 https://meritora.com/i/bob-example/accounts/donations

Bitcoin Donations (future)
==========================

To donate to bitcoin addresses, you could do the following:

    bitcoin 100 1PC9aZC4hNX2rmmrt7uHTfYAS3hRbph4UN

URL Donations (future)
======================

If you are using a proprietary web-based payment solution, you can request
that a web browser is opened to a particular URL. For example, the 
following would perform a PayPal donation:

    url https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ABCDEFG1234567
