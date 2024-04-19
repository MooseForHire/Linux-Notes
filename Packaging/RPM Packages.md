
An RPM package is a file containing other files and their metadata (information about the files that are needed by the system).

Specifically, an RPM package consists of the `cpio` archive.

The `cpio` archive contains:

- Files
- RPM header (package metadata)
    
    The `rpm` package manager uses this metadata to determine dependencies, where to install files, and other information.


##### Types of RPM packages

There are two types of RPM packages. Both types share the file format and tooling, but have different contents and serve different purposes:

- Source RPM (SRPM)
    
    An SRPM contains source code and a SPEC file, which describes how to build the source code into a binary RPM. Optionally, the patches to source code are included as well.
    
- Binary RPM
    
    A binary RPM contains the binaries built from the sources and patches.

