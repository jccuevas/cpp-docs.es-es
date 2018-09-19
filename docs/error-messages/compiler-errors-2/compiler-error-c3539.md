---
title: Error del compilador C3539 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3539
dev_langs:
- C++
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2f78b69e00290dcc283e3fc340d25a4a071776
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091886"
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