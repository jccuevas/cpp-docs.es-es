---
title: Error del compilador C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 6df8fd3df023602f65c872dedd74da36bbbc6bd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649922"
---
# <a name="compiler-error-c3297"></a>Error del compilador C3297

'restricción_2': no se puede usar 'restricción_1' como restricción porque 'restricción_1' tiene la restricción de valor

Las clases de valor son de tipo sealed. Si una restricción es una clase de valor, otra restricción nunca puede derivar de ella.

Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3297.

```
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```