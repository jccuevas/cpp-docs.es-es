---
title: texture (Clase)
ms.date: 11/04/2016
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: f7a38c84c5def629c7a42b2c05bf1ed04441593b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127782"
---
# <a name="texture-class"></a>texture (Clase)

Una textura es un agregado de datos en un `accelerator_view` en el dominio de extensión. Es una colección de variables, una para cada elemento de un dominio de extensión. Cada variable contiene un valor correspondiente al C++ tipo primitivo (`unsigned int`, `int`, `float`, `double`), un tipo escalar (`norm`o `unorm`) o un tipo de vector corto.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename value_type,  int _Rank>
class texture;
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
|`scalar_type`|Tipos escalares.|
|`value_type`|Tipos de valor.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de textura](#ctor)|Inicializa una nueva instancia de la clase `texture`.|
|[~ Texture (destructor)](#ctor)|Destruye el objeto `texture`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[copy_to](#copy_to)|Copia el objeto de `texture` en el destino, realizando una copia en profundidad.|
|[data](#data)|Devuelve un puntero de CPU a los datos sin procesar de esta textura.|
|[get](#get)|Devuelve el valor del elemento en el índice especificado.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Devuelve el [accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.|
|[get_depth_pitch](#get_depth_pitch)|Devuelve el número de bytes entre cada segmento de profundidad en una textura de ensayo 3D en la CPU.|
|[get_row_pitch](#get_row_pitch)|Devuelve el número de bytes entre cada fila de una textura de ensayo 2D o 3D en la CPU.|
|[set](#set)|Establece el valor del elemento en el índice especificado.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator()](#operator_call)|Devuelve el valor del elemento especificado por los parámetros.|
|[operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator=](#operator_eq)|Copia el objeto de [textura](texture-class.md) especificado en este.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank)|Obtiene el rango del objeto `texture`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.|
|[depth_pitch](#depth_pitch)|Obtiene el número de bytes entre cada segmento de profundidad en una textura de ensayo 3D en la CPU.|
|[row_pitch](#row_pitch)|Obtiene el número de bytes entre cada fila de una textura de ensayo 2D o 3D en la CPU.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Texture_base`

`texture`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics. h

**Espacio de nombres:** Concurrency:: Graphics

## <a name="dtor"></a>~ Texture

Destruye el objeto `texture`.

```cpp
~texture() restrict(cpu);
```

## <a name="associated_accelerator_view"></a>associated_accelerator_view

Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

Copia el objeto de `texture` en el destino, realizando una copia en profundidad.

```cpp
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parámetros

*_Dest*<br/>
El objeto en el que se copia.

*_Rank*<br/>
Rango de la textura.

*value_type*<br/>
Tipo de los elementos de la textura.

## <a name="data"></a>Data

Devuelve un puntero de CPU a los datos sin procesar de esta textura.

```cpp
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

Puntero a los datos sin formato de la textura.

## <a name="depth_pitch"></a>depth_pitch

Obtiene el número de bytes entre cada segmento de profundidad en una textura de ensayo 3D en la CPU.

```cpp
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

## <a name="get"></a>Obtener

Devuelve el valor del elemento en el índice especificado.

```cpp
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento.

### <a name="return-value"></a>Valor devuelto

Valor del elemento en el índice especificado.

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Devuelve el accelerator_view que es el destino preferido para que esta textura se copie.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

[Accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.

## <a name="get_depth_pitch"></a>get_depth_pitch

Devuelve el número de bytes entre cada segmento de profundidad en una textura de ensayo 3D en la CPU.

```cpp
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

El número de bytes entre cada segmento de profundidad en una textura de ensayo 3D en la CPU.

## <a name="get_row_pitch"></a>get_row_pitch

Devuelve el número de bytes entre cada fila de una textura de ensayo de 2 dimensiones o entre cada fila de un segmento de profundidad en una textura de ensayo de 3 dimensiones.

```cpp
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

El número de bytes entre cada fila de una textura de ensayo de 2 dimensiones o entre cada fila de un segmento de profundidad en una textura de ensayo de 3 dimensiones.

## <a name="operator_call"></a>operador ()

Devuelve el valor del elemento especificado por los parámetros.

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice.

*_I0*<br/>
Componente más significativo del índice.

*_I1*<br/>
El siguiente componente más significativo del índice.

*_I2*<br/>
El componente menos significativo del índice.

*_Rank*<br/>
Rango del índice.

### <a name="return-value"></a>Valor devuelto

Valor del elemento especificado por los parámetros.

## <a name="operator_at"></a>operador []

Devuelve el elemento que se encuentra en el índice especificado.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice.

*_I0*<br/>
El índice.

### <a name="return-value"></a>Valor devuelto

Elemento que se encuentra en el índice especificado.

## <a name="operator_eq"></a>operador =

Copia el objeto de [textura](texture-class.md) especificado en este.

```cpp
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto de `texture` del que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `texture`.

## <a name="rank"></a>criterios

Obtiene el rango del objeto `texture`.

```cpp
static const int rank = _Rank;
```

## <a name="row_pitch"></a>row_pitch

Obtiene el número de bytes entre cada fila de una textura de ensayo 2D o 3D en la CPU.

```cpp
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

## <a name="set"></a>conjunto

Establece el valor del elemento en el índice especificado.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento.

*_Rank*<br/>
Rango del índice.

*value*<br/>
Nuevo valor del elemento.

## <a name="ctor"></a>degrada

Inicializa una nueva instancia de la clase `texture`.

```cpp
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

texture(int _E0) restrict(cpu);

texture(int _E0, int _E1) restrict(cpu);

texture(int _E0, int _E1, int _E2) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const texture& _Src,
    const Concurrency::accelerator_view& _Acc_view);

texture(
    texture&& _Other);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av);

texture(
    const texture& _Src);
```

### <a name="parameters"></a>Parámetros

*_Acc_view*<br/>
[Accelerator_view](accelerator-view-class.md) que especifica la ubicación de la textura.

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md) que especifica la ubicación de la textura.

*_Associated_av*<br/>
Accelerator_view que especifica el destino preferido para las copias a o desde esta textura.

*_Bits_per_scalar_element*<br/>
Número de bits por cada elemento escalar en el tipo escalar subyacente de la textura. En general, el valor admitido es 8, 16, 32 y 64. Si se especifica 0, el número de bits es el mismo que el scalar_type subyacente. 64 solo es válido para las texturas basadas en dos.

*_Ext*<br/>
La extensión de cada dimensión de la textura.

*_E0*<br/>
El componente más significativo de la textura.

*_E1*<br/>
El siguiente componente más significativo de la textura.

*_E2*<br/>
El componente menos significativo de la extensión de la textura.

*_Input_iterator*<br/>
El tipo de iterador de entrada.

*_Mipmap_levels*<br/>
El número de niveles de mipmap en la textura subyacente. Si se especifica 0, la textura tendrá el intervalo completo de niveles de mipmap hasta el tamaño más pequeño posible para la extensión especificada.

*_Rank*<br/>
Rango de la extensión.

*_Source*<br/>
Un puntero a un búfer del host.

*_Src*<br/>
A la textura para copiar.

*_Src_byte_size*<br/>
Número de bytes del búfer de origen.

*_Src_first*<br/>
Un iterador inicial en el contenedor de origen.

*_Src_last*<br/>
Un iterador final en el contenedor de origen.

*_Other*<br/>
Otro origen de datos.

*_Rank*<br/>
Rango de la sección.

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
