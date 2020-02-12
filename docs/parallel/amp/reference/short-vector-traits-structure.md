---
title: short_vector_traits (Estructura)
ms.date: 11/04/2016
f1_keywords:
- short_vector_traits
- AMP_SHORT_VECTORS/short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::short_vector_traits
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector_traits::size Constant
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
ms.openlocfilehash: 7531a57dddcc85392380029afc6edd577bbc5cf3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126385"
---
# <a name="short_vector_traits-structure"></a>short_vector_traits (Estructura)

short_vector_traits permite la recuperación de la longitud del vector subyacente y del tipo escalar de un tipo de vector corto o un tipo escalar.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    typename T
>
struct short_vector_traits;
template<>
struct short_vector_traits<unsigned int>;
template<>
struct short_vector_traits<uint_2>;
template<>
struct short_vector_traits<uint_3>;
template<>
struct short_vector_traits<uint_4>;
template<>
struct short_vector_traits<int>;
template<>
struct short_vector_traits<int_2>;
template<>
struct short_vector_traits<int_3>;
template<>
struct short_vector_traits<int_4>;
template<>
struct short_vector_traits<float>;
template<>
struct short_vector_traits<float_2>;
template<>
struct short_vector_traits<float_3>;
template<>
struct short_vector_traits<float_4>;
template<>
struct short_vector_traits<unorm>;
template<>
struct short_vector_traits<unorm_2>;
template<>
struct short_vector_traits<unorm_3>;
template<>
struct short_vector_traits<unorm_4>;
template<>
struct short_vector_traits<norm>;
template<>
struct short_vector_traits<norm_2>;
template<>
struct short_vector_traits<norm_3>;
template<>
struct short_vector_traits<norm_4>;
template<>
struct short_vector_traits<double>;
template<>
struct short_vector_traits<double_2>;
template<>
struct short_vector_traits<double_3>;
template<>
struct short_vector_traits<double_4>;
```

### <a name="parameters"></a>Parámetros

`T`

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[short_vector_traits:: short_vector_traits (constructor)](#ctor)||

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[short_vector_traits:: Size (constante)](#size)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`short_vector_traits`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_short_vectors. h

**Espacio de nombres:** Concurrency:: Graphics

## <a name="ctor"></a>short_vector_traits:: short_vector_traits (constructor)

```cpp
short_vector_traits();
```

## <a name="size"></a>short_vector_traits:: Size (constante)

```cpp
static int const size = 1;
```

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
