<h1> Bio Server </h1>

![Go](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white)
![MongoDb](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)

[Università La Sapienza Roma](https://www.uniroma1.it/en), [Dipartimento di Informatica](https://www.studiareinformatica.uniroma1.it/)

![Sapienza Università di Roma](/logos/sapienza-big.png)

### Credits

[`federico-rosatelli`](https://github.com/federico-rosatelli) [`Mat`](https://github.com/AxnNxs) [`Loriv3`](https://github.com/Loriv3) [`Samsey`](https://github.com/Samseys) [`Calli`](https://github.com/BboyCaligola)

# MicroAlgae DB
- This repository is part of MicroAlgae DB project, formed by various modules. Visit the homepage at link https://github.com/BITSapienza for a general guide and automatic installation through docker-compose.

# Description
- Bio-Server is a backend platform written in Golang and based on Fantastic Coffee platform. Is intended for research and consultation only and contains a custom structure for a Web and Software Application project. The difference between our project and the original platform is the differentiation of Front-end (accessible at https://github.com/BITSapienza/Vulgaris-Platform) and Back-end for modular approach of development.

# Requirements
- Despite being a module in its own right, the focus of this backend is to run aside Vulgaris Platform and MongoDB. Please visit homepage for further informations. A docker-file is provided to run a standalone backend in semi-automatic mode, avoiding compatibility and installation issues. If running docker is not desired, golang is needed to be installed in host operating system for running and debugging. [Go Vendoring](https://go.dev/ref/mod#vendoring) is used in this project .

## Project structure
* `cmd/` contains all executables; Go programs here do "executable-stuff", like reading options from the CLI/env, etc.
	* `cmd/webapi` contains an example of a web API server daemon
* `service/` has all packages for focal functionalities:
	* `service/api` contains queries and filter methods. The main requests are managed by `service/api/routerfunctions.go`, that take in all Endpoints and return the requested data by user, calling all other classes under api folder sotto for a first skimming (check on IDs, errors, missing data and various filters);
	* `service/database`  contains other queries and filter methods finalizers. After first skimming, they serve for search on MongoDB (with check on data and populated structure for table view) and return data requested by router function.
* `vendor/` is managed by Go, and contains a copy of all dependencies. It is not served by default because is created during build phase. With docker, this folder is managed in a container.
* webui is provided in Front-end.

# End-Points
* As displayed in `service/api/api-handler.go` they are:
	- "/"
	- "/taxonomy"
	- "/taxonomy_tree"
	- "/taxon_term"
	- "/organism/:id/nucleotides"
	- "/organism/:id/nucleotides/:locus"
	- "/organism/:id/proteins"
	- "/organism/:id/proteins/:locus"
	- "/analysis"

## How to build
To run backend open terminal and write:
	```shell
	go build ./cmd/webapi/
	```
Launch the backend only using (development mode):
	```shell
	go run ./cmd/webapi/
	```

## Node/NPM vendoring
This repository contains the `webui/node_modules` directory with all dependencies for Vue.JS. You should commit the content of that directory and both `package.json` and `package-lock.json`.
```shell
npm run ./cmd/webapi/
```
