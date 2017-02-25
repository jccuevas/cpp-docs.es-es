---
title: "BEGIN_PROPSET_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_PROPSET_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_PROPSET_MAP (macro)"
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# BEGIN_PROPSET_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marca el principio de las entradas del mapa del conjunto de propiedades.  
  
## Sintaxis  
  
```  
  
BEGIN_PROPSET_MAP(  
Class   
)  
  
```  
  
#### Parámetros  
 *Clase*  
 \[in\] La clase en la que especifican a este conjunto de propiedades.  Un conjunto de propiedades se puede especificar en los siguientes objetos OLE DB:  
  
-   [\<caps:sentence id\="tgt4" sentenceid\="75bbb794f21139fcd243c18fff6050d2" class\="tgtSentence"\>Objetos de origen de datos\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [\<caps:sentence id\="tgt5" sentenceid\="e423b0fba10fc83bd76e01e3eee2fd69" class\="tgtSentence"\>Objetos de sesión\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [\<caps:sentence id\="tgt6" sentenceid\="5f6bc08c46cee6f21bfcdd08aff6e8aa" class\="tgtSentence"\>Comandos\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## Ejemplo  
 A continuación se muestra un conjunto de propiedades del ejemplo asignado:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/CPP/begin-propset-map_1.h)]  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)