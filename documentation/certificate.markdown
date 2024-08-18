---
layout: default
permalink: /documentation/certificate/
---
# Integration with certificate generation entities and data cycle
The certificate generation entities are a key part of the solution, it is use to send the amount of energy generated from the different generators. Since different entities might be used depending of the country / market where the solution is being deployed, a a service must be selected to operate with.

## Integration with certificate generation entity
Currently one service for certificate generation entity is supported and must implement the interface `tech.renovus.solarec.certificateCertificateService` and implement the required method for the data cycle. The different methods will allow the registration of different clients and the amount energy generated, and will return the required information to be used in future operations.

Currently 4 services are available:
- `tech.renovus.solarec.certificate.disabled.DisabledCertificateService` (solarec.service.certificate.provider = disabled)
- `tech.renovus.solarec.certificate.drecs.DrecsCertificateService` (solarec.service.certificate.provider = drecs)
- `tech.renovus.solarec.certificate.surentis.SurentisCertificateService` (solarec.service.certificate.provider = surentis)
- `tech.renovus.solarec.certificate.irec.br.IrecBrCertificateService` (solarec.service.certificate.provider = irecbr)

In order to determinate the service to be use, you need to the set the `solarec.service.certificate.provider` property in the `application.properties` files.

