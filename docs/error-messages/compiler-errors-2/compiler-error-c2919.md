---
title: "Compiler Error C2919 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2919"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2919"
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Compiler Error C2919
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': no se pueden usar operadores en la superficie publicada de un tipo WinRT  
  
 El sistema de tipos de Windows en tiempo de ejecución no admite las funciones miembro de operadores en la superficie publicada de un tipo.  Esto es porque no todos los lenguajes pueden usar las funciones miembro de operadores.  Puede crear funciones miembro de operadores privadas o internas que se pueden llamar desde el código de C\+\+ en la misma clase o unidad de compilación.  
  
 Para corregir este problema, quite la función de miembro de operador de la interfaz pública o cámbiela por una función miembro con nombre.  Por ejemplo, en lugar de `operator==`, asígnele a la función miembro el nombre `Equals`.