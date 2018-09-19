---
title: Error del compilador C2919 | Microsoft Docs
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
ms.openlocfilehash: 5d6ee01e32cd1855855fa6ac071af159be8bac0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106836"
---
# <a name="compiler-error-c2919"></a>Error del compilador C2919

'type': no se pueden usar operadores en la superficie publicada de un tipo WinRT

El sistema de tipos de Windows Runtime no admite las funciones miembro de operadores en la superficie publicada de un tipo. Esto es porque no todos los lenguajes pueden usar las funciones miembro de operadores. Puede crear funciones miembro de operadores privadas o internas que se pueden llamar desde el código de C++ en la misma clase o unidad de compilación.

Para corregir este problema, quite la función de miembro de operador de la interfaz pública o cámbiela por una función miembro con nombre. Por ejemplo, en lugar de `operator==`, asígnele a la función miembro el nombre `Equals`.