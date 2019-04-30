---
title: stdext (espacio de nombres)
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: d40f3f7a99db72784cc9a32a9c37064228597d34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412428"
---
# <a name="stdext-namespace"></a>stdext (espacio de nombres)

Los miembros de la [ \<hash_map >](../standard-library/hash-map.md) y [ \<hash_set >](../standard-library/hash-set.md) archivos de encabezado no son parte de la imagen ISO C++ estándar. Por lo tanto, estos tipos y miembros se movieron del espacio de nombres `std` al espacio de nombres `stdext`, para seguir siendo compatibles con el estándar de C++.

Cuando se compila con [/Ze](../build/reference/za-ze-disable-language-extensions.md), que es el valor predeterminado, el compilador advierte sobre el uso de `std` para los miembros de la \<hash_map > y \<hash_set > archivos de encabezado. Para deshabilitar la advertencia, use el pragma [warning](../preprocessor/warning.md) .

Para que el compilador genere un error por el uso de `std` para los miembros de la \<hash_map > y \<hash_set > archivos de encabezado con **/Ze**, agregue la siguiente directiva antes de `#include` cualquier C++ archivos de encabezado de la biblioteca estándar.

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

Cuando se compila con **/Za**, el compilador genera un error.

## <a name="see-also"></a>Vea también

[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)
