[![Build status](https://img.shields.io/travis/Chicago/open311-api-docs/master.svg?style=flat-square&maxAge=2592000)](https://travis-ci.org/Chicago/open311-api-docs)[![Version](https://img.shields.io/github/release/Chicago/open311-api-docs.svg?maxAge=2592000&style=flat-square)](https://github.com/Chicago/open311-api-docs/releases)

# Open311 API Documentation

This repo provides the source material for City of Chicago's Open311 application programmer interface (API). The documentation in the `master` branch is compiled and deployed to the city's [developer's site](http://dev.cityofchicago.org). 

This repository should only be used to edit the source documents for the Open311 documentation. Other changes to dev.cityofchicago.org should be made to that project's [repo](https://github.com/Chicago/dev.cityofchicago.org).


## Building and Testing

The documentation is compiled with [MkDocs](http://www.mkdocs.org/) and is required while testing.

### Local Testing

Test changes to the documentation by opening a terminal and run

```
mkdocs serve
```

Visit `localhost:8000` in a browser to inspect the documentation.

Once changes are acceptable, build the documentation by returning to the terminal and run

```
mkdocs build
```

Commit and push changes to the server.

### Deployment to dev.cityofchicago.org

Currently, the website must be manually deployed to the Amazon S3 instance hosting dev.cityofchicago.org. Copy the contents of the `site/` directory from the `open311-api-docs` repo to `s://cityofchicago.org/docs/open311/`. Using the [AWS CLI](https://aws.amazon.com/cli/), this can be done by the following:

```bash
cd /path/to/open311-api-docs/site
aws s3 cp . s3://dev.cityofchicago.org/docs/open311 --recursive
```

Please note: the `site/` directory is not tracked by git and not commited to the repo. While it is feasible to automatically deploy the documentation to the final website, there is an issue preventing it. See [#2](https://github.com/Chicago/open311-api-docs/issues/2) for a description of that issue.

## License

Copyright &copy; 2016-2017 City of Chicago. Documentation is licensed under [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/).