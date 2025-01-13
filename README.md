# entity
- application: application for which properties have to be sourced
- profile: for an application, which profile has the properties
- label: for a profile, which label has the properties (branch in git)


# defining backends to source properties
application.yml / bootstrap.yml
```yaml
spring:
  application:
    profiles:
    active: git, mongodb
```
- order of backends are specified using attribute order

# git setup
- create a repo with name entity.application
- Create application specific file (entity.application-entity.profile.properties) or common file (application-entity.profile.properties)
- add properties
- e.g. https://github.com/rishighai97-config-service/myapp/blob/main/myapp-qa.properties

# mongodb setup
- add spring-data dependency in build.gradle
- add database connection settings (url, db, collection) in application.yml
- create properties document in mongo collection for app
- e.g. 
```json
{
  "application": "myapp",
  "profile": "qa",
  "label": "main",
  "properties": {
    "property1": "mongoValue1-qa",
    "property2": "mongoValue2-qa",
    "property3": "mongoValue3-qa"
  }
}
```

# todo
- test for multiple application having common properties
- test for same repo having properties for all applications