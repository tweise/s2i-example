# Example for building a Flink container using S2I

## Building the example

Install S2I on macOS:

`brew install source-to-image`

(other platforms see: https://github.com/openshift/source-to-image#installation)

Create the builder image:

`docker build -t flink-builder-image ./builder-image`

Build the application container:

`s2i build . flink-builder-image s2i-test --copy`

## S2I pointers

Simple Example:

https://github.com/debianmaster/openshift-java-s2i-example

Creating Images (and the s2i scripts):

https://docs.openshift.com/online/creating_images/s2i.html#build-process
