---
title: "CDBPropIDSet (Clase) | Microsoft Docs"
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
  - "CDBPropIDSet"
  - "ATL.CDBPropIDSet"
  - "ATL::CDBPropIDSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropIDSet (clase)"
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropIDSet (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hereda de la estructura de **DBPROPIDSET** y agregue un constructor que inicializa los campos clave junto con el método de acceso de [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) .  
  
## Sintaxis  
  
```  
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|Agrega una propiedad al conjunto de identificadores de la propiedad.|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|Constructor.|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|Establece el GUID del conjunto de identificadores de la propiedad.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../../data/oledb/cdbpropidset-operator-equal.md)|Asigna el contenido de un identificador de propiedad establecido en otro.|  
  
## Comentarios  
 Los consumidores OLE DB utilizan estructuras de **DBPROPIDSET** para pasar una matriz de los id. de propiedad para los que el consumidor desea obtener información de la propiedad.  Las propiedades identificadas en una única estructura de [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) pertenecen a un conjunto de propiedades.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)