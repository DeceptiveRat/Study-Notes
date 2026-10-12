
```xml
<Sysmon schemaversion="4.30">
  <EventFiltering>
    <RuleGroup name="" groupRelation="or">
      <!-- Rule for CreateRemoteThread (Event ID 8) -->
      <CreateRemoteThread onmatch="include">
        <SourceImage condition="is not">C:\Windows\System32\WerFault.exe</SourceImage>
        <SourceImage condition="is not">C:\Windows\explorer.exe</SourceImage>
      </CreateRemoteThread>
    </RuleGroup>

    <RuleGroup name="" groupRelation="or">
      <!-- Rule for ImageLoad (Event ID 7) -->
      <ImageLoad onmatch="include">
        <!-- Detect unsigned DLLs loading into signed processes -->
        <Signed condition="is not">true</Signed>
        <Signed condition="is not">true</Signed>
      </ImageLoad>
    </RuleGroup>

    <RuleGroup name="" groupRelation="or">
      <!-- Rule for ImageLoad from suspicious locations -->
      <ImageLoad onmatch="include">
        <Image condition="contains">\AppData\</Image>
      </ImageLoad>
    </RuleGroup>

    <RuleGroup name="" groupRelation="or">
      <!-- Rule for ProcessAccess (Event ID 10) on sensitive processes -->
      <ProcessAccess onmatch="include">
        <TargetImage condition="end with">lsass.exe</TargetImage>
        <GrantedAccess condition="contains">0x1F3FFF</GrantedAccess> <!-- Look for high-privilege access -->
      </ProcessAccess>
    </RuleGroup>

    <RuleGroup name="" groupRelation="or">
      <FileCreateStreamHash onmatch="include">
      </FileCreateStreamHash>
    </RuleGroup>

    <RuleGroup name="" groupRelation="or">
      <NetworkConnect onmatch="include">
      </NetworkConnect>
    </RuleGroup>

    <RuleGroup name="" groupRelation="or">
      <FileCreate onmatch="include">
	        <TargetFilename condition="is not">C:\Windows\asdasdfsf</TargetFilename>
      </FileCreate>
    </RuleGroup>

    <RuleGroup name="" groupRelation="or">
      <RegistryEvent onmatch="include">
      </RegistryEvent>
    </RuleGroup>

  </EventFiltering>
</Sysmon>
```

*** TargetFilename tag under FileCreate is necessary to make it work!!! ***