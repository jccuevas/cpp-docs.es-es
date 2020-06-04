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
ms.openlocfilehash: 8f47bf6e9b88dba1e94e9e2ed2b93c8d2d3f9b8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126361"
---
# <a name="sampler-class"></a>sampler (Clase)

La clase muestreador agrega información de configuración de muestreo que se usará para el muestreo de textura.

## <a name="syntax"></a>Sintaxis

```cpp
class sampler;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de muestra](#ctor)|Sobrecargado. Construye una instancia de muestra.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|Devuelve el `address_mode` asociado al objeto de muestra.|
|[get_border_color](#get_border_color)|Devuelve el color del borde asociado al objeto de muestra.|
|[get_filter_mode](#get_filter_mode)|Devuelve el `filter_mode` asociado al objeto de muestra.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Sobrecargado. Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[address_mode](#address_mode)|Obtiene el modo de dirección del objeto `sampler`.|
|[border_color](#border_color)|Obtiene el color del borde del objeto `sampler`.|
|[filter_mode](#filter_mode)|Obtiene el modo de filtro del objeto `sampler`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`sampler`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics. h

**Espacio de nombres:** Concurrency:: Graphics

## <a name="ctor"></a>muestras

Construye una instancia de la [clase de muestra](sampler-class.md).

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
Modo de filtro que se va a utilizar en el muestreo.

*_Address_mode*<br/>
Modo de direccionamiento que se va a usar en el muestreo para todas las dimensiones.

*_Border_color*<br/>
Color de borde que se va a utilizar si el modo de dirección es address_border. El valor predeterminado es `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.

*_Other*<br/>
[5] constructor de copias el objeto `sampler` que se va a copiar en la nueva instancia de `sampler`.

[6] constructor de movimiento el objeto de `sampler` que se va a desplace en la nueva instancia de `sampler`.

## <a name="address_mode"></a>address_mode

Obtiene el modo de dirección del objeto `sampler`.

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

## <a name="border_color"></a>border_color

Obtiene el color del borde del objeto `sampler`.

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

## <a name="filter_mode"></a>filter_mode

Obtiene el modo de filtro del objeto `sampler`.

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

## <a name="get_address_mode"></a>get_address_mode

Devuelve el modo de filtro que se configura para este `sampler`.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>Valor devuelto

Modo de dirección que se configura para la muestra.

## <a name="get_border_color"></a>get_border_color

Devuelve el color del borde que se configura para este `sampler`.

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valor devuelto

Float_4 que contiene el color del borde.

## <a name="get_filter_mode"></a>get_filter_mode

Devuelve el modo de filtro que se configura para este `sampler`.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valor devuelto

El modo de filtro que se configura para la muestra.

## <a name="operator_eq"></a>operador =

Asigna el valor de otro objeto de muestra a una muestra existente.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
[1] operador de asignación de copia el objeto `sampler` que se va a copiar en esta `sampler`.

[2] operador de asignación de movimiento el objeto `sampler` que se va a pasar a este `sampler`.

### <a name="return-value"></a>Valor devuelto

Referencia a esta instancia de muestra.

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
