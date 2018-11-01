---
title: Error del compilador C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 067412e59041cb98b68cb373c4671c243ab8a0ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479071"
---
# <a name="compiler-error-c3888"></a>Error del compilador C3888

'name': C++/CLI no admite la expresión const asociada con este miembro de datos literal

El miembro de datos *name* que se declara con la palabra clave [literal](../../windows/literal-cpp-component-extensions.md) se inicializa con un valor que no es compatible con el compilador. El compilador solo admite los tipos de constante integral, de enumeración o de cadena. La causa probable del error **C3888** es que el miembro de datos se inicializa con una matriz de bytes.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Compruebe que el miembro de datos declarado literal es un tipo admitido.

## <a name="see-also"></a>Vea también

[literal](../../windows/literal-cpp-component-extensions.md)