---
title: "Implements::FillArrayWithIid (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Implements::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid (método)"
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Implements::FillArrayWithIid (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inserta el identificador de interfaz especificado por el parámetro actual de la plantilla de zeroth en el elemento de matriz especificado.  
  
## Sintaxis  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### Parámetros  
 `index`  
 Un índice cero\- basado en que indica el elemento de matriz inicial para esta operación.  Cuando esta operación finaliza, `index` se incrementa en 1.  
  
 `iids`  
 Una matriz de IID escrito.  
  
## Comentarios  
 Función interna de la aplicación auxiliar.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Implements \(Estructura\)](../Topic/Implements%20Structure.md)