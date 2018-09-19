---
title: Compilador advertencia (nivel 4) C4714 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4714
dev_langs:
- C++
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecb9ecb1c73373ae96c92c911988a512e2173cec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136106"
---
# <a name="compiler-warning-level-4-c4714"></a>Advertencia del compilador (nivel 4) C4714

la función 'función' marcada como __forceinline no está entre línea

La función especificada se ha seleccionado para la expansión en línea, pero el compilador no llevó a cabo la inserción.

Aunque `__forceinline` es una indicación de mayor prioridad al compilador que `__inline`, inserción todavía se realiza a discreción del compilador, pero no se utiliza heurística para determinar las ventajas de inclusión entre líneas esta función.

En algunos casos, el compilador no insertará una determinada función por motivos mecánicos. Por ejemplo, el compilador no insertará:

- Una función de si el resultado de la mezcla de SEH y C++ EH.

- Algunas funciones de copia construyen objetos pasados por valor cuando GX/EHs/EHa está activada.

- Funciones que devuelven un objeto por valor cuando GX/EHs/EHa está activada.

- Funciones con ensamblado en línea al compilar sin - Og/Ox/O1/O2.

- Funciones con una lista de argumentos de variable.

- Una función con un **intente** instrucción (control de excepciones de C++).

El ejemplo siguiente genera C4714:

```
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```