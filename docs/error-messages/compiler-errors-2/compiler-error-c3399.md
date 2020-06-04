---
title: Error del compilador C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d20b5e816930969278536fe3771df4ad38c3c86b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737522"
---
# <a name="compiler-error-c3399"></a>Error del compilador C3399

'tipo': no se pueden proporcionar argumentos cuando se crea una instancia de un parámetro genérico

Cuando se especifica la restricción `gcnew()` , se indica que el tipo de restricción tendrá un constructor sin parámetros. Por lo tanto, es un error tratar de crear una instancia de ese tipo y pasar un parámetro.

Consulte [restricciones en los parámetros de tipo genérico (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3399.

```cpp
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```
