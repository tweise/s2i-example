# Example for building a Flink container using S2I

## Building the example

Install S2I on macOS:

`brew install source-to-image`

(other platforms see: https://github.com/openshift/source-to-image#installation)

Create the builder image:

`docker build -t flink-builder-image ./builder-image`

Build the application container:

`s2i build . flink-builder-image s2i-test --copy`

Use `--copy` to pick up local uncommitted changes for the build.

Incremental build (restore .m2 from previous image instead for pulling from central):

`s2i build . flink-builder-image s2i-test --loglevel 1 --incremental`

## Run example

`docker run -p 8081:8081 s2i-test:latest local`

`docker exec -it db552d50f890 bash`

https://ci.apache.org/projects/flink/flink-docs-release-1.4/quickstart/setup_quickstart.html

## References

Simple S2I Example:

https://github.com/debianmaster/openshift-java-s2i-example

Creating S2I Images (and the s2i scripts):

https://docs.openshift.com/online/creating_images/s2i.html#build-process

Apache Flink Docker:

https://github.com/docker-flink/docker-flink
