---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 87d268977ee46112fedce517e66a9e68071863db
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457572"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Incluye el encabezado \<stddef. > h de la biblioteca estándar de C y agrega los `std` nombres asociados al espacio de nombres. Incluir este encabezado garantiza que los nombres declarados mediante vinculación externa en el encabezado de la biblioteca estándar `std` de C se declaran en el espacio de nombres.

> [!NOTE]
> \<cstddef > incluye el tipo **byte** y no incluye el tipo **wchar_t**.

## <a name="syntax"></a>Sintaxis

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Espacio de nombres y macros

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
Tipo de entero con signo definido por la implementación que puede contener la diferencia de dos subíndices en un objeto de matriz.

*size_t*\
Un tipo entero sin signo definido por la implementación que es lo suficientemente grande como para contener el tamaño en bytes de cualquier objeto.

*max_align_t*\
Un tipo POD cuyo requisito de alineación sea al menos tan grande como el de todos los tipos escalares, y cuyo requisito de alineación se admita en todos los contextos.

*nullptr_t*\
Sinónimo del tipo de una expresión **nullptr** . Aunque no se puede tomar una dirección **nullptr** , se puede tomar la dirección de otro objeto *nullptr_t* que es un valor l.

## <a name="byte-class"></a>byte (clase)

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

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
