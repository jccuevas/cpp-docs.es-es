---
title: Error del compilador C3133
ms.date: 11/04/2016
f1_keywords:
- C3133
helpviewer_keywords:
- C3133
ms.assetid: 4a709405-b67b-4061-8a2a-19fa5fb34a2a
ms.openlocfilehash: 0a0c30203f886934a19fde35e51602b57cc1b14d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164857"
---
# <a name="compiler-error-c3133"></a>Error del compilador C3133

No se puede aplicar atributos a varargs de C++

Se aplicó incorrectamente un atributo. No se pueden aplicar atributos a un botón de puntos suspensivos que representa los argumentos de variable.

Para obtener más información, consulte [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3133.

```
// C3133.cpp
// compile with: /clr /c
ref struct MyAttr: System::Attribute {};
void Func([MyAttr]...);   // C3133
void Func2([MyAttr] int i);   // OK
```