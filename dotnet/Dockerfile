ARG DOTNET_VERSION=10.0

FROM mcr.microsoft.com/dotnet/sdk:${DOTNET_VERSION}-alpine

ARG DOTNET_TOOL_PATH=/opt/dotnet
ARG DOCFX_VERSION=2.78.5
ARG TRX2JUNIT_VERSION=2.1.0
ARG DOTNET_SONARSCANNER_VERSION=11.1.0
ARG DOTNET_COVERAGE_VERSION=18.4.1

RUN apk update && apk add git musl libxml2 libintl && rm -rf /var/cache/apk/*

RUN    dotnet tool update docfx               --version ${DOCFX_VERSION}               --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    && dotnet tool update trx2junit           --version ${TRX2JUNIT_VERSION}           --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    && dotnet tool update dotnet-sonarscanner --version ${DOTNET_SONARSCANNER_VERSION} --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    && dotnet tool update dotnet-coverage     --version ${DOTNET_COVERAGE_VERSION}     --tool-path ${DOTNET_TOOL_PATH} --verbosity normal \
    ;

ENV PATH=$PATH:${DOTNET_TOOL_PATH}

CMD ["sh"]
