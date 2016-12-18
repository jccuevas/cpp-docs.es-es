---
title: "alloca | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# alloca
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es preciso que la función [\_alloca](../c-runtime-library/reference/alloca.md) sea de 16 bytes alineados y, además, es preciso que utilice un puntero de marco.  
  
 La pila asignada tiene que incluir espacio por debajo de la función para los parámetros de las funciones a las que se llame posteriormente, tal y como se describe en [Asignación de espacio de pila](../build/stack-allocation.md).  
  
## Vea también  
 [Uso de las pilas](../build/stack-usage.md)