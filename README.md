# RingCentral RingCX API Docs

[![Specs Status][specs-status-svg]][specs-status-url]
[![Docs Status][docs-status-svg]][docs-status-url]
[![Docs Status][docs-svg]][docs-url]

This repository is the home of the RingCentral RingCX Developer Guide: a collection of materials, and documentation to help educate developers on how to build on top of the RingCentral RingCX platform.

Visit at: https://engage-voice-api-docs.rtfd.org

## Contributing

If you would like to contribute to the RingCentral documentation effort, fork this repository, make your desired edits and contributions, and issue a pull request accordingly.

### Running ReadTheDocs Locally

```
% git clone https://github.com/ringcentral/engage-voice-api-docs.git
% cd engage-voice-api-docs
% pip install mkdocs
% pip install mkdocs-ringcentral
% pip install markdown-include
% mkdocs serve
```

Then you should be able to load http://localhost:8000 to view the documentation.

### Testing OpenAPI Specs

This repo holds OpenAPI specs for RingCX. For each commit, tests are run on Travis CI to verify that the OpenAPI 3.0 specs validate.

* RingCX Spec: [specs/voice/engage-voice_openapi3.json](specs/voice/engage-voice_openapi3.json)
* Tests: [specs_test.go](specs_test.go)

You can verify the specs locally with the following if you have [Go installed](https://golang.org/).

```
% git clone https://github.com/ringcentral/engage-voice-api-docs.git
% cd engage-voice-api-docs
% go test -v ./...
```

If you wish to change the specs being tested edit the [specs_test.go](specs_test.go) file.

 [specs-status-svg]: https://github.com/ringcentral/engage-voice-api-docs/workflows/build/badge.svg?branch=master
 [specs-status-url]: https://github.com/ringcentral/engage-voice-api-docs/actions
 [docs-status-svg]: https://readthedocs.org/projects/engage-voice-api-docs/badge/?version=latest
 [docs-status-url]: https://readthedocs.org/projects/engage-voice-api-docs/builds/
 [docs-svg]: https://img.shields.io/badge/docs-preview-blue.svg
 [docs-url]: https://engage-voice-api-docs.readthedocs.io/
