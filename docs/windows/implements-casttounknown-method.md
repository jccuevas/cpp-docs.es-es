---
title: "Implements::CastToUnknown (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Implements::CastToUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CastToUnknown (método)"
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Implements::CastToUnknown (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene un puntero a la interfaz subyacente de IUnknown.  
  
## Sintaxis  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## Valor devuelto  
 Esta operación se realiza correctamente y siempre devuelve el puntero de IUnknown.  
  
## Comentarios  
 Función interna de la aplicación auxiliar.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Implements \(Estructura\)](../Topic/Implements%20Structure.md)