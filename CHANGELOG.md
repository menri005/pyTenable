# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.3.26]
### Fixed
- Failed to add necessary requirement for the "ipaddress" python package.

## [0.3.25]
### Added
- Added the Tenable.io ScansAPI.history endpoint #141
- Added the ability for Tenable.io's PolicyAPI.list() iterator to graft on plugin family details.

### Fixed
- Spelling type in Tenable.sc ScansAPI.launch when generating diagnostic passwords #142
- Incorrect policy UUID passed to scans created in Tenable.io w/ an existing policy. #143


## [0.3.24]
### Changed
- Switched the Nessusv2 file parser to diffusedxml per recommendation with bandit

### Fixed
- TenableSC SSL verification flags were not set in the session builder, which meant that login was a one-time event. #139


## [0.3.23]
### Changed
- Improved documentation for creating scans to include credentials

### Added
- Tenable.io Access Group API Added and Tested #98
- Tenable.io Networks API Added and Tested #129
- Tenable.io Managed Credentials API Added and Tested #130

### Fixed
- tio.policies.template_details wasn't correctly constructing the document from the editor API #136
- tio.agent_groups.list was missing from the documentation


## [0.3.22]
### Added
- Tenable.sc Asset List API Added and Tested #13

### Changed
- Export wait logic is now centralized.  Both scan export and workbench export now use this new method.

### Fixed
- Multiple chapters should be merged with ; and not , in Workbenches exports
- Chapter "vuln_by_asset" was missing from the choices for workbench export #127
- Docstrings incorrectly state that chapters are only necessary for PDF and HTML #127
- Scan types weren't being set when passing the subordinate attribute #128


## [0.3.21]
### Changed
- Tenable.io scans.export now supports explicitly defining the filters attribute as well as the implicit argument list #124

### Fixed
- Doc examples for TenableSC credentials.create were incorrect. #122
- SC API Reference incorrectly stated authType of "publickey" instead of "publicKey". #122
- SC Analysis Query Expander wasn't expanding numerid ids https://community.tenable.com/s/question/0D7f2000005b5OX/filter-on-asset-via-api-call-to-analysis-resource-using-pytenable
- SC Credential privilegeEscalation attr pre-fill wasn't restricted to just specific types #126
- SC Users docs weren't linked into the documentation.


## [0.3.20]
### Added
- Added support for the new plugins list endpoint.
- Support for extensible retry logic using the retry_on param.
- Tested out CSv2 API endpoints #8 #9

### Changed
- Homogenized the docstrings for TenableSC #115
- Updated docs in tio.scans.create to denote that the name is required. #118

### Fixed
- Streaming responses in TenableSC weren't working as expected #114
- Files weren't uploading properly in TenableSC Credentials endpoints #122
- User permissions parameter type #121
- Typo in docs #120
- Scanner listing when WAS wasn't enabled caused an error #117


## [0.3.19]
### Changed
- All Tenable.io API doc links have been re-pointed to the new developer portal. #111
- tio.editor.edit has been renamed to tio.editor.template_details as it was misnamed.
- tio.editor.list has been renamed to tio.editor.template_list to more accurately describe it's function.

### Added
- Added the asset delete method to the workbenches TenableIO module #110
- Added and tested out the TenableSC plugin family additions to the plugins module #78
- Added and tested out the TenableSC OrganizationAPI module #77
- Added and tested out the TenableSC QueryAPI module #79

### Fixed
- Various documentation issues reported by sphinx addressed
- TenableSC.scan_instances.list can now support non-standard timeframes #108


## [0.3.18]
### Added
- Added and tested out support for TenableSC Credentials #76

## [0.3.17]
### Added
- Analysis filters now allow for collapsing lists if id dicts into lists of
  integer ids.  e.g. `('name', '=', [{'id': 1}])` is now `('name', '=', [1])`
- Added and tested out support for TenableSC AuditFileAPI #75

### Changed
- Tenable.io Exports iterator now has **uuid**, **chunk_id**, **chunks**, and
  **processed** publicly exposed.

### Fixed
- Addressed issue where UnexpectedValueError was sometimes raised when
  specifying a scanner by name in tio.scans._create_scan_document.


## [0.3.16]
### Added
- Added and tested out support for TenableSC UserAPI #24
- Added and tested out support for TenableSC GroupAPI #24
- Added and tested TenableIO.agent_groups.list() #105

### Fixed
- Tenable.sc Schedule document validation extended to support `now` for
  scans #102


## [0.3.15]
### Added
- Added and tested out support for TenableSC RoleAPI #24

