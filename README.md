# Sample Font

This is a sample font repository, based on the [Unified Font Repository v2.0](https://github.com/raphaelbastide/Unified-Font-Repository), a standard way to organize font project source files. I have expanded upon this structure to make something that generally works for me.

I have adopted this structure because it keeps my project folders organized and predictable. Knowing nothing about a font or its development, I can come to a repository and have a sense of where the latest and greatest fonts are, and what the family is like. It allows me to write scripts that can make assumptions about where the latest masters are and where the fonts should go.

This README, and other files in the repository, are in Markdown format (you might know it ias the syntax used in WriterPro). It is worth familiarizing yourself with [Markdown’s basic syntax](https://daringfireball.net/projects/markdown/syntax).

Below is a quick rundown of the contents of this repository.

## /sources

All of your UFOs go in here. The idea is to be predictable. No UFOs are stored in the main folder; all are stored in a subfolder that describes the type of source. You can add as many source categories as the project requires, but we can expect the primary data to reside in two directories, `/1-drawing` and `/2-build`. The sources folder can also contain other file formats for dealing with sources such as Superpolator files.

### /sources/1-drawing

This directory contains the "masters", namely the UFOs that you are drawing in. These sources can be somewhat "under construction", and can include scrap glyphs, double encodings, and other shortcuts that may not make it into the final fonts. 

*If I want to expand this family, this is where I will start.*

### /sources/2-build

This contains the UFOs that are used when generating font data. This will include interpolated instances, and fonts that have had scrap glyphs removed and are otherwise mastered and ready for generation.

*If I want to generate some fonts from UFO, this is where I will start.*

### /sources/features

It is not necessary to store your features in a separate file or folder, but it makes sense if your features will be shared across sources. In your UFO,

    ../features/Sample_Font.fea

## /fonts

This folder contains a copy of the most recent version of generated fonts.

*If I want to grab the latest and greatest fonts, this is where I will start.*

## /dist

This folder contains an archive of the generated fonts of major versions. While it is possible to go back in time and retrieve old files using Git, it seems to make sense to store major iterations of the font here for easy access.

## /documentation

This directory is primarily intended for documents that describe how to use the font and how to edit it. These can be written in Markdown format.

I have also been using this directory as a place to store proofs, reference files, and other secondary files that I have used in the design process and want to keep with my font files.

## /scripts

A directory of development tools that are specific to this typeface.

## /website

If you are developing a minisite, you can put the files for that here. 

If you would like to use this website on GitLab's servers (at least as a playground), add `.gitlab-ci.yml` to the project’s root directory. The URL for this website is [http://*username*.gitlab.com/*your_font_name*](http://djrrb.gitlab.com/sample_font).

Here is a sample `.gitlab-ci.yml` file, that will run a build to create the website from the `/website` diretory when the repository is updated.

    pages:
      stage: deploy
      script:
      - cp -r website .public
      - mv .public public
      artifacts:
        paths:
        - public
      only:
      - master

## Other files in the root directory

### README.md

A space for basic information about the typeface.

### LICENSE.txt

Either a link or the full text for the font’s license.

### FONTLOG.md

A simple space to keep track of major revisions to the font.

### METADATA.yml

This contains searchable metadata in [YAML](https://en.wikipedia.org/wiki/YAML) that we can use to tag, categorize, and search through the UFO library. I’m still figuring out the best way to use this file, but for now it has the following structure:

#### Information about the repository itself:
* unified font repository version: "0.2"
* unified font repository url: https://github.com/raphaelbastide/Unified-Font-Repository/

#### Information about the typeface family:
* name
* tags
* repository url
* project url
* project status (released, gamma, beta, alpha)
* tools (used to create the typeface)
* similar fonts
* sample text

### COPYRIGHT.md & TRADEMARK.md

Simple spaces to keep track of important of the copyright and trademark status of the typeface.