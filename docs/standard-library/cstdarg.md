---
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: 0b45d5f591c5394ffa861e75169dce70f53b1baf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448024"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

Incluye el encabezado \<stdarg. > h de la biblioteca estándar de C y agrega los nombres `std` asociados al espacio de nombres. Incluir este encabezado garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar `std` de C se declaran en el espacio de nombres.

## <a name="syntax"></a>Sintaxis

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>Espacio de nombres y macros

```cpp
namespace std {
    using va_list = see below;
}

#define va_arg(V, P)
#define va_copy(VDST, VSRC)
#define va_end(V)
#define va_start(V, P)
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
