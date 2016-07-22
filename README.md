# CareConnect-methodology

## Goal
To adapt the HL7 FHIR standard and create a library of profiles (resources and interaction patterns) that implementors can adopt to simplify integration and interoperability within UK Health and Social Care.

## Methodology
Profiling creates FHIR resources including: StructureDefinitions (profiles AND data dictionary items), ValueSets (standard lists), Conformance statements (client-server interaction patterns). Profiling also creates documentation (e.g. patterns of use) Assets are held by the HL7-UK organisation on github [https://github.com/HL7-UK]. Assets are licensed under Apache 2 license [http://www.apache.org/licenses/LICENSE-2.0]. Assets are managed by an editorial team representing stakeholders.

Each domain of interest has an individual public repository, to allow different domains to proceed at their own rate. It is anticipated that an additional data dictionary repository will hold shared/common resources. Where resources exist in a number of domains, editors will seek to harmonise across domains and bring into data dictionary.

Each repository uses the gitflow pattern [http://nvie.com/posts/a-successful-git-branching-model/]. Latest versions of assets are available on develop branch. Latest version of documentation is published as github pages.

## Contributors
Contributors are responsible for the customisation of resources to suit the requirements of the domain.

Contributors create a GitHub account and fork the develop branch of the repository, editing as they wish. When a contributor has a change to propose they make changes to the develop branch by submitting pull requests. There are no restrictions on how a repository can be forked - individual contributors may fork a repository or an organisation may create their own fork to channel contributions. Similarly, the pull requests are expected to range from corrections to spelling mistakes through to entire new profiles. All we ask is that improvements are contributed back to the main branch for the benefit of all.

## Editors
Editors are responsible for coordinating the publishing of resources created by the community of contributors.

Editors review pull requests for consistency prior to merging into develop.Periodically, editors create a release candidate. Where appropriate, editors seek wider review of assets within release candidate including clinical review, connectathon testing. Following successful review, assets are marked as active and published to master branch. Github webhooks are configured to automatically publish master branch from github to Furore's simplifier registry [https://www.simplifier.net/] to share  assets until such time as a UK-specific registry is available.

## Editorial policy
Profiles should follow the HL7 FHIR standard so that standard tooling can be used.

### Editorial principles
These principles broadly adopt the established Code4Health interoperability community design principles [https://code4health.org/communities/interoperability/groups/design]

#### Share freely
When sharing resources, enable information repositories to share freely i.e. provide flexibility to include whatever information that they are willing and able to share.

This means that:

1. common profiles should rarely (if ever?) constrain out properties in the core profiles. As part of this, we need to carefully consider modifierExtension as this places constraints on the information consumers.
2. common profiles should set minimum constraints necessary for interoperability within England (? UK), especially where we have an agreed national standard. For example, Patient.identifier should include an NHS Number, a CodeableConcept should include a SNOMED code etc.
3. Where common elements can be identified, provide guidance on how to share them in a consistent way. For example, it's far more important to profile Address to provide a common definition than to require use of Address within every Patient resource (initially emphasise the data dictionary rather than the data model?).

#### Accept grudgingly
When accepting resources, enable information repositories to constrain freely i.e. they must have flexibility to constrain the information they accept to reflect internal constraints and policies.

This means that:

1. common profiles should set only the minimum constraints necessary for interoperability within the UK.
2. information repositories are responsible for publishing profiles describing the resources they accept. These profiles extend the common profiles and constrain out data items that can't be accepted. I would expect these profiles to be aggressive in how they constrain! There is nothing to preclude a special interest group defining a common profile that they use by mutual agreement.

#### Naming
Names will be informative to implementors and consistent across the profiles.

The scheme for profile naming is:

    CareConnect-{{profile.name}}-{{major}}

#### Versioning
Resource versioning follows Semantic Versioning [http://semver.org/]. Resources carry major version in name (e.g. CareConnect-Foo-2) and major/minor version within StructureDefinition/Conformance. 

Major versions will be maintained in parallel for a period of time before deprecation (period to be confirmed, but anticipated to be at least 12 months).