### Fixed
- Retries would throw an error as they weren't floats.
- Exports would erroneously set an option if set to none.
- The scan history test cassette was modified to match the new call.


## [0.3.14]
### Fixed
- Corrected Doc Issue where the downloads API was incorrectly referencing
  sc.alerts
- Fixed issue with scan history deletion where the path was incorrect #101


## [0.3.13]
### Added
- Tested out TenableSC StatusAPI #22
- Tested out TenableSC SystemAPI #22
- Tested out TenableSC ScanZoneAPI #21
- Tested out TenableSC ScannerAPI #21
- Tested out Downloads API

### Fixed
- RetryError no longer itself throws an error due to logging.
- Fixed type mismatch bug in IO workbench filters #97
- Corrected issue with ScanZone updates using the wrong HTTP method #95
- Corrected doc issue with ScanResultAPI.export not referring to the fact that
  the exported scan is zipped.
- Corrected the raw HTTP method docs


## [0.3.12]
### Added
- Added view parameter for TenableSC.analysis.scan #73
- Added accept_risks module #18 (untested)
- Added system module and converted the TenableSC module to use it over a raw
  call #22
- Added status module #22 (untested)

### Fixed
- Fixed issue with TenableSC.analysis.scan not properly passing a view. #73


## [0.3.11]
### Added
- Added proxy support for the IO, SC, etc. #72

### Fixed
- Fixed issue where supplied sessions weren't being properly passed to
  _build_session.


## [0.3.10]
### Added
- Added example for Workbench CSV Downloads for IO
- Added support for multi-value filters in IO.
- Added Request-UUID logging for all responses when available.
- Added TenableSC scan_instances endpoints and associated tests #19.
- Added TenableSC scan policies endpoints and associated tests #20.
- TenableIO can now pull API keys directly from environment variables as well.
- Added doc page detailing how to run the tests.
- Added TenableSC repositories endpoint and associated tests #17

### Fixed
- Exports methods in TenableIO now respect 0 integers being passed #69.
- Errored scan exports in TenableIO will no longer wait forever.
- Scan Exports using multiple chapters now works as expected #71 #70

### Removed
- schedule_* parameters in scans have been removed in favor of direct checking
    and documentation of the schedule dictionary.  This has larger implications
    down the line with repositories, alerts, etc.


## [0.3.9]
### Added
- Added the `aggregate` parameter for scan import.
- Added Changelog and backfilled changes from 0.1.0 to current
- Added testing for user outputs #26
- Added testing for scanner outputs #30
- Added testing for permissions #34
- Added testing for groups #35
- Adjusted the doc format to no longer pin the sidebar #61
- Added redaction to sensitive pathways #66
- Added tagging support #44

### Changed
- Tenable.sc files module was incorrectly pointing to self.post instead of
  self._api.post
- Launching a scan with alt_targets sends an array instead of a string #64
- Tenable.sc Analysis will now handle Query IDs #63
- Agent-Delete within Tenable.io Was using the wrong Endpoint #59
- Refactored TIOIterator to use less code when subclassing.
- Documented iterators and other common models.


## [0.3.8]
### Added
- Added TioExportsError to handle status error
- Tagging support for asset export


## [0.3.7]
### Added
- Added scans.status in Tenable.sc
- Added scans module for Tenable.sc
- Added logging support for the whole of pyTenable

### Changed
- Corrected pathway to acceptRiskRule for Tenable.sc package
- Scans.update renamed to Scans.edit in Tenable.io

### Removed
- analysis_type from being sent to the API


## [0.3.6]
### Added
- Tenable.sc login testing
- Tenable.sc Analysis testing #10

### Changed
- Fixed iterator looping issue
- Travis now runs all tests
- Converted pytest to use conftest standard
- Improved VCRpy testing

### Removed
- Container Security v1 tests (not VCRed)


## [0.3.5]
### Changed
- Fixed iterator first page problem
- Adjusted Tenable.sc model constructors to all behave the same uniform way


## [0.3.4]
### Added
- Added tagging support for vulnerability export
- Added VCRpy to all unit tests
- Added accept_risks Model to TenableSC

### Changed
- Moved get_status checking for iterators to conform to DRY
- lxml is now an optional dependency


## [0.3.3]
### Added
- Added scan_instances to TenableSC

### Changed
- tio.scanners.linking_key is now a method instead fo a property

### Removed
- Removed a lot of stubbed models that haven't been worked on yet


## [0.3.2]
### Changed
- Documentation refactored
- Mocked up some of the libraries for improved testing
- Fixed typo bug in sc.scans


## [0.3.1]
### Added
- Documented asset_activity to TenableIO

