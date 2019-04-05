---
title: Error del compilador C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: be1051859ebbcbdc22a9b71f8c5adba2e75c4e92
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025185"
---
# <a name="compiler-error-c3539"></a>Error del compilador C3539

'type': un argumento de plantilla no puede ser un tipo que contiene 'auto'

El tipo de argumento de plantilla indicada no puede contener un uso de la `auto` palabra clave.

### <a name="to-correct-this-error"></a>Para corregir este error

1. No se especifica el argumento de plantilla con el `auto` palabra clave.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3539.

```
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

[auto (Palabra clave)](../../cpp/auto-keyword.md)