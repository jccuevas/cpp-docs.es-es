---
title: short_vector (Estructura)
ms.date: 11/04/2016
f1_keywords:
- short_vector
- AMP_SHORT_VECTORS/short_vector
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector::short_vector Constructor
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
ms.openlocfilehash: fc2864477da80885b18dabb08b9ccbee30f31387
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374750"
---
# <a name="short_vector-structure"></a>short_vector (Estructura)

short_vector proporciona definiciones de metaprogramación que son útiles para programar vectores cortos de forma genérica.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    typename _Scalar_type,
    int _Size
>
struct short_vector;
template<>
struct short_vector<unsigned int, 1>;
template<>
struct short_vector<unsigned int, 2>;
template<>
struct short_vector<unsigned int, 3>;
template<>
struct short_vector<unsigned int, 4>;
template<>
struct short_vector<int, 1>;
template<>
struct short_vector<int, 2>;
template<>
struct short_vector<int, 3>;
template<>
struct short_vector<int, 4>;
template<>
struct short_vector<float, 1>;
template<>
struct short_vector<float, 2>;
template<>
struct short_vector<float, 3>;
template<>
struct short_vector<float, 4>;
template<>
struct short_vector<unorm, 1>;
template<>
struct short_vector<unorm, 2>;
template<>
struct short_vector<unorm, 3>;
template<>
struct short_vector<unorm, 4>;
template<>
struct short_vector<norm, 1>;
template<>
struct short_vector<norm, 2>;
template<>
struct short_vector<norm, 3>;
template<>
struct short_vector<norm, 4>;
template<>
struct short_vector<double, 1>;
template<>
struct short_vector<double, 2>;
template<>
struct short_vector<double, 3>;
template<>
struct short_vector<double, 4>;
```

### <a name="parameters"></a>Parámetros

*_Scalar_type*<br/>

*_Size*<br/>

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`type`||

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[short_vector::short_vector (Constructor)](#ctor)||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`short_vector`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_short_vectors.h

**Espacio de nombres:** Simultaneidad::gráficos

## <a name="short_vectorshort_vector-constructor"></a><a name="ctor"></a>Constructor short_vector::short_vector

```cpp
short_vector();
```

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (Espacio de nombres)](concurrency-graphics-namespace.md)
