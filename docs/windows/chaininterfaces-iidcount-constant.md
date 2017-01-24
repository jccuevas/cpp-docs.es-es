---
title: "ChainInterfaces::IidCount (Constante) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces::IidCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IidCount (constante)"
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces::IidCount (Constante)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El número total de id. de interfaz contenidos en las interfaces especificadas por los parámetros `I0` de plantilla con `I9`.  
  
## Sintaxis  
  
```  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## Valor devuelto  
 El número total de id. de la interfaz.  
  
## Comentarios  
 Se requieren los parámetros `I0` y `I1` de la plantilla, y los parámetros `I2` con `I9` son opcionales. El número de identificador IID de cada interfaz es normalmente 1.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ChainInterfaces \(Estructura\)](../windows/chaininterfaces-structure.md)