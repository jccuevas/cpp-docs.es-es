---
title: Error del compilador C2919 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a70b679d4add5fa4ad2904e3c0d103e1c8881280
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2919"></a>Error del compilador C2919
'type': no se pueden usar operadores en la superficie publicada de un tipo WinRT  
  
 El sistema de tipos de Windows Runtime no admite las funciones miembro de operadores en la superficie publicada de un tipo. Esto es porque no todos los lenguajes pueden usar las funciones miembro de operadores. Puede crear funciones miembro de operadores privadas o internas que se pueden llamar desde el código de C++ en la misma clase o unidad de compilación.  
  
 Para corregir este problema, quite la función de miembro de operador de la interfaz pública o cámbiela por una función miembro con nombre. Por ejemplo, en lugar de `operator==`, asígnele a la función miembro el nombre `Equals`.
