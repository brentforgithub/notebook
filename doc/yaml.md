## yaml配置文件
-----


### 配置注意事项
    - 注意事项1
    - 注意事项1

-----

### 配置map,list格式 
 - yaml
```yaml
      demo:
        key: demo1
        demoMap:
            onekey: 23123
            twokey: 23125
        demoList:
            - aaaa
            - bbbb
            - cccc
        list: topic1,topic2,topic3
        maps: "{key1: 'value1', key2: 'value2'}"
```
- java

```java

@ConfigurationProperties(prefix = "demo")
@Component
public class Config {
    @Value("${demo.key}")
    private String demoKey;

    private Map<String,String> demoMap;

    private List<String> demoList;

    @Value("#{'${demo.list}'.split(',')}")
    private List<String> list;

    @Value("#{${demo.maps}}")
    private Map<String,String> maps;

    public String getDemoKey() {
        return demoKey;
    }

    public void setDemoKey(String demoKey) {
        this.demoKey = demoKey;
    }

    public Map<String, String> getDemoMap() {
        return demoMap;
    }

    public void setDemoMap(Map<String, String> demoMap) {
        this.demoMap = demoMap;
    }

    public List<String> getDemoList() {
        return demoList;
    }

    public void setDemoList(List<String> demoList) {
        this.demoList = demoList;
    }
}
```

demoMap和demoList 的方式，要有@ConfigurationProperties(prefix = "demo")和set方法。

list和maps 的方式，一定要用""把map所对应的value包起来，要不然解析会失败，导致不能转成 Map<String,String>。


--------
[《《 返回主页](../readme.md)