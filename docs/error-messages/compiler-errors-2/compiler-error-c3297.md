---
title: Error del compilador C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 6fed01b0dcf50a657b6eb457ab8e546d0648beec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760105"
---
# <a name="compiler-error-c3297"></a>Error del compilador C3297

'restricción_2': no se puede usar 'restricción_1' como restricción porque 'restricción_1' tiene la restricción de valor

Las clases de valor son de tipo sealed. Si una restricción es una clase de valor, otra restricción nunca puede derivar de ella.

Para más información, consulte [Restricciones de parámetros de tipo genérico](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3297.

```cpp
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```
