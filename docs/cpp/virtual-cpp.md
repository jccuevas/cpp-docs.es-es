---
title: virtual (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2471dac12db574aa045142a654effafadbabd732
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092278"
---
# <a name="virtual-c"></a>virtual (C++)

El **virtual** palabra clave declara una función virtual o una clase base virtual.

## <a name="syntax"></a>Sintaxis

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>Parámetros

*especificadores de tipo*<br/>
Especifica el tipo de valor devuelto de la función miembro virtual.

*declarador de función miembro*<br/>
Declara una función miembro.

*especificador de acceso*<br/>
Define el nivel de acceso a la clase base, **pública**, **protegido** o **privada**. Puede aparecer antes o después de la **virtual** palabra clave.

*nombre de clase base*<br/>
Identifica un tipo de clase declarado previamente.

## <a name="remarks"></a>Comentarios

Consulte [funciones virtuales](../cpp/virtual-functions.md) para obtener más información.

Consulte también las siguientes palabras clave: [clase](../cpp/class-cpp.md), [privada](../cpp/private-cpp.md), [pública](../cpp/public-cpp.md), y [protegido](../cpp/protected-cpp.md).

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)