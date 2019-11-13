---
title: ADVERTENCIA del compilador (nivel 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 3139d321bca64b9938badebdabccd3ca1eb96d11
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966260"
---
# <a name="compiler-warning-level-1-c4530"></a>ADVERTENCIA del compilador (nivel 1) C4530

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