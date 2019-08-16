---
title: Advertencia del compilador (nivel 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: a542f9b6bb73e561592e1e779aa6ee493612e6ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160723"
---
# <a name="compiler-warning-level-1-c4530"></a>Advertencia del compilador (nivel 1) C4530

Controlador de excepciones de C++ que utiliza, pero la semántica de desenredo no están habilitadas. Especifique /EHsc

Se usó el control de excepciones de C++ pero [/EHsc](../../build/reference/eh-exception-handling-model.md) no se ha seleccionado.

Cuando no se ha habilitado la opción/EHsc, un objeto con almacenamiento automático en el marco, entre la función que realiza la captura y la función que captura el throw, no se destruirá. Sin embargo, se crea un objeto con almacenamiento automático en un **intente** o **catch** bloque que se va a destruir.

El ejemplo siguiente genera C4530:

```
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Compile el ejemplo con/EHsc para resolver la advertencia.