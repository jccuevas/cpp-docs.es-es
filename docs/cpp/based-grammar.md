---
title: "__based (Gram&#225;tica) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "direccionamiento con base"
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# __based (Gram&#225;tica)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 El direccionamiento de base es útil cuando se necesita el control preciso del segmento en el que se asignan los objetos \(datos basados estáticos y dinámicos\).  
  
 La única forma de direccionamiento de base aceptable en compilaciones de 32 bits y 64 bits es "basado en un puntero" que define un tipo que contiene un desplazamiento de 32 bits o de 64 bits respecto a una base de 32 bits o de 64 bits, o basado en `void`.  
  
## Gramática  
 *based\-range\-modifier*:  
 **\_\_based\(**  *base\-expression*  **\)**  
  
 *base\-expression*:  
 *based\-variablebased\-abstract\-declaratorsegment\-namesegment\-cast*  
  
 *based\-variable*:  
 *identifier*  
  
 *based\-abstract\-declarator*:  
 *abstract\-declarator*  
  
 *base\-type*:  
 *type\-name*  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Punteros con base](../cpp/based-pointers-cpp.md)