---
title: Error del compilador C3393
ms.date: 11/04/2016
f1_keywords:
- C3393
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
ms.openlocfilehash: 5147e3e406fde73a05b7069e2a9336f27b3db622
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328671"
---
# <a name="compiler-error-c3393"></a>Error del compilador C3393

error de sintaxis en la cláusula de restricciones: 'identifier' no es un tipo

El identificador que se pasó a una restricción, que debe ser un tipo, no es un tipo.  Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3393:

```
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