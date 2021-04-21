FROM debian:buster-slim
LABEL maintainer="Joel Luth (joel.luth@gmail.com)"
LABEL description="Base image for Google Coral projects"

RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
		ca-certificates \
		curl \
		git \
		gnupg \
		libjpeg-dev \
		python3 \
		python3-pip \
		zlib1g-dev \
	&& apt-get clean \
	&& apt-get autoremove -y \
	&& rm -rf /var/lib/apt/lists/*

# Install Coral Edge code
RUN echo "deb https://packages.cloud.google.com/apt coral-edgetpu-stable main" | tee /etc/apt/sources.list.d/coral-edgetpu.list
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN apt-get update \
        && apt-get install -y --no-install-recommends \
		libedgetpu1-std \
		python3-edgetpu \
        && apt-get clean \
        && apt-get autoremove -y \
        && rm -rf /var/lib/apt/lists/*

RUN pip3 install https://github.com/google-coral/pycoral/releases/download/release-frogfish/tflite_runtime-2.5.0-cp37-cp37m-linux_armv7l.whl
#RUN pip3 install pillow
#RUN apt-get install libedgetpu1-std -y
