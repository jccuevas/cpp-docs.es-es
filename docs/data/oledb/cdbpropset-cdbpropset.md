---
title: "CDBPropSet::CDBPropSet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBPropSet.CDBPropSet"
  - "CDBPropSet::CDBPropSet"
  - "ATL::CDBPropSet::CDBPropSet"
  - "ATL.CDBPropSet.CDBPropSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropSet (clase), constructor"
ms.assetid: 02ae5d9e-c067-47ca-8111-a03e86b5626b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDBPropSet::CDBPropSet
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Constructor.  Inicializa **rgProperties**, **cProperties**, y los campos de **guidPropertySet** de la estructura de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) .  
  
## Sintaxis  
  
```  
  
      CDBPropSet(  
   const GUID& guid   
);  
CDBPropSet(   
   const CDBPropSet& propset    
);  
CDBPropSet( );  
```  
  
#### Parámetros  
 `guid`  
 \[in\] GUID utilizado para inicializar el campo de **guidPropertySet** .  
  
 *propset*  
 \[in\] Otro objeto de `CDBPropSet` para la construcción de copia.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBPropSet \(Clase\)](../../data/oledb/cdbpropset-class.md)   
 [CDBPropSet::SetGUID](../../data/oledb/cdbpropset-setguid.md)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)