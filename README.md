Python wrapper for semicomplete's Grok library.

About
-----
Grok allows you to easily parse logs and other files and turns the unstructured
log and event data into structured data.

Installing
----------

You will need libgrok installed in other to use libgrok-py. On MacOSX this is available via Homebrew:

Install Grok Dependencies
    brew install tokyo-cabinet pcre libevent

Install Grok
    brew install grok

You can also compile from source.


Usage
-----

    >>> import libgrok
    >>> grok = libgrok.Grok()
    >>> grok.add_patterns_from_file('test/patterns/base')
    >>> grok.compile('%{URI:foo}')
    >>> match = grok("http://www.example.com/test/")
    >>> match.captures.items()
    [('USERNAME', ''), ('HOSTNAME', 'www.example.com'), ('URIPATH', '/test/'), ('IPORHOST', 'www.example.com'), ('POSINT:port', ''), ('URIPROTO', 'http'), ('IP', ''), ('URIHOST', 'www.example.com'), ('URIPATHPARAM', '/test/'), ('URI:foo', 'http://www.example.com/test/'), ('URIPARAM', ''), ('USER', '')]
