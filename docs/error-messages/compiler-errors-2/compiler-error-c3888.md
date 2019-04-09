---
title: Error del compilador C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: e4d52946126e7be6c6f2aef34b5eb5a93a0babad
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033646"
---
# <a name="compiler-error-c3888"></a>Error del compilador C3888

'name': C++/CLI no admite la expresión const asociada con este miembro de datos literal

El miembro de datos *name* que se declara con la palabra clave [literal](../../extensions/literal-cpp-component-extensions.md) se inicializa con un valor que no es compatible con el compilador. El compilador solo admite los tipos de constante integral, de enumeración o de cadena. La causa probable del error **C3888** es que el miembro de datos se inicializa con una matriz de bytes.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Compruebe que el miembro de datos declarado literal es un tipo admitido.

## <a name="see-also"></a>Vea también

[Literal](../../extensions/literal-cpp-component-extensions.md)