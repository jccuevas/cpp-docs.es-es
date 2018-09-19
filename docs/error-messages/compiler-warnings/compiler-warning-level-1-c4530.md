---
title: Compilador advertencia (nivel 1) C4530 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbfbc67377dd48eeb692bdd4cac1f113fbdf7f6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110463"
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