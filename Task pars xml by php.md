``` xml
<?xml version="1.0" encoding="UTF-8"?>
<Provisioning xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <Request>
      <Header>
         <Command>Create</Command>
         <EntityIdentifiers>
            <Identifier Type="TelephoneNumber" Value="436646997780" />
         </EntityIdentifiers>
         <EntityName>Subscriber</EntityName>
      </Header>
      <Data>
         <Subscriber>
            <SubscriberCosName>BobPrepaid</SubscriberCosName>
            <AMTEDestinations>
               <Value>l.breahna@unifun.com</Value>
               <Value>e.sidorov@unifun.com</Value>
           </AMTEDestinations>
           <CosOption>PowerBox</CosOption>
            <AMTEEnabled>false</AMTEEnabled>
            <AMTEOn>false</AMTEOn>
            <VVMDeviceType>4</VVMDeviceType>
            <GlobalLanguageId>de-AT</GlobalLanguageId>
         </Subscriber>
      </Data>
   </Request>
</Provisioning>
```

Нужно спарсить теги:
-   Command
-   Identifier->Value
-   А та же все узлы из тега Subscriber