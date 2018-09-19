---
title: Error del compilador C2383 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c529c22636f112291fa53b852899cad78dac589
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113232"
---
# <a name="compiler-error-c2383"></a>Error del compilador C2383

'*símbolo*': no se permiten argumentos predeterminados en este símbolo

El compilador de C++ no permiten argumentos predeterminados en punteros a funciones.

Este código fue aceptado por el compilador de Visual C++ en las versiones anteriores de Visual Studio 2005, pero ahora produce un error. Para el código que funciona en todas las versiones de Visual C++, no asigne un valor predeterminado para un argumento de puntero a función.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2383 y muestra una posible solución:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```