---
title: Error del compilador C2919 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5e2eb2a32f1a906814f5b347ba1ebf13eba71ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2919"></a>Error del compilador C2919
'type': no se pueden usar operadores en la superficie publicada de un tipo WinRT  
  
 El sistema de tipos de Windows Runtime no admite las funciones miembro de operadores en la superficie publicada de un tipo. Esto es porque no todos los lenguajes pueden usar las funciones miembro de operadores. Puede crear funciones miembro de operadores privadas o internas que se pueden llamar desde el código de C++ en la misma clase o unidad de compilación.  
  
 Para corregir este problema, quite la función de miembro de operador de la interfaz pública o cámbiela por una función miembro con nombre. Por ejemplo, en lugar de `operator==`, asígnele a la función miembro el nombre `Equals`.