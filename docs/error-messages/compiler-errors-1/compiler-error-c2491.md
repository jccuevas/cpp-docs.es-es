---
title: Error del compilador C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 3b48bebde6d7baedea73ed181cd4ea33adc44a69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361339"
---
# <a name="compiler-error-c2491"></a>Error del compilador C2491

'identifier': definición de la función dllimport no permitida

Los datos, los miembros de datos estáticos y las funciones pueden declararse como `dllimport`s, pero no definirse como `dllimport`s.

Para solucionar este problema, quite el especificador `__declspec(dllimport)` de la definición de la función.

El código siguiente genera el error C2491:

```
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```