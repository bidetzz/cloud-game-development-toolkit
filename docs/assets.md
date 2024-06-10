# Assets

**Assets** are reusable scripts, pipeline definitions, Dockerfiles, Packer templates, and other resources that might prove useful or are dependencies of any of the modules. Each asset contains its own documentation as a `README.md` file. 

!!! info
    **Don't see an asset listed?** Create a [feature request](https://github.com/aws-games/cloud-game-development-toolkit/issues/new?assignees=&labels=feature-request&projects=&template=feature_request.yml&title=Feature+request%3A+TITLE) for a new asset or learn [how to contribute new assets to the project below](#Contribute new Assets to the Cloud Game Development Toolkit)

## Packer Templates

Packer templates provide an easy way to build machine images for commonly used game dev infrastructure. Currently the project includes Packer templates for UE5 build agents for Linux and Windows, as well as a Packer template for building a Perforce Helix Core version control AMI.

- **[Unreal Engine Build Agents](#unreal-engine-build-agents)**: Packer templates for building Unreal Engine on Windows and Linux, including support for x86 and ARM (i.e. Graviton).
- **[Perforce Helix Core AMI](#perforce-helix-core-packer-template)**: Packer templates for creating an Amazon Machine Image (AMI) of Perforce Helix Core on Linux and configuration with Perforce Server Deployment Package (SDP)

<!-- Build Agents README #unreal-engine-build-agents -->
--8<-- "assets/packer/build-agents/README.md"

<!-- Perforce Helix Core README #perforce-helix-core-ami -->
--8<-- "assets/packer/perforce/helix-core/README.md"

## Dockerfiles

Dockerfiles for creating Docker images of commonly used game dev infrastructure. 

## Contribute new Assets to the Cloud Game Development Toolkit

This section will contain documentation about how to create new assets, how they should be tested and documented, and the process for submitting them as PRs to the project.