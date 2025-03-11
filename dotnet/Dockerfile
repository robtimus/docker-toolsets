ARG DOTNET_VERSION=8.0

FROM mcr.microsoft.com/dotnet/sdk:${DOTNET_VERSION}-alpine

ARG DOTNET_TOOL_PATH=/opt/dotnet
ARG DOCFX_VERSION=2.78.3
ARG TRX2JUNIT_VERSION=2.1.0
ARG DOTNET_SONARSCANNER_VERSION=9.2.1
ARG DOTCOVER_VERSION=2023.2.5

RUN apk update && apk add git && rm -rf /var/cache/apk/*

RUN    dotnet tool update docfx                         --version ${DOCFX_VERSION}               --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    && dotnet tool update trx2junit                     --version ${TRX2JUNIT_VERSION}           --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    && dotnet tool update dotnet-sonarscanner           --version ${DOTNET_SONARSCANNER_VERSION} --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    && dotnet tool update JetBrains.dotCover.GlobalTool --version ${DOTCOVER_VERSION}            --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    ;

ENV PATH=$PATH:${DOTNET_TOOL_PATH}

CMD sh
