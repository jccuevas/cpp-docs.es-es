---
title: "CriticalSectionTraits::GetInvalidValue (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInvalidValue (método)"
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSectionTraits::GetInvalidValue (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especial una plantilla de CriticalSection de modo que la plantilla es siempre no válida.  
  
## Sintaxis  
  
```  
inline static Type GetInvalidValue();  
```  
  
## Valor devuelto  
 Siempre devuelve un puntero a una sección crítica no válida.  
  
## Comentarios  
 Definen el modificador de *Type* como `typedef CRITICAL_SECTION* Type;`.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits  
  
## Vea también  
 [CriticalSectionTraits \(Estructura\)](../windows/criticalsectiontraits-structure.md)