---
title: "unsupported_feature (Clase) | Microsoft Docs"
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
  - "amprt/Concurrency::unsupported_feature"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unsupported_feature (clase)"
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unsupported_feature (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La excepción que se produce cuando se usa una función no compatible.  
  
## Sintaxis  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[unsupported\_feature::unsupported\_feature \(Constructor\)](../Topic/unsupported_feature::unsupported_feature%20Constructor.md)|Construye una nueva instancia de la excepción `unsupported_feature`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)