# summary: A Plugin for Pelican

[![Build Status](https://img.shields.io/github/workflow/status/pelican-plugins/summary/build)](https://github.com/pelican-plugins/summary/actions) [![PyPI Version](https://img.shields.io/pypi/v/pelican-summary)](https://pypi.org/project/pelican-summary/)

This plugin allows easy, variable length summaries directly embedded into the
body of your articles. It introduces two new settings: `SUMMARY_BEGIN_MARKER`
and `SUMMARY_END_MARKER`: strings which can be placed directly into an article
to mark the beginning and end of a summary. When found, the standard
`SUMMARY_MAX_LENGTH` setting will be ignored. The markers themselves will also
be removed from your articles before they are published. The default values
are `<!-- PELICAN_BEGIN_SUMMARY -->` and `<!-- PELICAN_END_SUMMARY -->`.
For example::

    Title: My super title
    Date: 2010-12-03 10:20
    Tags: thats, awesome
    Category: yeah
    Slug: my-super-post
    Author: Alexis Metaireau

    This is the content of my super blog post.
    <!-- PELICAN_END_SUMMARY -->
    and this content occurs after the summary.

Here, the summary is taken to be the first line of the post. Because no
beginning marker was found, it starts at the top of the body. It is possible
to leave out the end marker instead, in which case the summary will start at the
beginning marker and continue to the end of the body.

If no beginning or end marker is found, and if `SUMMARY_USE_FIRST_PARAGRAPH`
is enabled in the settings, the summary will be the first paragraph of the post.

The plugin also sets a `has_summary` attribute on every article. It is True
for articles with an explicitly-defined summary, and False otherwise.  (It is
also False for an article truncated by `SUMMARY_MAX_LENGTH`.)  Your templates
can use this e.g. to add a link to the full text at the end of the summary.

### reST example

Inserting the markers into a reStructuredText document makes use of the
comment directive, because raw HTML is automatically escaped. The reST equivalent of the above Markdown example looks like this:

    My super title
    ##############

    :date: 2010-12-03 10:20
    :tags: thats, awesome
    :category: yeah
    :slug: my-super-post
    :author: Alexis Metaireau

    This is the content of my super blog post.

    .. PELICAN_END_SUMMARY

    and this content occurs after the summary.

Installation
------------

This plugin can be installed via:

    python -m pip install pelican-summary

Contributing
------------

Contributions are welcome and much appreciated. Every little bit helps. You can contribute by improving the documentation, adding missing features, and fixing bugs. You can also help out by reviewing and commenting on [existing issues][].

To start contributing to this plugin, review the [Contributing to Pelican][] documentation, beginning with the **Contributing Code** section.

[existing issues]: https://github.com/pelican-plugins/summary/issues
[Contributing to Pelican]: https://docs.getpelican.com/en/latest/contribute.html
