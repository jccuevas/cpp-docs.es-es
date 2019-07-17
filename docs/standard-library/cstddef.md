---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 15d13a3af35cb41950df8aeba0c86d779e701ddb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244446"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Incluye el encabezado de la biblioteca estándar de C \<stddef.h > y agrega los nombres asociados a la `std` espacio de nombres. Incluir este encabezado también garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar de C se declaran en el `std` espacio de nombres.

> [!NOTE]
> \<cstddef > incluye tipo **bytes** y no incluye el tipo **wchar_t**.

## <a name="syntax"></a>Sintaxis

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Macros y Namespace

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>Parámetros

*ptrdiff_t*\
Una implementación definido por el tipo con signo de entero que puede contener la diferencia entre dos subíndices en un objeto de matriz.

*size_t*\
Un tipo definido por la implementación de entero sin signo que es lo suficientemente grande como para contener el tamaño en bytes de cualquier objeto.

*max_align_t*\
Un tipo POD, cuyos requisitos de alineación es al menos tan grande que el de todos los tipos escalares y cuyos requisitos de alineación se admiten en todos los contextos.

*nullptr_t*\
Un sinónimo del tipo de un **nullptr** expresión. Aunque un **nullptr** dirección no se pueden tomar, la dirección de otro *nullptr_t* se puede tomar el objeto que es un valor l.

## <a name="byte-class"></a>bytes de clase

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
