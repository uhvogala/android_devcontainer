FROM mcr.microsoft.com/devcontainers/javascript-node:0-14

RUN apt update && apt install -y unzip openjdk-11-jdk && rm -rf /var/lib/apt/lists/*

WORKDIR /android_sdk/Android
RUN PACKAGE="commandlinetools-linux-9123335_latest.zip" \
    && wget -q https://dl.google.com/android/repository/${PACKAGE} \
    && unzip ${PACKAGE} -d cmdline-tools-tmp \
    && mv cmdline-tools-tmp/cmdline-tools/* ./cmdline-tools/latest/ \
    && rm -r cmdline-tools-tmp

ENV ANDROID_SDK=/android_sdk
ENV ANDROID_HOME=${ANDROID_SDK}/Android
ENV PATH="${PATH}:${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/platform-tools"

RUN yes | sdkmanager --licenses \
    && yes | sdkmanager "platform-tools" "platforms;android-29" "build-tools;29.0.2"
