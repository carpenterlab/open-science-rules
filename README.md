# Ten Simple Rules for Using Open Science in Biomedical Research

[![HTML Manuscript](https://img.shields.io/badge/manuscript-HTML-blue.svg)](https://carpenterlab.github.io/open-science-rules/)
[![PDF Manuscript](https://img.shields.io/badge/manuscript-PDF-blue.svg)](https://carpenterlab.github.io/open-science-rules/manuscript.pdf)
[![Build Status](https://travis-ci.com/carpenterlab/open-science-rules.svg?branch=master)](https://travis-ci.com/carpenterlab/open-science-rules)

## Manuscript description

The collaboratively written manuscript will provide ten rules for effectively using open science in biomedical research.
Written in the style of the [PLOS ten simple rules collections](https://collections.plos.org/ten-simple-rules), the manuscript is aimed at a larger audience of biomedical researchers.
Our goal is to introduce, describe, and guide scientists towards open science research policies while acknowledging legitimate barriers of adoption.
For many, simply having an open discussion about open science is beneficial.

Open science is an approach to research that makes all data, software, results, and discussions freely available from the beginning of a project and throughout development.
Open science ties together computational biology and software development best practices with scientific discovery and dissemination.
A brief figure below outlines the approach.

![Open Science Figure](open-science-overview.png)

## Current Status (17 July 2019)

The manuscript begins!
We are beginning to brainstorm and discuss open science rules and open science papers in [github issues](https://github.com/carpenterlab/open-science-rules/issues).
See [#1](https://github.com/carpenterlab/open-science-rules/issues/1) for more details about the current scope and purpose of the paper.

We are also soliciting contributions!
Open science is most effective by leveraging the skills and expertise of current practitioners.
Written in the style of [deep-rules](https://github.com/Benjamin-Lee/deep-rules) and the [deep-review](https://github.com/greenelab/deep-review), the open-science-rules repository will be a place to learn about open science and will also serve as the framework to draft the actual manuscript.

The manuscript is written using [Manubot](https://doi.org/10.1371/journal.pcbi.1007128).

## Manubot

<!-- usage note: do not edit this section -->

Manubot is a system for writing scholarly manuscripts via GitHub.
Manubot automates citations and references, versions manuscripts using git, and enables collaborative writing via GitHub.
An [overview manuscript](https://greenelab.github.io/meta-review/ "Open collaborative writing with Manubot") presents the benefits of collaborative writing with Manubot and its unique features.
The [rootstock repository](https://git.io/fhQH1) is a general purpose template for creating new Manubot instances, as detailed in [`SETUP.md`](SETUP.md).
See [`USAGE.md`](USAGE.md) for documentation how to write a manuscript.

Please open [an issue](https://git.io/fhQHM) for questions related to Manubot usage, bug reports, or general inquiries.

### Repository directories & files

The directories are as follows:

+ [`content`](content) contains the manuscript source, which includes markdown files as well as inputs for citations and references.
  See [`USAGE.md`](USAGE.md) for more information.
+ [`output`](output) contains the outputs (generated files) from Manubot including the resulting manuscripts.
  You should not edit these files manually, because they will get overwritten.
+ [`webpage`](webpage) is a directory meant to be rendered as a static webpage for viewing the HTML manuscript.
+ [`build`](build) contains commands and tools for building the manuscript.
+ [`ci`](ci) contains files necessary for deployment via continuous integration.
  For the CI configuration, see [`.travis.yml`](.travis.yml).

### Local execution

The easiest way to run Manubot is to use [continuous integration](#continuous-integration) to rebuild the manuscript when the content changes.
If you want to build a Manubot manuscript locally, install the [conda](https://conda.io) environment as described in [`build`](build).
Then, you can build the manuscript on POSIX systems by running the following commands from this root directory.

```sh
# Activate the manubot conda environment (assumes conda version >= 4.4)
conda activate manubot

# Build the manuscript, saving outputs to the output directory
bash build/build.sh

# At this point, the HTML & PDF outputs will have been created. The remaining
# commands are for serving the webpage to view the HTML manuscript locally.
# This is required to view local images in the HTML output.

# Configure the webpage directory
python build/webpage.py

# You can now open the manuscript webpage/index.html in a web browser.
# Alternatively, open a local webserver at http://localhost:8000/ with the
# following commands.
cd webpage
python -m http.server
```

Sometimes it's helpful to monitor the content directory and automatically rebuild the manuscript when a change is detected.
The following command, while running, will trigger both the `build.sh` and `webpage.py` scripts upon content changes:

```sh
bash build/autobuild.sh
```

### Continuous Integration

[![Build Status](https://travis-ci.com/carpenterlab/open-science-rules.svg?branch=master)](https://travis-ci.com/carpenterlab/open-science-rules)

Whenever a pull request is opened, Travis CI will test whether the changes break the build process to generate a formatted manuscript.
The build process aims to detect common errors, such as invalid citations.
If your pull request build fails, see the Travis CI logs for the cause of failure and revise your pull request accordingly.

When a commit to the `master` branch occurs (for example, when a pull request is merged), Travis CI builds the manuscript and writes the results to the [`gh-pages`](https://github.com/carpenterlab/open-science-rules/tree/gh-pages) and [`output`](https://github.com/carpenterlab/open-science-rules/tree/output) branches.
The `gh-pages` branch uses [GitHub Pages](https://pages.github.com/) to host the following URLs:

+ **HTML manuscript** at https://carpenterlab.github.io/open-science-rules/
+ **PDF manuscript** at https://carpenterlab.github.io/open-science-rules/manuscript.pdf

For continuous integration configuration details, see [`.travis.yml`](.travis.yml).

## License

<!--
usage note: edit this section to change the license of your manuscript or source code changes to this repository.
We encourage users to openly license their manuscripts, which is the default as specified below.
-->

[![License: CC BY 4.0](https://img.shields.io/badge/License%20All-CC%20BY%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by/4.0/)
[![License: CC0 1.0](https://img.shields.io/badge/License%20Parts-CC0%201.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

Except when noted otherwise, the entirety of this repository is licensed under a CC BY 4.0 License ([`LICENSE.md`](LICENSE.md)), which allows reuse with attribution.
Please attribute by linking to https://github.com/carpenterlab/open-science-rules.

Since CC BY is not ideal for code and data, certain repository components are also released under the CC0 1.0 public domain dedication ([`LICENSE-CC0.md`](LICENSE-CC0.md)).
All files matched by the following glob patterns are dual licensed under CC BY 4.0 and CC0 1.0:

+ `*.sh`
+ `*.py`
+ `*.yml` / `*.yaml`
+ `*.json`
+ `*.bib`
+ `*.tsv`
+ `.gitignore`

All other files are only available under CC BY 4.0, including:

+ `*.md`
+ `*.html`
+ `*.pdf`
+ `*.docx`

Please open [an issue](https://github.com/carpenterlab/open-science-rules/issues) for any question related to licensing.
