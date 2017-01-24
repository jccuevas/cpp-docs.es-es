---
title: "PROPERTY_INFO_ENTRY_EX | Microsoft Docs"
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
  - "PROPERTY_INFO_ENTRY_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROPERTY_INFO_ENTRY_EX (macro)"
ms.assetid: af32dfcd-4c50-449d-af3b-48d21bd67a04
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PROPERTY_INFO_ENTRY_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una propiedad concreta de un conjunto de propiedades.  
  
## Sintaxis  
  
```  
  
PROPERTY_INFO_ENTRY_EX(  
dwPropID  
,  
vt  
,  
dwFlags  
,  
value  
,  
options  
)  
  
```  
  
#### Parámetros  
 *dwPropID*  
 \[in\] Valor [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) que se puede usar con el GUID del conjunto de propiedades para identificar una propiedad.  
  
 *vt*  
 \[in\] La [VARTYPE](http://msdn.microsoft.com/es-es/317b911b-1805-402d-a9cb-159546bc88b4) de esta entrada de la propiedad.  
  
 `dwFlags`  
 \[in\] Un valor [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) que describe esta entrada de la propiedad.  
  
 *valor*  
 \[in\] El valor de la propiedad de tipo `DWORD`.  
  
 `options`  
 **DBPROPOPTIONS\_REQUIRED** o **DBPROPOPTIONS\_SETIFCHEAP**. Normalmente, un proveedor no necesita establecer `options` ya que lo hace el consumidor.  
  
## Comentarios  
 Con esta macro, puede especificar directamente el valor de propiedad de tipo `DWORD` así como opciones y marcas. Para establecer simplemente una propiedad a un valor predeterminado definido en ATLDB.H, use [PROPERTY\_INFO\_ENTRY](../../data/oledb/property-info-entry.md). Para establecer una propiedad a un valor de su elección, sin establecer opciones ni marcas en ella, use [PROPERTY\_INFO\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md).  
  
## Ejemplo  
 Vea [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md).  
  
## Requisitos  
 **Encabezado:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)