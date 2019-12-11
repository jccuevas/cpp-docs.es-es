---
title: Advertencia del compilador (nivel 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: bcd51c66359d0553b7657d85f5b45ee22d4648ff
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991649"
---
# <a name="compiler-warning-level-4-c4100"></a>Advertencia del compilador (nivel 4) C4100

'identificador': parámetro formal no referenciado

No se hace referencia al parámetro formal en el cuerpo de la función. Se omite el parámetro no referenciado.

También puede emitirse C4100 cuando el código llama a un destructor en un parámetro de tipo primitivo no referenciado de otra forma.  Se trata de una limitación del compilador de Microsoft C++ .

El código siguiente genera el error C4100:

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
