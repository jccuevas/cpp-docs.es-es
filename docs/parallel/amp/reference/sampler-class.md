---
title: sampler (Clase)
ms.date: 06/28/2018
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 1a66e4d025a7592b78839dbe5f25f9103da41224
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352598"
---
# <a name="sampler-class"></a>sampler (Clase)

La clase de muestra agrega información de configuración de muestreo que se usará para el muestreo de textura.

## <a name="syntax"></a>Sintaxis

```cpp
class sampler;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[muestra de Constructor](#ctor)|Sobrecargado. Construye una instancia de muestra.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|Devuelve el `address_mode` que está asociada con el objeto de muestra.|
|[get_border_color](#get_border_color)|Devuelve el color del borde que está asociado con el objeto de muestra.|
|[get_filter_mode](#get_filter_mode)|Devuelve el `filter_mode` que está asociada con el objeto de muestra.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Sobrecargado. Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[address_mode](#address_mode)|Obtiene el modo de direccionamiento de la `sampler` objeto.|
|[border_color](#border_color)|Obtiene el color del borde de la `sampler` objeto.|
|[filter_mode](#filter_mode)|Obtiene el modo de filtro de la `sampler` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`sampler`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics.h

**Namespace:** Concurrency:: Graphics

##  <a name="ctor"></a> muestra

Construye una instancia de la [Sampler (clase)](sampler-class.md).

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parámetros

*_Filter_mode*<br/>
El modo de filtro que se usará en el muestreo.

*_Address_mode*<br/>
El modo de direccionamiento que se usará en el muestreo para todas las dimensiones.

*_Border_color*<br/>
El color del borde que se utilizará si el modo de direccionamiento es address_border. El valor predeterminado es `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.

*_Other*<br/>
[5] Constructor de copia la `sampler` objeto que se va a copiar en el nuevo `sampler` instancia.

[6] Constructor de movimiento el `sampler` mover en el nuevo objeto `sampler` instancia.

##  <a name="address_mode"></a> address_mode

Obtiene el modo de direccionamiento de la `sampler` objeto.

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

##  <a name="border_color"></a> border_color

Obtiene el color del borde de la `sampler` objeto.

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

##  <a name="filter_mode"></a> filter_mode

Obtiene el modo de filtro de la `sampler` objeto.

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

##  <a name="get_address_mode"></a> get_address_mode

Devuelve el modo de filtro que está configurado para este `sampler`.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>Valor devuelto

El modo de direccionamiento que se configura para el muestrario.

##  <a name="get_border_color"></a> get_border_color

Devuelve el color del borde que se configura para este `sampler`.

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valor devuelto

Un valor float_4 que contiene el color del borde.

##  <a name="get_filter_mode"></a> get_filter_mode

Devuelve el modo de filtro que está configurado para este `sampler`.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valor devuelto

El modo de filtro que está configurado para el muestrario.

##  <a name="operator_eq"></a> operator=

Asigna el valor de otro objeto de muestra para una muestra existente.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
[1] operador de asignación el `sampler` objeto que se va a copiar en este `sampler`.

[2] operador de asignación de movimiento del `sampler` mover este objeto `sampler`.

### <a name="return-value"></a>Valor devuelto

Una referencia a esta instancia de muestra.

## <a name="see-also"></a>Vea también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
