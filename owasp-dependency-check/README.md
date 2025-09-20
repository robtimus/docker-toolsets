# owasp-dependency-check

A Docker image containing the OWASP Dependency-Check tool including a database that should be no more than 24 hours old. This makes it usable in situations where updating the database isn't possible.

## Usage

```
docker run <docker options> robtimus/owasp-dependency-check <owasp-dependency-check options>
```

Note: it's suggested to add `--noupdate` to the OWASP Dependency-Check options, as it shouldn't be necessary to update the database.

## Include the database in other Docker images

Include the following in your Dockerfile to include the database:

```
COPY --from=robtimus/owasp-dependency-check /usr/share/dependency-check/data /usr/share/dependency-check/data
# The following may or may not be necessary
#RUN chmod go+w /usr/share/dependency-check/data
```

## Extracting the database

Run the following to extract the database:

```
docker run -v $TARGET_FOLDER:/data-extract --entrypoint= --pull always robtimus/owasp-dependency-check sh -c "cp -R /usr/share/dependency-check/data/* /data-extract/"
```
