2017-10-12

## Static Resource

##### default location

`classpath:/static/`

`classpath:/public/`

`classpath:/resources/`

`classpath:/META-INF/resources/`

`/`

```js
public class ResourceProperties implements ResourceLoaderAware {

  // ...

  /**
   * Locations of static resources. Defaults to classpath:[/META-INF/resources/,
   * /resources/, /static/, /public/] plus context:/ (the root of the servlet context).
   */
  private String[] staticLocations = RESOURCE_LOCATIONS;

  // ...
```

##### customize location

```
# application.properties
spring.resources.static-locations (Locations of static resources)  string[]
```
