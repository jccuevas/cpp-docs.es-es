---
title: double_2 (Clase)
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::double_2::set_x
- amp_short_vectors/Concurrency::graphics::double_2::operator+=
- amp_short_vectors/Concurrency::graphics::double_2::operator=
- amp_short_vectors/Concurrency::graphics::double_2::operator/=
- amp_short_vectors/Concurrency::graphics::double_2::operator*=
- amp_short_vectors/Concurrency::graphics::double_2::yx
- amp_short_vectors/Concurrency::graphics::double_2::y
- amp_short_vectors/Concurrency::graphics::double_2::xy
- amp_short_vectors/Concurrency::graphics::double_2::set_xy
- amp_short_vectors/Concurrency::graphics::double_2::get_yx
- amp_short_vectors/Concurrency::graphics::double_2::set_yx
- amp_short_vectors/Concurrency::graphics::double_2::get_xy
- amp_short_vectors/Concurrency::graphics::double_2::operator++
- amp_short_vectors/Concurrency::graphics::double_2::get_x
- amp_short_vectors/Concurrency::graphics::double_2::operator-=
- amp_short_vectors/Concurrency::graphics::double_2::rg
- amp_short_vectors/Concurrency::graphics::double_2::gr
- amp_short_vectors/Concurrency::graphics::double_2::get_y
- amp_short_vectors/Concurrency::graphics::double_2::x
- amp_short_vectors/Concurrency::graphics::double_2::r
- amp_short_vectors/Concurrency::graphics::double_2::operator--
- amp_short_vectors/Concurrency::graphics::double_2
- amp_short_vectors/Concurrency::graphics::double_2::operator-
- amp_short_vectors/Concurrency::graphics::double_2::g
- amp_short_vectors/Concurrency::graphics::double_2::set_y
ms.assetid: c19c2d21-3cbf-4ce5-b460-3b8253688f82
ms.openlocfilehash: 73656415d1b8774fe8304d674872524e76ee301d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126713"
---
# <a name="double_2-class"></a>double_2 (Clase)

Representa un vector corto de 2 dobles.

## <a name="syntax"></a>Sintaxis

```cpp
class double_2;
```

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de double_2](#ctor)|Sobrecargado. El constructor predeterminado, inicializa todos los elementos con 0.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|double_2::get_x||
|double_2::get_xy||
|double_2::get_y||
|double_2::get_yx||
|double_2::ref_g||
|double_2::ref_r||
|double_2::ref_x||
|double_2::ref_y||
|double_2::set_x||
|double_2::set_xy||
|double_2::set_y||
|double_2::set_yx||

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|double_2::operator-||
|double_2::operator--||
|double_2::operator*=||
|double_2::operator/=||
|double_2::operator++||
|double_2::operator+=||
|double_2::operator=||
|double_2::operator-=||

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|double_2::size (Constante)||

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|double_2::g||
|double_2::gr||
|double_2::r||
|double_2::rg||
|double_2::x||
|double_2::xy||
|double_2::y||
|double_2::yx||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`double_2`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_short_vectors. h

**Espacio de nombres:** Concurrency:: Graphics

## <a name="ctor"></a>double_2

El constructor predeterminado, inicializa todos los elementos con 0.

```cpp
double_2() restrict(amp,
    cpu);

double_2(
    double _V0,
    double _V1) restrict(amp,
    cpu);

double_2(
    double _V) restrict(amp,
    cpu);

double_2(
    const double_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const norm_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parámetros

*_V0*<br/>
Valor para inicializar el elemento 0.

*_V1*<br/>
Valor para inicializar el elemento 1.

*_V*<br/>
Valor de inicialización.

*_Other*<br/>
Objeto usado para inicializar.

## <a name="double_2__size"></a>ajusta

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
