---
title: "ChainInterfaces::Verify (M&#233;todo) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces::Verify"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Verify (método)"
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces::Verify (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba que cada interfaz definida por los parámetros `I0` de plantilla con `I9` hereda de IUnknown o de IInspectable, y que `I0` hereda de `I1` con `I9`.  
  
## Sintaxis  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## Comentarios  
 Si se produce un error en la operación de comprobación, `static_assert` emite un mensaje de error que describe el error.  
  
## Comentarios  
 Se requieren los parámetros `I0` y `I1` de la plantilla, y los parámetros `I2` con `I9` son opcionales.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ChainInterfaces \(Estructura\)](../windows/chaininterfaces-structure.md)