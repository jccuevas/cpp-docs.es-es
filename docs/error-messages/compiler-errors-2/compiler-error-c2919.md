---
title: Error del compilador C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: ab11226c8cc4629a265dd182d5f882f6b3be7e5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160863"
---
# <a name="compiler-error-c2919"></a>Error del compilador C2919

'type': No se puede usar operadores en la superficie publicada de un tipo WinRT

El sistema de tipos de Windows en tiempo de ejecución no admite las funciones miembro de operadores en la superficie publicada de un tipo. Esto es porque no todos los lenguajes pueden usar las funciones miembro de operadores. Puede crear funciones miembro de operadores privadas o internas que se pueden llamar desde el código de C++ en la misma clase o unidad de compilación.

Para corregir este problema, quite la función de miembro de operador de la interfaz pública o cámbiela por una función miembro con nombre. Por ejemplo, en lugar de `operator==`, asígnele a la función miembro el nombre `Equals`.