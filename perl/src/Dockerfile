FROM ubuntu:14.04
ARG version
ARG package
ARG release
ARG install_dir
RUN mkdir -pv ${install_dir}

RUN apt-get update && apt-get install -y ruby-dev build-essential git curl

RUN gem install fpm --no-rdoc --no-ri

RUN git clone https://github.com/tagomoris/xbuild.git

RUN xbuild/perl-install ${version} ${install_dir}

RUN fpm -s dir -t deb -C ${install_dir} \
      --name circleci-${package}-${version} \
      --version ${release} \
      --prefix ${install_dir} \
      --force \
      --description "Perl ${version} built by shigeyuki.fujishima" \
      --no-depends \
      .
