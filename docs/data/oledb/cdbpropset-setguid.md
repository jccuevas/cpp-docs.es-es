---
title: "CDBPropSet::SetGUID | Microsoft Docs"
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
  - "ATL.CDBPropSet.SetGUID"
  - "CDBPropSet.SetGUID"
  - "ATL::CDBPropSet::SetGUID"
  - "SetGUID"
  - "CDBPropSet::SetGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddProperty (método)"
  - "SetGUID (método)"
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropSet::SetGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el campo de **guidPropertySet** en la estructura de **DBPROPSET** .  
  
## Sintaxis  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### Parámetros  
 `guid`  
 \[in\] GUID utilizado para establecer el campo de **guidPropertySet** de la estructura de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) .  
  
## Comentarios  
 Este campo se puede establecer a [constructor](../../data/oledb/cdbpropset-cdbpropset.md) también.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBPropSet \(Clase\)](../../data/oledb/cdbpropset-class.md)