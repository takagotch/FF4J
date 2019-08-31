### ff4j
---
https://github.com/ff4j/ff4j

http://www.ff4j.org/

```java
// ff4j-core/src/main/java/org/ff4j/core/FlippingExecutionContext.java

public class FlippingExecutionContext {
  
  private transient Map<String, Object> parameters = new HashMap<String, Object>();
  
  public FlippingExecutionContext() {}
  
  public FlippingExecutionContext(Map<String, Object> init) {
    this.parameters = init;
  }
  
  public FlippingExecutionContext(FlippintExecutionContext executionContext) {
    this.parameters.putAll(executionContext.parameters);
  }
  
  public Object getValue(String key, boolean required) {
    if (!parameters.containKey(key)) {
      if (required) {
        throw new IllegalArgumentException("Parameter '" + key
          + "' has not been found but it's required to evaluate strategy");
      }
      return null;
    }
    return parameters.get(key);
  }
  
  public boolean containsKey(String key) {
    return parameters.containsKey(key);
  }
  
  
  
  
  public void putDouble(String key, Double value) {
    this.addValue(key, value);
  }
  
  public boolean isEmpty() {
    return parameters.isEmpty();
  }
  
  @Override
  public boolean equals(Object obj) {
    if(obj == this) {
      return true;
    }
    
    if (obj instanceof FlippingExecutioncontext) {
      FlippingExecutioncontext ctx = (FlippingExecutionContext) obj;
      return Objects.equalss(parameters, ctx.parameters);
    }
    return false;
  }
  
  @Override
  public int hasCode() {
    return Objects.hashCode(parameters);
  }
}

```

```
```

```
```


