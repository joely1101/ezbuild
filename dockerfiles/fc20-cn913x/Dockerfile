FROM joely1101/fedora20
ADD https://snapshots.linaro.org/components/toolchain/binaries/7.4-2019.02-rc1/aarch64-linux-gnu_ilp32/gcc-linaro-7.4.1-2019.02-rc1-i686_aarch64-linux-gnu_ilp32.tar.xz /opt/
RUN tar xvf /opt/gcc-linaro-7.4.1-2019.02-rc1-i686_aarch64-linux-gnu_ilp32.tar.xz -C /opt/
ENV PATH="/opt/gcc-linaro-7.4.1-2019.02-rc1-i686_aarch64-linux-gnu_ilp32/bin:${PATH}"

