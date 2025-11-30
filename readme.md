# Clinical Data Repository and Trust Integration Engine 

## Install instructions

(Intersystems IRIS Data Platform including FHIR Repository)
FHIR Repository [Intersystems Open Exchange - iris-fhir-template](https://openexchange.intersystems.com/package/iris-fhir-template)

## Useful links 

Username: _System 
Password: SYS

- Command Line - On mac, using docker studio, use exec window and start using 'irissession IRIS' command.
- Management Portal [IRIS Managment Portal](http://localhost:32783/csp/sys/UtilHome.csp)
- SQL Explorer - [IRIS SQL Explorer](http://localhost:32783/csp/sys/exp/%25CSP.UI.Portal.SQL.Home.zen?$NAMESPACE=FHIRSERVER)

```sql
SELECT 
*
FROM HSFHIR_X0001_S.Observation
where patient = 'Patient/6' and code [ '38483-4';
````

## Development

### Visual Studio 

https://docs.intersystems.com/components/csp/docbook/DocBook.UI.Page.cls?KEY=GVSCO_intro

### Python - Intersystems + FHIR packages

`pip install intersystems-irispython`

`pip install sqlalchemy-iris`

`pip install fhir.resources`



## Notes

####  Patient Data Fix

[iris-fhir-template issue 32](https://github.com/intersystems-community/iris-fhir-template/issues/32)

Follow instructions up to this command

`FHIRSERVER>d ##class(fhirtemplate.Setup).LoadPatientData("/irisdev/app/output/fhir","FHIRSERVER","/fhir/r4")`

Instead

Using [IRIS Package Manager](http://localhost:32783/csp/sys/mgr/%25CSP.UI.Portal.Mappings.zen?MapType=Prj&PID=FHIRSERVER) map package `fhirtemplate` from USER namespace.

Copy contents of

> output\fhir

These need to be copied to

> data\fhir

Which is a mapped folder in the docker-compose. Then the load command is (presuming the class has been mapped to FHIRSERVER namespace)

> d ##class(fhirtemplate.Setup).LoadPatientData("/data/fhir","FHIRSERVER","/fhir/r4")

### Useful resources

Intersystems (France) Engineer
https://github.com/SylvainGuilbaud?tab=repositories

