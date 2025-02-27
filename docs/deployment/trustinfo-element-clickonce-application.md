---
title: '&lt;trustInfo&gt; elemento (applicazione ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3dd75e8c88f87991abbdaa74a711b8f3c7324b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927299"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>Elemento &lt;trustInfo&gt; (applicazione ClickOnce)
Descrive le autorizzazioni di sicurezza minime richieste per l'esecuzione dell'applicazione nel computer client.

## <a name="syntax"></a>Sintassi

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `trustInfo` è obbligatorio e si trova nello spazio dei nomi `asm.v2` . Non ha attributi e contiene gli elementi seguenti.

## <a name="security"></a>sicurity
 Obbligatorio. Questo elemento è figlio dell'elemento `trustInfo` . Contiene l'elemento `applicationRequestMinimum` e non dispone di attributi.

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 Obbligatorio. Questo elemento è figlio dell'elemento `security` e contiene gli elementi `PermissionSet`, `assemblyRequest`e `defaultAssemblyRequest`. Questo elemento non ha attributi.

## <a name="permissionset"></a>PermissionSet
 Obbligatorio. Questo elemento è figlio dell'elemento `applicationRequestMinimum` e contiene l'elemento `IPermission` . Questo elemento ha gli attributi seguenti.

- `ID`

     Obbligatorio. Identifica il set di autorizzazioni. Questo attributo può avere qualsiasi valore. Gli attributi `defaultAssemblyRequest` e `assemblyRequest` fanno riferimento all'ID.

- `version`

     Obbligatorio. Identifica la versione dell'autorizzazione. In genere questo valore è `1`.

## <a name="ipermission"></a>IPermission
 Facoltativo. Questo elemento è figlio dell'elemento `PermissionSet` . L'elemento `IPermission` identifica in modo completo una classe di autorizzazioni in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. L'elemento `IPermission` ha gli attributi seguenti, ma può avere attributi aggiuntivi che corrispondono alle proprietà della classe di autorizzazioni. Per scoprire la sintassi di un'autorizzazione specifica, vedere gli esempi elencati nel file Security.config.

- `class`

     Obbligatorio. Identifica la classe di autorizzazioni in base al nome sicuro. Ad esempio, il codice seguente identifica il tipo `FileDialogPermission` .

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     Obbligatorio. Identifica la versione dell'autorizzazione. In genere questo valore è `1`.

- `Unrestricted`

     Obbligatorio. Indica se l'applicazione richiede una concessione senza restrizioni di questa autorizzazione. Se `true`, la concessione dell'autorizzazione è non condizionale. Se `false`, o se questo attributo non è definito, è limitata in base agli attributi specifici dell'autorizzazione definiti nel tag `IPermission` . Si analizzino le autorizzazioni seguenti:

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     In questo esempio, la dichiarazione per <xref:System.Security.Permissions.EnvironmentPermission> impedisce all'applicazione di leggere solo la variabile di ambiente USERNAME, mentre la dichiarazione per <xref:System.Security.Permissions.FileDialogPermission> consente all'applicazione di usare senza restrizioni tutte le classi <xref:System.Windows.Forms.FileDialog> .

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 Facoltativo. Identifica il set di autorizzazioni concesso agli assembly. Questo elemento è figlio dell'elemento `applicationRequestMinimum` e ha l'attributo seguente.

- `permissionSetReference`

     Obbligatorio. Identifica l'ID del set di autorizzazioni che è l'autorizzazione predefinita. Il set di autorizzazioni viene dichiarato nell'elemento `PermissionSet` .

## <a name="assemblyrequest"></a>assemblyRequest
 Facoltativo. Identifica le autorizzazioni per un assembly specifico. Questo elemento è figlio dell'elemento `applicationRequestMinimum` e ha l'attributo seguente.

- `Name`

     Obbligatorio. Identifica il nome dell'assembly.

- `permissionSetReference`

     Obbligatorio. Identifica l'ID del set di autorizzazioni richiesto dall'assembly. Il set di autorizzazioni viene dichiarato nell'elemento `PermissionSet` .

## <a name="requestedprivileges"></a>requestedPrivileges
 Facoltativo. Questo elemento è figlio dell'elemento `security` e contiene l'elemento `requestedExecutionLevel` . Questo elemento non ha attributi.

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 Facoltativo. Identifica il livello di sicurezza a cui eseguire le richieste dell'applicazione. Questo elemento non ha figli e ha gli attributi seguenti.

- `Level`

   Obbligatorio. Indica il livello di sicurezza richiesto dall'applicazione. I possibili valori sono:

   `asInvoker`, non vengono richieste autorizzazioni aggiuntive. Questo livello non richiede prompt di attendibilità aggiuntivi.

   `highestAvailable`, viene richiesto il livello più elevato di autorizzazioni disponibile nel processo padre.

   `requireAdministrator`, vengono richieste autorizzazioni di amministrazione complete.

   Le applicazioni[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verranno installate solo con un valore `asInvoker`. L'installazione con qualsiasi altro valore avrà esito negativo.

- `uiAccess`

   Facoltativo. Indica se l'applicazione richiede l'accesso agli elementi protetti dell'interfaccia utente. I valori sono `true` o `false`e il valore predefinito è false. Solo le applicazioni firmate devono avere un valore true.

## <a name="remarks"></a>Note
 Se un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] richiede altre autorizzazioni rispetto a quelle concesse per impostazione predefinita al computer client, il gestore di attendibilità di Common Language Runtime chiederà all'utente se vuole concedere all'applicazione un livello così elevato di attendibilità. Se l'utente rifiuta, l'applicazione non verrà eseguita. In caso contrario, eseguirà le autorizzazioni richieste.

 Tutte le autorizzazioni richieste mediante `defaultAssemblyRequest` e `assemblyRequest` verranno concesse senza chiedere all'utente se il manifesto di distribuzione ha una licenza di attendibilità valida.

 Per altre informazioni sull'elevazione delle autorizzazioni, vedere [protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md). Per altre informazioni sulla distribuzione dei criteri, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

## <a name="examples"></a>Esempi
 I seguenti tre esempi di codice descrivono gli elementi `trustInfo` per le aree di sicurezza denominate predefinite, ovvero Internet, LocalIntranet e FullTrust, per l'uso in un manifesto dell'applicazione di distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Il primo esempio descrive l'elemento `trustInfo` per le autorizzazioni predefinite disponibili nell'area di sicurezza Internet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 Il secondo esempio descrive l'elemento `trustInfo` per le autorizzazioni predefinite disponibili nell'area di sicurezza LocalIntranet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 Il terzo esempio descrive l'elemento `trustInfo` per le autorizzazioni predefinite disponibili nell'area di sicurezza FullTrust.

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)