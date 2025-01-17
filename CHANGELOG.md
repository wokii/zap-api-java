# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
### Added
- Add API for SOAP Scanner add-on, version 3.

### Changed
- Core APIs updated for ZAP version 2.8.0.
- Update Replacer API, per release of version 7.
- Add description to Importurls API endpoint.

### Fixed
- Disable XXE processing when parsing ZAP API responses.
- Ensure alerts file is always closed.

## [1.6.0] - 2018-04-10
### Added
- WebSockets ("websocket").

### Fixed
- Explicitly disable HTTP caching, to always obtain a fresh response from ZAP.

## [1.5.0] - 2017-11-30
### Changed
- Core APIs updated for ZAP version 2.7.0.

## [1.4.0] - 2017-07-13
### Added
- New Ant task to create ZAP reports:
  ```XML
  <!-- Defined the task: -->
  <taskdef name="reportTask" classname="org.zaproxy.clientapi.ant.ReportTask" />
  <!-- Call the task: -->
  <reportTask zapAddress="localhost" zapPort="8080" apikey="API-KEY"
      type="html" file="report.html" overwrite="true" />
      <!--
          type - the type/format of the report (e.g. HTML, XML, MD), defaults to HTML.
          file - where the report should be created (can be an absolute path, if relative it is resolved against the build directory).
          overwrite - if the file should be overwritten.
      -->
  ```

## [1.3.0] - 2017-06-23
### Added
- Import files containing URLs ("importurls").
- OpenAPI Support ("openapi").
- Replacer ("replacer").

### Changed
- Update scan Ant tasks to wait for the corresponding scan to finish.

## [1.2.0] - 2017-03-29
### Changed
- Core APIs updated for ZAP version 2.6.0.
- Update AJAX Spider API
  - Allows to obtain the full results of a scan, messages in/out of scope
  and message with I/O errors.

## [1.1.1] - 2017-03-09
### Fixed
- Fixed a bug that prevented the new API methods (that don't require
the API key) from being used with ZAP versions <= 2.5.0.

## [1.1.0] - 2017-03-09
### Added
- Context Alert Filters API, for more information refer to the help page:
https://github.com/zaproxy/zap-extensions/wiki/HelpAddonsAlertFiltersAlertFilter
- The `Alert` now exposes the alert ID, message ID, and scanner ID.
- Added confidence "False Positive" (enum `Alert.Confidence`).

### Changed
- The `ClientApi` now allows to set the API key through the constructor,
which ensures that the API key is sent whenever required. 
- It's now possible to obtain the keys of the values of an `ApiResponseSet`
(also, deprecated unused/unnecessary constructor and method).
- It's now possible to specify the API key in all Ant tasks.
- Update AJAX Spider API
  - Allows to scan a context, as a user and just a subtree.
- Update Selenium API
  - Allows to choose which Firefox binary is used and set the path to geckodriver.

### Deprecated
 - The API methods that allowed to pass the API key were deprecated in
favour of using the new `ClientApi` constructor.
- `Alert` and `AlertTask` now use `name` instead of `alert` for the name
of the alert (zaproxy/zaproxy#1341), older methods were deprecated.

### Fixed
- `ApiResponseSet` now has as values `ApiResponse` (zaproxy/zaproxy#3228).

## [1.0.0] - 2016-06-03
### Added
 - First version as "stand alone library", it was migrated from the [zaproxy repository](https://github.com/zaproxy/zaproxy)
 and released to Maven Central.

[Unreleased]: https://github.com/zaproxy/zap-api-java/compare/v1.6.0...HEAD
[1.6.0]: https://github.com/zaproxy/zap-api-java/compare/v1.5.0...v1.6.0
[1.5.0]: https://github.com/zaproxy/zap-api-java/compare/v1.4.0...v1.5.0
[1.4.0]: https://github.com/zaproxy/zap-api-java/compare/v1.3.0...v1.4.0
[1.3.0]: https://github.com/zaproxy/zap-api-java/compare/v1.2.0...v1.3.0
[1.2.0]: https://github.com/zaproxy/zap-api-java/compare/v1.1.1...v1.2.0
[1.1.1]: https://github.com/zaproxy/zap-api-java/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/zaproxy/zap-api-java/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/zaproxy/zap-api-java/compare/6c778f77a817e1ff71e9279e4759535d482e8393...v1.0.0