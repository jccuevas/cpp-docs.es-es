---
title: "CAccessorBase::GetHAccessor | Microsoft Docs"
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
  - "GetHAccessor"
  - "CAccessorBase::GetHAccessor"
  - "CAccessorBase.GetHAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetHAccessor (método)"
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase::GetHAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el identificador de descriptor de acceso de un descriptor de acceso especificado.  
  
## Sintaxis  
  
```  
  
      HACCESSOR GetHAccessor(  
   ULONG nAccessor   
) const;  
```  
  
#### Parámetros  
 `nAccessor`  
 \[in\] El número de cero\- desplazamiento para el descriptor de acceso.  
  
## Valor devuelto  
 El identificador de descriptor de acceso.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CAccessorBase \(Clase\)](../../data/oledb/caccessorbase-class.md)