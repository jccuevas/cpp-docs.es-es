---
title: "CDBPropIDSet::SetGUID | Microsoft Docs"
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
  - "CDBPropIDSet.SetGUID"
  - "ATL::CDBPropIDSet::SetGUID"
  - "SetGUID"
  - "ATL.CDBPropIDSet.SetGUID"
  - "CDBPropIDSet::SetGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetGUID (método)"
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBPropIDSet::SetGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el campo GUID en la estructura de **DBPROPIDSET** .  
  
## Sintaxis  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### Parámetros  
 `guid`  
 \[in\] GUID utilizado para establecer el campo de **guidPropertySet** de la estructura de [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) .  
  
## Comentarios  
 Este campo se puede establecer a [constructor](../../data/oledb/cdbpropidset-cdbpropidset.md) también.  Llame a esta función si utiliza el constructor predeterminado para esta clase.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDBPropIDSet \(Clase\)](../../data/oledb/cdbpropidset-class.md)