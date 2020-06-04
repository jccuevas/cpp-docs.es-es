---
title: Error del compilador C3393
ms.date: 11/04/2016
f1_keywords:
- C3393
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
ms.openlocfilehash: 0f6952de20c27a811b85694ae13892eff9231f83
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757545"
---
# <a name="compiler-error-c3393"></a>Error del compilador C3393

error de sintaxis en la cláusula de restricciones: 'identifier' no es un tipo

El identificador que se pasó a una restricción, que debe ser un tipo, no es un tipo.  Para más información, consulte [Restricciones de parámetros de tipo genérico](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3393:

```cpp
// C3393.cpp
// compile with: /clr /c
void MyInterface() {}
interface class MyInterface2 {};

generic<typename T>
where T : MyInterface   // C3393
// try the following line instead
// where T : MyInterface2
ref class R {};
```
