---
title: Error del compilador C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 85381b237480b86b59c33f02601a1b9dc644a5a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761535"
---
# <a name="compiler-error-c3539"></a>Error del compilador C3539

' tipo ': un argumento de plantilla no puede ser un tipo que contiene ' auto '

El tipo de argumento de plantilla indicado no puede contener el uso de la palabra clave `auto`.

### <a name="to-correct-this-error"></a>Para corregir este error

1. No especifique el argumento de plantilla con la palabra clave `auto`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3539.

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)
