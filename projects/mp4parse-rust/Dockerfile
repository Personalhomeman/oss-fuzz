# Copyright 2020 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################

FROM gcr.io/oss-fuzz-base/base-builder
MAINTAINER mgregan@mozilla.com
RUN apt-get update && apt-get install -y make autoconf automake libtool curl cmake python llvm-dev libclang-dev clang

ENV CARGO_HOME=/rust RUSTUP_HOME=/rust/rustup PATH=$PATH:/rust/bin
RUN curl https://sh.rustup.rs | sh -s -- -y --default-toolchain=nightly
RUN cargo install cargo-fuzz

RUN git clone --depth 1 https://github.com/mozilla/mp4parse-rust mp4parse-rust
WORKDIR mp4parse-rust

COPY build.sh $SRC/
