---
title: "CUtlProps::SetPropValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetPropValue"
  - "ATL::CUtlProps<T>::SetPropValue"
  - "ATL.CUtlProps<T>.SetPropValue"
  - "ATL.CUtlProps.SetPropValue"
  - "CUtlProps::SetPropValue"
  - "CUtlProps<T>::SetPropValue"
  - "CUtlProps.SetPropValue"
  - "CUtlProps<T>.SetPropValue"
  - "ATL::CUtlProps::SetPropValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetPropValue (método)"
ms.assetid: 69a703c0-f640-4ca3-8850-0c4e75d52429
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CUtlProps::SetPropValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece una propiedad en un conjunto de propiedades.  
  
## Sintaxis  
  
```  
  
      HRESULT SetPropValue(  
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
 \[in\] Un puntero a un tipo Variant que contiene el nuevo valor de propiedad.  
  
## Valor devuelto  
 `Failure` en el error y `S_OK` si correctamente.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [CUtlProps \(Clase\)](../../data/oledb/cutlprops-class.md)