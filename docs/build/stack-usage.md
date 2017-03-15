---
title: "Uso de las pilas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Uso de las pilas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Toda la memoria a partir de la dirección actual de RSP se considera volátil: el SO, o un depurador, pueden sobrescribir esta memoria durante una sesión de depuración del usuario, o un controlador de interrupciones.  Por lo tanto, hay que establecer siempre RSP antes de intentar leer o escribir valores en un marco de pila.  
  
 En esta sección se explica la asignación de espacio de pila para las variables locales y para la función intrínseca **alloca**.  
  
-   [Asignación de espacio de pila](../build/stack-allocation.md)  
  
-   [Construcción del área de pila para el parámetro dinámico](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Tipos de funciones](../build/function-types.md)  
  
-   [Alineación de malloc](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)