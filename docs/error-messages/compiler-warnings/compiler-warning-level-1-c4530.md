---
title: Advertencia del compilador (nivel 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 69ca60e2cba338bf1bd1ac3470e583739e72a68e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186457"
---
# <a name="compiler-warning-level-1-c4530"></a>Advertencia del compilador (nivel 1) C4530

C++controlador de excepciones usado, pero la semántica de desenredo no está habilitada. Especificar/EHsc

C++se usó el control de excepciones pero no se seleccionó [/EHsc](../../build/reference/eh-exception-handling-model.md) .

Cuando no se ha habilitado la opción/EHsc, un objeto con almacenamiento automático en el marco, entre la función que realiza la operación Throw y la función que detecta Throw, no se destruirá. Sin embargo, se destruirá un objeto con almacenamiento automático creado en un bloque **try** o **catch** .

En el ejemplo siguiente se genera C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Compile el ejemplo con/EHsc para resolver la advertencia.
