---
title: "Tipos de funciones | Microsoft Docs"
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
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tipos de funciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Básicamente, hay dos tipos de funciones.  Una función que requiere un marco de pila se denomina función de marco.  Una función que no requiere un marco de pila se denomina función de hoja.  
  
 Una función de marco es una función que asigna el espacio de la pila, llama a otras funciones, guarda registros no variables o utiliza el control de excepciones.  También requiere una entrada de la tabla de funciones.  Una función de marco requiere un prólogo y un epílogo.  Una función de marco puede asignar dinámicamente el espacio de la pila y puede emplear un puntero de marco.  Una función de marco tiene a su disposición toda la capacidad de este estándar de llamada.  
  
 Si una función de marco no llama a otra función, entonces no es necesario que alinee la pila \(se menciona en la sección [Asignación de espacio de pila](../build/stack-allocation.md)\).  
  
 Una función de hoja es aquella que no requiere una entrada de la tabla de funciones.  No puede llamar a otras funciones, ni asignar espacio ni guardar registros no variables.  Puede dejar sin alinear la pila mientras se ejecuta.  
  
## Vea también  
 [Uso de las pilas](../build/stack-usage.md)