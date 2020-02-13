---
title: writeonly_texture_view (Clase)
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 8978a548ed246c59d7e7f007f1180685c7343a14
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126245"
---
# <a name="writeonly_texture_view-class"></a>writeonly_texture_view (Clase)

Proporciona un acceso de WriteOnly a una textura.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view;

template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
Tipo de los elementos de la textura.

*_Rank*<br/>
Rango de la textura.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`scalar_type`||
|`value_type`|Tipo de los elementos de la textura.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de writeonly_texture_view](#ctor)|Inicializa una nueva instancia de la clase `writeonly_texture_view`.|
|[~ writeonly_texture_view destructor](#ctor)|Destruye el objeto `writeonly_texture_view`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[set](#set)|Establece el valor del elemento en el índice especificado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Copia el objeto de `writeonly_texture_view` especificado en este.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank)|Obtiene el rango del objeto `writeonly_texture_view`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics. h

**Espacio de nombres:** Concurrency:: Graphics

## <a name="dtor"></a>~ writeonly_texture_view

Destruye el objeto `writeonly_texture_view`.

```cpp
~writeonly_texture_view() restrict(amp,cpu);
```

## <a name="operator_eq"></a>operador =

Copia el objeto de `writeonly_texture_view` especificado en este.

```cpp
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
`writeonly_texture_view` objeto desde el que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `writeonly_texture_view`.

## <a name="rank"></a>criterios

Obtiene el rango del objeto `writeonly_texture_view`.

```cpp
static const int rank = _Rank;
```

## <a name="set"></a>conjunto

Establece el valor del elemento en el índice especificado.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento.

*value*<br/>
Nuevo valor del elemento.

## <a name="ctor"></a>writeonly_texture_view

Inicializa una nueva instancia de la clase `writeonly_texture_view`.

```cpp
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
Rango de la textura.

*value_type*<br/>
Tipo de los elementos de la textura.

*_Src*<br/>
Textura que se usa para crear el `writeonly_texture_view`.

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
