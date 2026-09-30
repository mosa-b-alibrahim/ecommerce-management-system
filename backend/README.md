# Backend

Requires JDK 21. Run commands below from `backend/` using the included Maven wrapper.

## Configuration basics

Spring Boot configuration supplies settings separately from Java code so the same
application can run in different environments. Spring automatically reads
`src/main/resources/application.properties`. It contains shared settings, currently
only the application name. `application.yml` is a YAML alternative; this project
uses `.properties` consistently and does not need both formats.

A Spring profile is a named set of settings. Activating `dev` also loads
`application-dev.properties`, whose values override matching base settings.
Future environments can follow the same `application-{profile}.properties` naming.
The development profile is selected at runtime, never activated in the shared file.

Environment variables are values supplied to a process by its shell, IDE, or hosting
platform. `SPRING_PROFILES_ACTIVE` selects the profile. In the development file,
`${SERVER_PORT:8080}` uses `SERVER_PORT` when supplied and falls back to `8080`.
Spring also supports environment overrides directly, such as `SERVER_PORT` for
`server.port`. No database configuration or credentials are needed at this stage.

## Run in development

PowerShell:

```powershell
$env:SPRING_PROFILES_ACTIVE = 'dev'
./mvnw.cmd spring-boot:run
```

macOS/Linux:

```sh
SPRING_PROFILES_ACTIVE=dev ./mvnw spring-boot:run
```

The logs should report the active `dev` profile and Tomcat listening on port `8080`.
Stop with Ctrl+C. To use another port, set `$env:SERVER_PORT = '8081'` in PowerShell
before starting, or run
`SPRING_PROFILES_ACTIVE=dev SERVER_PORT=8081 ./mvnw spring-boot:run` on macOS/Linux.
In an IDE, set these environment variables in the application's run configuration.
PowerShell variables last for the shell session; remove them afterward with
`Remove-Item Env:SPRING_PROFILES_ACTIVE, Env:SERVER_PORT -ErrorAction SilentlyContinue`.

## Secrets

Commit only non-sensitive defaults. Passwords, tokens, and keys in Git can be copied
and remain in history even after deletion. When secrets become necessary, supply
them at runtime using environment variables or the hosting platform's secret store.
Do not add real secrets to configuration files, examples, or logs. If one is
committed accidentally, revoke or rotate it; deleting the file is insufficient.

Local `.env` and `.env.*` files are ignored, except `.env.example`, which must contain
only safe examples. Spring Boot does not automatically load `.env` files: export
values in your shell or configure your IDE to supply them. Git ignore rules do not
protect files that are already tracked; inspect staged changes before committing.

## Verification and review

Run `./mvnw.cmd test` (Windows) or `./mvnw test` (macOS/Linux) for the existing context
test. With `SPRING_PROFILES_ACTIVE=dev` set as above, this also checks that the
development configuration loads. Start the application using the development
commands and confirm the active profile and listening port in its logs. Repeat
with `SERVER_PORT=8081` to check the environment override. No endpoint is required
yet, so an HTTP 404 at `/` is expected.

Before merging, another team member should review the configuration and verify
startup, confirm no credentials or database settings were added, and resolve review
comments in the issue-linked pull request.

See the [Spring Boot configuration reference](https://docs.spring.io/spring-boot/reference/features/external-config.html).
