---
title: "IErrorRecordsImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IErrorRecordsImpl"
  - "ATL.IErrorRecordsImpl"
  - "IErrorRecordsImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IErrorRecordsImpl (clase)"
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IErrorRecordsImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la interfaz OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) , agregando registros a y recuperar los registros de un miembro de datos \([m\_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)\) de **CAtlArray\<**tipo`RecordClass`**\>**.  
  
## Sintaxis  
  
```  
template <  
   class T,   
   class RecordClass = ATLERRORINFO  
>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### Parámetros  
 `T`  
 Una clase derivada de `IErrorRecordsImpl`.  
  
 `RecordClass`  
 Una clase que representa un objeto de error de OLE DB.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|Obtiene la cadena de descripción del error de un registro de errores.|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|Obtiene el error GUID de un registro de errores.|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|Obtiene el Id. de contexto de ayuda de un registro de errores.|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|Obtiene el nombre completo de la ruta de acceso del archivo de ayuda de un registro de errores.|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|Obtiene el código fuente de error de un registro de errores.|  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|Agrega un registro al objeto de error de OLE DB.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Devuelve información básica sobre el error, como el código devuelto y el número de error proveedor\- concreto.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Devuelve un puntero a una interfaz en un objeto de error personalizado.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Devuelve un puntero de interfaz de [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) en el registro especificado.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Devuelve los parámetros del error.|  
|[GetRecordCount](../Topic/CDaoRecordset::GetRecordCount.md)|Devuelve el número de registros del objeto log de OLE DB.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|Una matriz de registros de error.|  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)