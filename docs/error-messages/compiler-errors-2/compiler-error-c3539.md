---
title: Error del compilador C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: be1051859ebbcbdc22a9b71f8c5adba2e75c4e92
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
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

[Auto (palabra clave)](../../cpp/auto-keyword.md)