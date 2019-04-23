---
title: Error del compilador C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d05a861a2baedb86482503b6860098f12c41bd78
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776462"
---
# <a name="compiler-error-c3399"></a>Error del compilador C3399

'tipo': no se pueden proporcionar argumentos cuando se crea una instancia de un parámetro genérico

Cuando se especifica la restricción `gcnew()` , se indica que el tipo de restricción tendrá un constructor sin parámetros. Por lo tanto, es un error tratar de crear una instancia de ese tipo y pasar un parámetro.

Consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3399.

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```