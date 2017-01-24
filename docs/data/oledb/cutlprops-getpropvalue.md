---
title: "CUtlProps::GetPropValue | Microsoft Docs"
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
  - "CUtlProps::GetPropValue"
  - "CUtlProps.GetPropValue"
  - "GetPropValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPropValue (método)"
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::GetPropValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene una propiedad de un conjunto de propiedades.  
  
## Sintaxis  
  
```  
  
      OUT_OF_LINE HRESULT GetPropValue(  
   const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue   
);  
```  
  
#### Parámetros  
 `pguidPropSet`  
 \[in\] GUID para el PropSet.  
  
 `dwPropId`  
 \[in\] El índice de la propiedad.  
  
 `pvValue`  
 \[out\] Un puntero a un tipo Variant que contiene el nuevo valor de propiedad.  
  
## Valor devuelto  
 `Failure` en el error y `S_OK` si correctamente.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CUtlProps \(Clase\)](../../data/oledb/cutlprops-class.md)