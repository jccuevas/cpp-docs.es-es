---
title: Del compilador (nivel 1) de la advertencia C4288 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8b9e82f8cb24c4635fb64c3ac0a1c82e301c086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056498"
---
# <a name="compiler-warning-level-1-c4288"></a>Advertencia del compilador (nivel 1) C4288

ha utilizado una extensión no estándar: 'var': variable de control de bucles declarada en el bucle for se utiliza fuera del ámbito del bucle for; entra en conflicto con la declaración en el ámbito externo

Cuando se compila con [/Ze](../../build/reference/za-ze-disable-language-extensions.md) y **forScope**, una variable declarada en un **para** bucle se usa después la [para](../../cpp/for-statement-cpp.md)-ámbito del bucle. Una extensión de Microsoft del lenguaje C++ permite que esta variable permanezca dentro del ámbito y C4288 te recuerda que no se utiliza la primera declaración de la variable.

Consulte [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) para obtener información sobre cómo especificar la extensión de Microsoft en **para** bucles con/Ze.

El ejemplo siguiente genera la advertencia C4288:

```
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```