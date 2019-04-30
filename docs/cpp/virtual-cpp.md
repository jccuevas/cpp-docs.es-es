---
title: virtual (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: f68bd2e500ebe16c43ef6c3d7a5aede26421b27d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393914"
---
# <a name="virtual-c"></a>virtual (C++)

El **virtual** palabra clave declara una función virtual o una clase base virtual.

## <a name="syntax"></a>Sintaxis

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>Parámetros

*type-specifiers*<br/>
Especifica el tipo de valor devuelto de la función miembro virtual.

*member-function-declarator*<br/>
Declara una función miembro.

*access-specifier*<br/>
Define el nivel de acceso a la clase base, **pública**, **protegido** o **privada**. Puede aparecer antes o después de la **virtual** palabra clave.

*base-class-name*<br/>
Identifica un tipo de clase declarado previamente.

## <a name="remarks"></a>Comentarios

Consulte [funciones virtuales](../cpp/virtual-functions.md) para obtener más información.

Consulte también las siguientes palabras clave: [clase](../cpp/class-cpp.md), [privada](../cpp/private-cpp.md), [pública](../cpp/public-cpp.md), y [protegido](../cpp/protected-cpp.md).

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)