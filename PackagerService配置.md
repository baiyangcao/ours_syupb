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
          <output type="excel"
                  conn="conn"
                  template=""
                  parameters=""
                  filenamefield="template" />
          <output type="service"
                  conn="conn"
                  sql=""
                  parameters=""
                  filenamefield="FileName"
                  serviceparameters=""
                  resulttype="[file]|type">
            <service name="" location="" method="">
              <parameter name="" valuetype="[raw]|sql" value=""
                sqlname="" connname=""/>
            </service>
          </output>
          <output type="draft"
                  conn="conn"
                  sql=""
                  parameters=""
                  filenamefield="FileName"
                  fileobjfield="FileOBj" />
        </group>
      </folder>
    </flow>
    ...
  </task>
  ...
</tasks>
```
