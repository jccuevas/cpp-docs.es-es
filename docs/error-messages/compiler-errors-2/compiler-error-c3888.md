---
title: Error del compilador C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 40156dfaad5965d30a32d3aa2ac574a5f91999ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176409"
---
# <a name="compiler-error-c3888"></a>Error del compilador C3888

'name': C++/CLI no admite la expresión const asociada con este miembro de datos literal

El miembro de datos *name* que se declara con la palabra clave [literal](../../extensions/literal-cpp-component-extensions.md) se inicializa con un valor que no es compatible con el compilador. El compilador solo admite los tipos de constante integral, de enumeración o de cadena. La causa probable del error **C3888** es que el miembro de datos se inicializa con una matriz de bytes.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Compruebe que el miembro de datos declarado literal es un tipo admitido.

## <a name="see-also"></a>Consulte también

[literal](../../extensions/literal-cpp-component-extensions.md)
