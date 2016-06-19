#### Build Package

```bash
# Go root
$ cd ..
# Run
$ ./build-package perl 5.24.0 0.0.1 '/opt/circleci/perl/5.24.0'
```

When `build-package` finished, you can find the deb file at `perl` directory.

#### Test Package

```bash
# Go perl directory from root directory
$ cd ./perl
# Copy test deb file
$ cp ./circleci-perl-5.24.0_0.0.1_amd64.deb ./test
# Go to test directory
$ cd ./test
# Run
$ docker build --build-arg package=perl --build-arg version=5.24.0 --build-arg install_dir='/opt/circleci/perl/5.24.0' -t sgykfjsm/package_builder-perl-test:5.24.0 .
```
