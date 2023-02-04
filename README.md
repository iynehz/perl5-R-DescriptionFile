[![Build Status](https://travis-ci.org/iynehz/perl5-R-DescriptionFile.svg?branch=master)](https://travis-ci.org/iynehz/perl5-R-DescriptionFile)

# NAME

R::DescriptionFile - R package DESCRIPTION file parser

# VERSION

version 0.005

# SYNOPSIS

    use R::DescriptionFile;

    my $desc1 = R::DescriptionFile->parse_file("DESCRIPTION");
    print $desc1->{'Description'};
    print $desc1->get('Depends');

    my $desc2 = R::DescriptionFile->parse_text($desc_file_text);

# DESCRIPTION

This module provides a parser for R's `DESCRIPTION` file which is shipped 
with a R package and contains meta data of the R package. 

`parse_file()` or `parse_text()` returns object of this module class. It's
a blessed hash, so fields of DESCRIPTION can be accessed via hash keys. There
is also a `get` method which does the same thing. 

For dependency fields like `Depends`, `Suggests`, `Imports`, `LinkingTo`,
`Enhances`, they would be parsed to hashrefs of the form
`{ pkgname => version_spec }`, where version spec is either like
`(>= 1.0)`, or an empty string if it's not defined.

For list fields like `URL`, `Additional_repositories`, `VignetteBuilder`,
they would be parsed to arrayrefs.

# SEE ALSO

R DESCRIPTION file spec:
[https://cran.r-project.org/doc/manuals/r-release/R-exts.html#The-DESCRIPTION-file](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#The-DESCRIPTION-file)

# AUTHOR

Stephan Loyd <sloyd@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2018-2023 by Stephan Loyd.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
