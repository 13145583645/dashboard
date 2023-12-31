# Copyright 2017 The Kubernetes Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM ubuntu:20.04 as builder

# Create a nonroot user for final image
RUN useradd -u 10001 nonroot

# Scratch can be used as the base image because the backend is compiled to include all
# its dependencies.
FROM scratch as final
ARG TARGETARCH
ARG TARGETOS

# Add all files from current working directory to the root of the image, i.e., copy dist directory
# layout to the root directory.
ADD .dist/metrics-scraper/$TARGETOS/$TARGETARCH /

# Copy nonroot user
COPY --from=builder /etc/passwd /etc/passwd
USER nonroot

# Declare the port on which the webserver will be exposed.
EXPOSE 8080

# Run the compiled binary.
ENTRYPOINT ["/metrics-scraper"]
