# Ramekin simple example

A static web page served by nginx, packaged with [Ramekin](https://github.com/ascension-association/ramekin) for a gokrazy device. This is the project from the Web Page Example in Ramekin's README.

- `example.def` is the Apptainer definition file: Chainguard's nginx image, the page, and port 80.
- `index.html` is the page.
- `ramekin.yaml` is the Ramekin project. It publishes to this repository's [releases](https://github.com/ascension-association/ramekin-simple-example/releases); `hello-web/stable.json` on this branch is the signed channel pointer devices poll.

Try it:

```sh
git clone https://github.com/ascension-association/ramekin-simple-example && cd ramekin-simple-example
ramekin keys generate
ramekin build
ramekin device init hello --no-updates --health-http http://127.0.0.1/
gok -i hello overwrite --full /dev/sdX
ramekin push hello
curl http://hello/
```

To publish your own releases, point `releases.github` in `ramekin.yaml` at a repository of yours.
