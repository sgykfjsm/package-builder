FROM circleci/ubuntu-server
ARG package
ARG version
ARG install_dir
ENV deb circleci-${package}-${version}_0.0.1_amd64.deb
ADD $deb $deb
RUN apt-get update
RUN apt-get install -y build-essential
RUN sudo dpkg -i $deb
RUN ${install_dir}/bin/perl --version
RUN ${install_dir}/bin/cpanm --version
RUN ${install_dir}/bin/carton version
RUN ${install_dir}/bin/start_server --version
