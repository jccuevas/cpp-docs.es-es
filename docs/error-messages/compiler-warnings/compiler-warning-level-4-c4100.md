---
title: Advertencia del compilador (nivel 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: ccb438cf7c80edb1403683ac4817617ffccc690d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447732"
---
# <a name="compiler-warning-level-4-c4100"></a>Advertencia del compilador (nivel 4) C4100

'identifier': parámetro formal sin referencia

No se hace referencia el parámetro formal en el cuerpo de la función. Se omite el parámetro no referenciado.

También puede emitirse C4100 cuando el código llama a un destructor en un parámetro de tipo primitivo no.  Esta es una limitación de Microsoft C++ compilador.

El ejemplo siguiente genera el error C4100:

```
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