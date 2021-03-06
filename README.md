# graalvm-gradle-docker

A docker image for [GraalVM](https://graalvm.org) and [Gradle](https://gradle.org) built with [sdkman](https://sdkman.io)

It also installs `native-image`

## Versions ##

- GraalVM: 21.1.0.r11-grl
- GraalVM: 21.2.0.r11-grl

## Pull image

```bash
$ docker pull bendi/graalvmgradle
```

## Run ##

The default `ENTRYPOINT` for this image is `./gradlew`.

If you want to `./gradlew clean nativeImage` your Java project, CD where the build.gradle[.kts] is located, then:

```bash
$ docker pull bendi/graalvmgradle
$ docker run -it --rm \
  -v "$PWD":/opt/app  \
  -v "$HOME"/.gradle:/root/.gradle \
  bendi/graalvmgradle \
  clean nativeImage
```

> The `-v "$HOME"/.gradle:/root/.gradle` parameter mounts your local `~/.gradle` Gradle repository as a Docker volume.

## Credits ##
Inspired by [SoftInstigate/graalvm-maven-docker](https://github.com/SoftInstigate/graalvm-maven-docker)
