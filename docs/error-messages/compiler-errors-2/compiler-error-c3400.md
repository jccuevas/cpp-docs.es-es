---
title: Error del compilador C3400
ms.date: 11/04/2016
f1_keywords:
- C3400
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
ms.openlocfilehash: c4b4cb64da83115ab5b6a5234cda2ea3c7ba3a53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300380"
---
# <a name="compiler-error-c3400"></a>Error del compilador C3400

dependencia de restricción circular que implica 'constraint_1' y 'constraint_2'

El compilador detectó restricciones circulares.

Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3400.

```
// C3400.cpp
// compile with: /clr /c
generic<class T, class U>
where T : U
where U : T   // C3400
public ref struct R {};
```