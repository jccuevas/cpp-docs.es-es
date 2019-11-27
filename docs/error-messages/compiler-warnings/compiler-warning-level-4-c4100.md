---
title: Advertencia del compilador (nivel 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 80794d270b40a8f40d44630da70455c015158423
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541242"
---
# <a name="compiler-warning-level-4-c4100"></a>Advertencia del compilador (nivel 4) C4100

' Identifier ': parámetro formal sin referencia

No se hace referencia al parámetro formal en el cuerpo de la función. Se omite el parámetro sin referencia.

C4100 también se puede emitir cuando el código llama a un destructor en un parámetro de tipo primitivo que, de otro modo, no se hace referencia.  Se trata de una limitación del compilador de Microsoft C++ .

En el ejemplo siguiente se genera C4100:

```cpp
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```