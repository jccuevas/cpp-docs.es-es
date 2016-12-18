---
title: "CDBPropSet (Clase) | Microsoft Docs"
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
  - "CDBPropSet"
  - "ATL.CDBPropSet"
  - "ATL::CDBPropSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropSet (clase)"
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropSet (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hereda de la estructura de **DBPROPSET** y agregue un constructor que inicializa los campos clave junto con el método de acceso de `AddProperty` .  
  
## Sintaxis  
  
```  
class CDBPropSet : public tagDBPROPSET  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddProperty](../../data/oledb/cdbpropset-addproperty.md)|Agrega una propiedad al conjunto de propiedades.|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|Constructor.|  
|[SetGUID](../../data/oledb/cdbpropset-setguid.md)|Establece el campo de **guidPropertySet** de la estructura de **DBPROPSET** .|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../../data/oledb/cdbpropset-operator-equal.md)|Asigna el contenido de una propiedad establecida a otra.|  
  
## Comentarios  
 Los proveedores y los consumidores OLE DB utilizan estructuras de **DBPROPSET** para pasar matrices de las estructuras de `DBPROP` .  Cada estructura de `DBPROP` representa una única propiedad que puede establecer.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet \(Clase\)](../../data/oledb/cdbpropidset-class.md)   
 [DBPROPSET Structure](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)