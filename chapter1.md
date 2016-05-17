# PackagerService配置

## 整体xml结构

```
<tasks>
  <task name="" outputfolder="">
    <flow name="" sql="" conn="conn" folder="">
      <folder name="">
        <group groupby="">
          <output type="word" 
                  conn="conn" 
                  template="" 
                  parameters="" 
                  filenamefield="template" />
          <output type=
        </group>
      </folder>
    </flow>
    ...
  </task>
  ...
</tasks>
```
