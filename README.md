<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/stevezaluk/mtgjson-proto">
    <img src="docs/images/logo-mtgjson.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">MTGJSON-Protobufs</h3>

  <p align="center">
    Protocol buffer models for the MTGJSON data set
    <br />
    <a href="https://github.com/stevezaluk/mtgjson-proto"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://stevezaluk.atlassian.net/jira/software/projects/SCRUM/boards/1/backlog">Jira Board</a>
    ·
    <a href="https://stevezaluk.atlassian.net/jira/software/projects/SCRUM/boards/1/backlog">Report Bug</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li><a href="#disclaimers">Disclaimers</a></li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#configuration">Configuration</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

MTGJSON-Protobufs are a set of protocol buffers modeling the original MTGJSON data set. These were originally developed for use within the MTGJSON API, however they can be used and integrated with any language. The models have been altered slightly to ensure that user ownership of objects (like decks) within the API can be implemented, please see model description below. 

## Disclaimers

MTGJSON Protobufs is unofficial Fan Content permitted under the Fan Content Policy. Not approved/endorsed by Wizards of the Coast. Portions of the materials used are property of Wizards of the Coast. © Wizards of the Coast LLC.

MTGJSON Protobufs is not officially endorsed by MTGJSON

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

To be able to generate models for your selected language, you will need the protobuf compiler installed. You can follow the instructions below for installing this

* Debian Based Linux Distribution: `apt-get update && apt install -y protobuf-compiler`
* MacOS: `brew update && brew install protobuf`

If you need additional tags to be injected into the generated models (specifically for use within Go) then protoc-go-inject-tag should be installed as well

* Install protoc-go-inject-tag: `go install github.com/favadi/protoc-go-inject-tag@latest`

### Installation

Generating protobuf models is incredibly simple and can be completed with a single command. The below example shows how to generate them for Go lang, however they can be generated for any other language that protoc support simply by changing the `--go_out` flag
to which ever flag best suits your language:

* Generate Protobuf's: `protoc -I=mtgjson-proto/ --go_out=<OUTPUT_DIRECTORY> --go_opt=paths=source_relative mtgjson-proto/*/*.proto`

#### Go-lang Generation Notes

Please be aware that if you are generating these for a go-lang project that is seperate from the MTGJSON-API, then you will need to change the `go_package` option statement that is defined at the top of each protobuf model. Currently, this is set to: `github.com/stevezaluk/mtgjson-models/<package>` to ensure that
the models will be properly generated for the MTGJSON-API

Additionally, please make note that the `paths=source_relative` option is currently set to ensure that protoc does not recreate the directory structure according to the `go_package` option. Remove this if you would like this functionality

#### Additional Go-lang Struct Tags
If you are generating these for go, and you need additional struct tags injected into the models then you should run the following command post-generation to inject the tags. You can define the additional tags that you want to inject using the following comment structure: `// @gotags: key=val`.
Comments injecting additional BSON tags have been provided already:

* Inject Tags: `cd mtgjson-models && protoc-go-inject-tag -input="*/*.pb.go"`

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->
## License

Distributed under Apache License 2.0. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Steven A. Zaluk - [@steve_zaluk](https://x.com/stevezaluk) - arcanegame@protonmail.com

Project Link: [https://github.com/stevezaluk/mtgjson-proto](https://github.com/stevezaluk/mtgjson-proto)\n

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/stevezaluk/mtgjson-proto.svg?style=for-the-badge
[contributors-url]: https://github.com/stevezaluk/mtgjson-proto/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/stevezaluk/mtgjson-proto.svg?style=for-the-badge
[forks-url]: https://github.com/stevezaluk/mtgjson-proto/network/members
[stars-shield]: https://img.shields.io/github/stars/stevezaluk/mtgjson-proto.svg?style=for-the-badge
[stars-url]: https://github.com/stevezaluk/mtgjson-proto/stargazers
[issues-shield]: https://img.shields.io/github/issues/stevezaluk/mtgjson-proto.svg?style=for-the-badge
[issues-url]: https://github.com/stevezaluk/mtgjson-proto/issues
[license-shield]: https://img.shields.io/github/license/stevezaluk/mtgjson-proto.svg?style=for-the-badge
[license-url]: https://github.com/stevezaluk/mtgjson-proto/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/stevezaluk/
[go-sdk-version]: https://img.shields.io/github/go-mod/go-version/stevezaluk/mtgjson-sdk
