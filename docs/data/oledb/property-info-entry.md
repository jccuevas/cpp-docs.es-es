---
title: "PROPERTY_INFO_ENTRY | Microsoft Docs"
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
  - "PROPERTY_INFO_ENTRY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY (macro)"
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROPERTY_INFO_ENTRY
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una propiedad concreta de un conjunto de propiedades.  
  
## Sintaxis  
  
```  
  
PROPERTY_INFO_ENTRY(  
dwPropID   
)  
  
```  
  
#### Parámetros  
 *dwPropID*  
 \[in\] Valor [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) que se puede usar con el GUID del conjunto de propiedades para identificar una propiedad.  
  
## Comentarios  
 Esta macro establece el valor de propiedad de tipo `DWORD` en un valor predeterminado definido en ATLDB. H. Para establecer la propiedad en un valor de su elección, use [PROPERTY\_INFO\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md). Para establecer el [VARTYPE](http://msdn.microsoft.com/es-es/317b911b-1805-402d-a9cb-159546bc88b4) y [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) para la propiedad al mismo tiempo, use [PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md).  
  
## Ejemplo  
 Consulte [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md).  
  
## Requisitos  
 **Encabezado:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)