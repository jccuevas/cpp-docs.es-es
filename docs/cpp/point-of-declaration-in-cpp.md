---
title: Punto de declaración en C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68ac24fcfe35701dd75d74800661aa5e41c005f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072073"
---
# <a name="point-of-declaration-in-c"></a>Punto de declaración en C++

Se considera que un nombre se declara inmediatamente después de su declarador pero antes de su inicializador (opcional). (Para obtener más información sobre los declaradores, vea [declaraciones y definiciones](declarations-and-definitions-cpp.md).)

Considere este ejemplo:

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

Si el punto de declaración estuviera *después* la inicialización, a continuación, en el equipo local `dVar` se inicializaría en 7.0, el valor de la variable global `dVar`. Sin embargo, como este no es el caso, `dVar` se inicializa en un valor no definido.

## <a name="see-also"></a>Vea también

[Ámbito](../cpp/scope-visual-cpp.md)