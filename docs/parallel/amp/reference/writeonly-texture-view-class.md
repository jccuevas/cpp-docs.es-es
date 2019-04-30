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
ms.openlocfilehash: 5244ae5df99b06c77f4eb27317e5829b21fabf24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405422"
---
# <a name="writeonlytextureview-class"></a>writeonly_texture_view (Clase)

Proporciona acceso de solo escritura a una textura.

## <a name="syntax"></a>Sintaxis

```
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

#### <a name="parameters"></a>Parámetros

*value_type*<br/>
El tipo de los elementos de la textura.

*_Rank*<br/>
El rango de la textura.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`scalar_type`||
|`value_type`|El tipo de los elementos de la textura.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[writeonly_texture_view (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `writeonly_texture_view`.|
|[~ writeonly_texture_view (destructor)](#ctor)|Destruye el objeto `writeonly_texture_view`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[set](#set)|Establece el valor del elemento en el índice especificado.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Copia especificado `writeonly_texture_view` objeto a ésta.|

### <a name="public-constants"></a>Constantes públicas

|Name|Descripción|
|----------|-----------------|
|[rank Constant](#rank)|Obtiene el rango de la `writeonly_texture_view` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics.h

**Espacio de nombres**: Concurrency:: Graphics

##  <a name="dtor"></a> ~writeonly_texture_view

Destruye el objeto `writeonly_texture_view`.

```
~writeonly_texture_view() restrict(amp,cpu);
```

##  <a name="operator_eq"></a> operator=

Copia especificado `writeonly_texture_view` objeto a ésta.

```
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
`writeonly_texture_view` objeto que se va a copiar desde.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `writeonly_texture_view` objeto.

##  <a name="rank"></a> rango

Obtiene el rango de la `writeonly_texture_view` objeto.

```
static const int rank = _Rank;
```

##  <a name="set"></a> Conjunto

Establece el valor del elemento en el índice especificado.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice del elemento.

*value*<br/>
Nuevo valor del elemento.

##  <a name="ctor"></a> writeonly_texture_view

Inicializa una nueva instancia de la clase `writeonly_texture_view`.

```
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Rank*<br/>
El rango de la textura.

*value_type*<br/>
El tipo de los elementos de la textura.

*_Src*<br/>
La textura que se usa para crear el `writeonly_texture_view`.

## <a name="see-also"></a>Vea también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