### Changed
- Re-pointed all SecurityCenter references to TenableSC instead
- Refactored schedule sub-document creation into a separate constructor for
  re-use
- Documentation improvements


## [0.3.0]
### Added
- Added unit tests for Inputs & Outputs for IO Scanner Groups
- Added unit tests for Inputs & Outputs for IO Policies
- Added unit tests for Inputs & Outputs for IO Plugins
- Added unit tests for Inputs & Outputs for IO Folders
- Added unit tests for Inputs & Outputs for IO Filters
- Added unit tests for Inputs & Outputs for IO Asset Lists
- Added unit tests for Inputs & Outputs for IO Target Groups
- Added unit tests for Inputs & Outputs for IO Sessions
- Added RetryError

### Changed
- Inlined all of the Documentation into the code itself
- Documentation refactoring effort for the whole package
- Unit test improvements


## [0.2.2]
### Changed
- Refactored long-description to better suit PyPI inclusion

## [0.2.1]
### Changed
- Inlined the Readme


## [0.2.0]
### Added
- Added TenableSC Analysis Model
- Added TenableSC Feeds Model
- Added TenableSC Files Model
- Added NessusReportv2 Model

### Changed
- Refactored the sub-package pathing
- Modified importing to be relative


## [0.1.0]
### Added
- Added TenableIO Exports Model
- Added TenableIO Scans Model
- Added

### Changed
- Fixed Time Conversion Issue #6

[Unreleased]: https://github.com/tenable/pyTenable/compare/0.3.26...master
[0.3.25]: https://github.com/tenable/pyTenable/compare/0.3.25...0.3.26
[0.3.25]: https://github.com/tenable/pyTenable/compare/0.3.24...0.3.25
[0.3.24]: https://github.com/tenable/pyTenable/compare/0.3.23...0.3.24
[0.3.23]: https://github.com/tenable/pyTenable/compare/0.3.22...0.3.23
[0.3.22]: https://github.com/tenable/pyTenable/compare/0.3.21...0.3.22
[0.3.21]: https://github.com/tenable/pyTenable/compare/0.3.20...0.3.21
[0.3.20]: https://github.com/tenable/pyTenable/compare/0.3.19...0.3.20
[0.3.19]: https://github.com/tenable/pyTenable/compare/0.3.18...0.3.19
[0.3.18]: https://github.com/tenable/pyTenable/compare/0.3.17...0.3.18
[0.3.17]: https://github.com/tenable/pyTenable/compare/0.3.16...0.3.17
[0.3.16]: https://github.com/tenable/pyTenable/compare/0.3.15...0.3.16
[0.3.15]: https://github.com/tenable/pyTenable/compare/0.3.14...0.3.15
[0.3.14]: https://github.com/tenable/pyTenable/compare/0.3.13...0.3.14
[0.3.13]: https://github.com/tenable/pyTenable/compare/0.3.12...0.3.13
[0.3.12]: https://github.com/tenable/pyTenable/compare/0.3.11...0.3.12
[0.3.11]: https://github.com/tenable/pyTenable/compare/0.3.10...0.3.11
[0.3.10]: https://github.com/tenable/pyTenable/compare/0.3.9...0.3.10
[0.3.9]: https://github.com/tenable/pyTenable/compare/0.3.8...0.3.9
[0.3.8]: https://github.com/tenable/pyTenable/compare/0.3.7...0.3.8
[0.3.7]: https://github.com/tenable/pyTenable/compare/0.3.6...0.3.7
[0.3.6]: https://github.com/tenable/pyTenable/compare/0.3.5...0.3.6
[0.3.5]: https://github.com/tenable/pyTenable/compare/0.3.4...0.3.5
[0.3.4]: https://github.com/tenable/pyTenable/compare/0.3.3...0.3.4
[0.3.3]: https://github.com/tenable/pyTenable/compare/0.3.2...0.3.3
[0.3.2]: https://github.com/tenable/pyTenable/compare/0.3.1...0.3.2
[0.3.1]: https://github.com/tenable/pyTenable/compare/0.3.0...0.3.1
[0.3.0]: https://github.com/tenable/pyTenable/compare/0.2.2...0.3.0
[0.2.2]: https://github.com/tenable/pyTenable/compare/0.2.1...0.2.2
[0.2.1]: https://github.com/tenable/pyTenable/compare/0.2.0...0.2.1
[0.2.0]: https://github.com/tenable/pyTenable/compare/0.1.0...0.2.0
[0.1.0]: https://github.com/tenable/pyTenable/compare/4ab62c61c80768a36b65ba5accef0bfe1350480e...0.1.0