---
title: "PROPERTY_INFO_ENTRY_VALUE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROPERTY_INFO_ENTRY_VALUE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY_VALUE (macro)"
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROPERTY_INFO_ENTRY_VALUE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una propiedad concreta en un conjunto de propiedades.  
  
## Sintaxis  
  
```  
  
PROPERTY_INFO_ENTRY_VALUE(  
dwPropID  
, value )  
```  
  
#### Parámetros  
 *dwPropID*  
 \[in\] Un valor de [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) que se puede utilizar junto con la propiedad GUID determinado para identificar una propiedad.  
  
 *valor*  
 \[in\] El valor de propiedad de `DWORD`escrito.  
  
## Comentarios  
 Con esta macro, puede especificar directamente el valor de propiedad de `DWORD`escrito.  Para establecer la propiedad en el valor predeterminado definido en ATLDB.H, utilice [PROPERTY\_INFORMATION\_ENTRY](../../data/oledb/property-info-entry.md).  Para establecer el valor, los marcadores, y las opciones para la propiedad, utilice [PROPERTY\_INFORMATION\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md).  
  
## Ejemplo  
 Vea [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)