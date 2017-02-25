---
title: "COleObjectFactory Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleObjectFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class factories, COleObjectFactory class"
  - "COleObjectFactory class"
  - "creación de objetos, objetos OLE"
  - "objetos [C++], crear OLE"
  - "OLE class factory"
  - "objetos OLE"
  - "objetos OLE, crear"
  - "OLE, class factory"
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# COleObjectFactory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa el generador\) de la clase, que crea objetos OLE como servidores, objetos de automatización, y documentos.  
  
## Sintaxis  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](../Topic/COleObjectFactory::COleObjectFactory.md)|Crea un objeto `COleObjectFactory`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](../Topic/COleObjectFactory::GetClassID.md)|Devuelve el identificador de la clase OLE de los objetos que esta generador crea.|  
|[COleObjectFactory::IsLicenseValid](../Topic/COleObjectFactory::IsLicenseValid.md)|Determina si la licencia de control es válida.|  
|[COleObjectFactory::IsRegistered](../Topic/COleObjectFactory::IsRegistered.md)|Indica si el generador de objeto está registrada con los archivos DLL de OLE del sistema.|  
|[COleObjectFactory::Register](../Topic/COleObjectFactory::Register.md)|Registra esta generador de objeto con los archivos DLL de OLE del sistema.|  
|[COleObjectFactory::RegisterAll](../Topic/COleObjectFactory::RegisterAll.md)|Registra los generadores del objeto de toda la aplicación con archivos DLL de OLE del sistema.|  
|[COleObjectFactory::Revoke](../Topic/COleObjectFactory::Revoke.md)|Revoca el registro de esta generador de objeto con los archivos DLL de OLE del sistema.|  
|[COleObjectFactory::RevokeAll](../Topic/COleObjectFactory::RevokeAll.md)|Revoca los registros de los generadores de objetos de una aplicación con los archivos DLL de OLE del sistema.|  
|[COleObjectFactory::UnregisterAll](../Topic/COleObjectFactory::UnregisterAll.md)|Anula todo de generadores de objeto de una aplicación.|  
|[COleObjectFactory::UpdateRegistry](../Topic/COleObjectFactory::UpdateRegistry.md)|Registra esta generador de objeto con el sistema OLE.|  
|[COleObjectFactory::UpdateRegistryAll](../Topic/COleObjectFactory::UpdateRegistryAll.md)|Registra los generadores del objeto de toda la aplicación con el sistema OLE.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](../Topic/COleObjectFactory::GetLicenseKey.md)|Solicita una clave única de la DLL del control.|  
|[COleObjectFactory::OnCreateObject](../Topic/COleObjectFactory::OnCreateObject.md)|Llamado por el marco para crear un nuevo objeto de tipo de este generador.|  
|[COleObjectFactory::VerifyLicenseKey](../Topic/COleObjectFactory::VerifyLicenseKey.md)|Comprueba que coincida con la clave inline en el control la clave inline en el contenedor.|  
|[COleObjectFactory::VerifyUserLicense](../Topic/COleObjectFactory::VerifyUserLicense.md)|Comprueba que el control sea licencia para su uso en tiempo de diseño.|  
  
## Comentarios  
 La clase de `COleObjectFactory` tiene funciones miembro para realizar las funciones siguientes:  
  
-   administrar el registro de objetos.  
  
-   Actualizar el sistema OLE, así como el registro en tiempo de ejecución que comunica a OLE que los objetos se ejecutan y listos para recibir mensajes.  
  
-   Aplicando la autorización limitando el uso del control a los desarrolladores con licencia en tiempo de diseño y aplicaciones de licencia en tiempo de ejecución.  
  
-   Registrar generadores del objeto de control con el sistema OLE.  
  
 Para obtener más información sobre la creación de objetos, vea los artículos [objetos de datos y orígenes de datos \(OLE\)](../../mfc/data-objects-and-data-sources-ole.md) y [objetos de datos y orígenes de datos: creación y Destruction](../../mfc/data-objects-and-data-sources-creation-and-destruction.md).  Para obtener más información sobre el registro, vea el artículo [registro](../../mfc/registration.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)