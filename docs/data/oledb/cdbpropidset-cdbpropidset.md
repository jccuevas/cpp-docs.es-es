---
title: "CDBPropIDSet::CDBPropIDSet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDBPropIDSet::CDBPropIDSet"
  - "CDBPropIDSet"
  - "CDBPropIDSet.CDBPropIDSet"
  - "CDBPropIDSet::CDBPropIDSet"
  - "ATL.CDBPropIDSet.CDBPropIDSet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBPropIDSet (clase), constructor"
ms.assetid: e68cc20e-fce2-4cc1-9e9d-05c542334cc8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDBPropIDSet::CDBPropIDSet
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Constructor.  Inicializa **rgProperties**, **cProperties**, y \(opcionalmente\) los campos de **guidPropertySet** de la estructura de [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) .  
  
## Sintaxis  
  
```  
  
      CDBPropIDSet(  
   const GUID& guid   
);  
CDBPropIDSet(   
   const CDBPropIDSet& propidset    
);  
CDBPropIDSet( );  
```  
  
#### Parámetros  
 `guid`  
 \[in\] GUID utilizado para inicializar el campo de **guidPropertySet** .  
  
 *propidset*  
 \[in\] Otro objeto de `CDBPropIDSet` para la construcción de copia.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBPropIDSet \(Clase\)](../../data/oledb/cdbpropidset-class.md)   
 [CDBPropIDSet::SetGUID](../../data/oledb/cdbpropidset-setguid.md)