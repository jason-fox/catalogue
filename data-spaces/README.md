# FIWARE for Data Spaces

This section describes the components of the FIWARE Catalogue that can be picked up, integrated together, and eventually
combined with other components in order to build the soft infrastructure and services required for creating data spaces
where smart applications from multiple domains can participate and exchange data. Smart applications participating in
such data spaces share digital twin data in near real-time (right-time) using the open standard NGSI-LD API and relying
on common data models. Each smart solution contributes to build a complete digital twin data representation of the real
world sharing their data through a Context Broker that implements the NGSI-LD API. At the same time, they can exploit
data shared by other applications. FIWARE Data Publication components like Idra enable the publication and discovery of
data resources in a standard manner. Relying on Marketplace services created using FIWARE
Business-API-Ecosystem/Marketplace components, on the other hand, participants of created Data Spaces can publish
offerings around access to data resources or data processing services under concrete terms and conditions which
establish data usage/access policies to be enforced and may include pricing. Finally, FIWARE components implementing
Identity and Access Management (IAM) functions enable to secure that data is accessed by the right parties and that
defined access policies are enforced.

## Contents

-   [Background](#background)
-   [Technology Building Blocks](#technology-building-blocks)
    -   [Data Interoperability](#data-interoperability)
    -   [Data Sovereignty and Trust](#data-sovereignty-and-trust)
    -   [Data Value Creation](#data-value-creation)
-   [Integrating Building Blocks for data spaces](#integrating-building-blocks-for-data-spaces)
    -   [NGSI-LD Data Service Provider](#ngsi-ld-data-service-provider)
    -   [Data Marketplace](#data-marketplace)

## Background

A **data space** is defined as a decentralised infrastructure for trustworthy data sharing and exchange in data
ecosystems based on commonly agreed principles. From a technical perspective, a number of **technology building blocks**
are required ensuring:

-   **Data interoperability** - Data spaces should provide a solid framework for an efficient exchange of data among
    participants, supporting full decoupling of data providers and consumers. This requires the adoption of a “common
    lingua” every participant uses, materialized in the adoption of common APIs for the data exchange, and the
    definition of common data models. Common mechanisms for traceability of data exchange transactions and data
    provenance, are also required.

-   **Data Sovereignty and trust** - Data spaces should bring technical means for guaranteeing that participants in a
    data space can trust each other and exercise sovereignty over data they share. This requires the adoption of common
    standards for managing the identity of participants, the verification of their truthfulness and the enforcement of
    policies agreed upon data access and usage control.

-   **Data value creation** - Data spaces should provide support for the creation of multi-sided markets where
    participants can generate value out of sharing data (i.e., creating data value chains). This requires the adoption
    of common mechanisms enabling the definition of terms and conditions (including pricing) linked to data offerings,
    the publication and discovery of such offerings and the management of all the necessary steps supporting the
    lifecycle of contracts that are established when a given participant acquires the rights to access and use data.

Besides the adoption of a common technology foundation, data spaces also require **governance**, that is the adoption of
a number of business, operational and organizational agreements among participants. Business agreements, for example,
specify what kind of terms and conditions can regulate the sharing of data between participants and the legal framework
supporting contracts established through the data space. Operational agreements, on the other hand, regulate policies
that have to be enforced during data space operation like, for example, compliance with GDPR (General Data Protection
Regulation) or the 2nd Payment Services Directive (PSD2) in the finance sector. They may also comprise the definition of
tools that operators of cloud infrastructures or global services supporting data spaces must implement, enabling
auditing of certain processes or the adoption of cyber-security practices. In addition, organizational agreements
establish the governance bodies (very much like ICANN for the Internet). They deal with the identification of concrete
specifications that products implementing technology building blocks in a data space should comply with, as well as the
business and operational agreements to be adopted. The complete taxonomy of building blocks required for creating data
spaces is illustrated in the following figure.

![DataSpacesBuildingBlocks](https://fiware.github.io/catalogue/img/data-spaces-building-blocks.png "Data Spaces Building Blocks")

Sharing of data within a given data space should not be limited to a single domain. This would severely limit the
creation of new innovative services since individuals and organizations usually act in multiple domains at the same time
and many opportunities will flourish when data generated within organizations operating in certain domain (management of
traffic in cities, for example) is shared for its exploitation in processes relevant to other domains (continuing with
the example, logistics). Therefore, technology building blocks for data spaces must be domain-agnostic. On the other
hand, they should rely on open standards, allowing multiple infrastructure and global service providers to emerge and
support data spaces, without getting locked in any particular provider. Given this, while making things work in living
labs and pilots is relatively easy, the main challenge towards definition of successful data spaces is the decision of
what concrete standards and design principles are adopted, since they have to be accepted by all participants.

## Technology Building blocks

This section describes the different components FIWARE brings materializing the different technical building blocks
enabling the soft infrastructure and global services required for creation of data spaces.

### Data Interoperability

#### Data Exchange API

Data providers joining data spaces must be able to publish data resources at well defined endpoints knowing that data
consumers, unknown by them a priori, will know how to retrieve and consume data through those endpoints. Data consumers,
on the other hand, must know how data available through endpoints they discover can be consumed. This is achieved by
adopting domain-agnostic common APIs for data exchange.

The **NGSI API** represents such API and many different systems have been developed using it in domains such as smart
cities, smart manufacturing, smart energy, smart water, smart agrifood, smart ports, or smart health. Data exchange
based on the NGSI API is implemented by the
[Core Context Broker components](https://github.com/FIWARE/catalogue#core-context-broker-components) like the Orion-LD,
Scorpio or Stellio Context Brokers.

#### Data Models & Formats

Combined with the data exchange APIs, achieving full interoperability also requires the adoption of common data models
to be represented in formats compatible with the API. The [Smart Data Model](https://github.com/smart-data-models)
initiative provides a library of data model specifications mapped into concrete JSON and JSON-LD data structures
compatible with the NGSI-LD API.

#### Provenance & Traceability

FIWARE brings components which provide the means for tracing and tracking in the process of data provision and data
consumption/use. It provides the basis for a number of important functions, from identification of the provenance of
data to audit-proof logging of NGSI-LD transactions. For those data spaces with strong requirements on transparency and
certification, FIWARE brings components (i.e., [Canis Major](https://github.com/FIWARE/CanisMajor)) that ease recording
of transaction logs into different **Distributed Ledgers / Blockchains**.

### Data Sovereignty and Trust

Data spaces must provide means for guaranteeing organizations joining data spaces that they can trust the other
participants and that they will be able to exercise sovereignty on their data. That requires the definition of common
building blocks, based on mature security standards that will be used by all participants in the data space.

The [FIWARE Security Access and API Management](../security/README.md) components implement these building blocks.

#### Identity Management

The building block of Identity Management allows identification, authentication, and authorization of organizations,
individuals, machines and other actors participating in a data space. FIWARE brings the
[Keyrock](https://github.com/ging/fiware-idm) component which supports [OpenIdConnect](https://openid.net/connect/),
[SAML 2.0](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html) and
[OAuth2](https://oauth.net/2/) standards. Quite relevant for data spaces deployed in Europe, Keyrock also resolves
integration with [eIDAS](https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/eID), a building block provided by the
European Commission that enables the mutual recognition of national electronic identification schemes (eID) across
borders, allowing European citizens to use their national eIDs when accessing online services from other European
countries.

#### Trusted exchange

Trusted data exchange among participants provides certainty that participants involved in the data exchange are who they
claim to be, and that they comply with defined rules/agreements. Trust refers to the fact that data providers and data
consumers can rely on the identity of the members of the data ecosystem and beyond that, between different security
domains. Here, **IDS Connector technology**, as described in the
[IDS Reference Architecture Model (RAM)](https://internationaldataspaces.org/download/16630/), emerges as a solid basis.

The FIWARE Community has incubated an open source implementation of this technology, the
[TRUE (TRUsted Engineering) Connector](https://github.com/Engineering-Research-and-Development/true-connector) that has
already been tested on how it can integrate with the rest of core FIWARE components. The TRUE Connector enables trusted
data exchange in data spaces that intend to be aligned with the
[IDS Reference Architecture Model](https://internationaldataspaces.org/wp-content/uploads/IDS-Reference-Architecture-Model-3.0-2019.pdf).
It brings the necessary capabilities to interact with external Identity Providers for verification and validation of
tokens, and also allows for usage control. It is also referenced in the
[Security Access and API Management](../security/README.md) section.

#### Access & Usage Control / Policies

Access and usage control guarantees enforcement of data access and usage policies defined as part of the terms and
conditions established when data resources or services are published or negotiated between providers and consumers. An
API proxy plays the role of the Policy Enforcement Point (PEP) and requires an additional Policy Decision Point (PDP).
Below listed are the FIWARE GEs implementing the PEP and PDP functionalities.

_PEP_:

-   [Wilma](https://github.com/ging/fiware-pep-proxy)
-   [API Umbrella](https://github.com/FIWARE/api-umbrella)
-   [CoatRack](https://github.com/coatrack/coatrack/)

_PDP_:

-   [AuthZForce](https://github.com/authzforce/server)
-   [Keyrock](https://github.com/ging/fiware-idm)
-   [API Umbrella](https://github.com/FIWARE/api-umbrella)

In addition, [Keyrock](https://github.com/ging/fiware-idm) also implements Policy Administration Point (PAP) and Policy
Management Point (PMP) standard [XACML](https://en.wikipedia.org/wiki/XACML) functions.

### Data Value Creation

Loose coupling of participants is a fundamental principle in data spaces. Data providers and consumers do not
necessarily know about each other. Therefore, it becomes essential to incorporate building blocks enabling the
management of data resources as true assets with a business value. Assets which can be published, discovered and,
eventually, traded. This way boosting the creation of multi-side markets where innovative services can be created.

Components under the FIWARE [API Management, Data Publication and Monetization](../data-publication/README.md) section
facilitate the building blocks listed below for data value creation.

#### Metadata & Discovery Services

This building block incorporates publishing and discovery mechanisms for data resources and services, making use of
common descriptions of resources, services, and participants.

#### Publication & Marketplace Services

To support the offering of data resources and services under defined terms and conditions, marketplaces must be
established. This building block supports publication of these offerings, management of processes linked to the creation
and monitoring of smart contracts (which clearly describe the rights and obligations for data and service usage), and
access to data and services.

The [Business API Ecosystem](https://github.com/FIWARE-TMForum/Business-API-Ecosystem) provides sellers the means for
managing, publishing, and generating revenue of their products, apps, data, and services. The Business API Ecosystem
enables the monetization of different kinds of assets (both digital and physical) across the whole service life cycle,
from offer creation through to charging, accounting and revenue settlement and sharing. It relies on a set of standard
APIs (and its reference implementations) provided by the TMForum in its TMF API ecosystem.

[Idra](https://github.com/OPSILab/Idra) is a web application able to federate existing Open Data Management Systems
(ODMS) based on different technologies providing a unique access point to search and discover open datasets coming from
heterogeneous sources. It supports natively ODMS based on CKAN, DKAN, Socrata, Orion Context Broker (NGSI v2, NGSI-LD)
and many other technologies: Idra provides also a set of APIs to federate ODMS not natively supported.

#### Data Usage Accounting

This building block provides the basis for accounting access to and/or usage of data by different users. This in turn is
supportive of important functions for clearing, payment, and billing (including data-sharing transactions without
involvement of data marketplaces).

## Integrating Building Blocks for data spaces

This section demonstrates common setups of the integration of the different building blocks for the creation of data
spaces and links to deployment instructions for Kubernetes. It will be enriched over time.

### NGSI-LD Data Service Provider

An NGSI based service provider can be any (right-time) data service or data processing provider. For instance, the
underlying Context Broker could provide right-time data from different external devices via the NGSI API, or receive
data for further data processing. Access to the Context Broker instance would be protected by an API PEP Proxy.

These [instructions](https://github.com/FIWARE/production-on-k8s/tree/main/NGSI-LD_Data-Provider) describe how to set up
an environment of such a data service provider based on the following components:

-   Orion Context Broker as NGSI API service provider
-   API Umbrella as API PEP Proxy (and probably PDP)
-   Optionally Keyrock (in case it is used as PDP and/or managing the user’s roles for authorization)

In addition, all these components require different databases to be set up.

### Data Marketplace

The data marketplace is based on the Business API Ecosystem (BAE) which allows service providers to publish offerings
around data assets, and service consumers to acquire access to them. A full instance is based on the BAE itself, the
Keyrock Identity Manager and several databases. These
[instructions](https://github.com/FIWARE/production-on-k8s/tree/main/business-api-ecosystem) describe how to deploy a
full setup on Kubernetes.
