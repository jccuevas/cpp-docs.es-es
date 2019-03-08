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
ms.openlocfilehash: cfcb65fa23fe4593e7dcf11da3b5da4b1785ce71
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279749"
---
# <a name="texture-class"></a>texture (Clase)

Una textura es un agregado de datos en un `accelerator_view` en el dominio de la extensión. Es una colección de variables, uno para cada elemento en un dominio de la extensión. Cada variable contiene un valor que corresponde al tipo primitivo de C++ ( `unsigned int`, `int`, `float`, `double`), un tipo escalar ( `norm`, o `unorm`), o un tipo de vector corto.

## <a name="syntax"></a>Sintaxis

```
template <typename value_type,  int _Rank>
class texture;
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
|`scalar_type`|Tipos escalares.|
|`value_type`|Tipos de valor.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Constructor de textura](#ctor)|Inicializa una nueva instancia de la clase `texture`.|
|[~ texture (destructor)](#ctor)|Destruye el objeto `texture`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[copy_to](#copy_to)|Copia la `texture` objeto en el destino, haciendo una copia en profundidad.|
|[data](#data)|Devuelve un puntero de CPU a los datos sin procesar de esta textura.|
|[get](#get)|Devuelve el valor del elemento en el índice especificado.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Devuelve el [accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.|
|[get_depth_pitch](#get_depth_pitch)|Devuelve el número de bytes entre cada segmento de profundidad en una textura de la CPU de ensayo de 3D.|
|[get_row_pitch](#get_row_pitch)|Devuelve el número de bytes entre cada fila de una 2D o 3D textura en la CPU de ensayo.|
|[set](#set)|Establece el valor del elemento en el índice especificado.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator()](#operator_call)|Devuelve el valor del elemento especificado por los parámetros.|
|[operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator=](#operator_eq)|Copia especificado [textura](texture-class.md) objeto a ésta.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[rank Constant](#rank)|Obtiene el rango de la `texture` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.|
|[depth_pitch](#depth_pitch)|Obtiene el número de bytes entre cada segmento de profundidad en una textura de ensayo de 3D en la CPU.|
|[row_pitch](#row_pitch)|Obtiene el número de bytes entre cada fila de una 2D o 3D la textura en la CPU de ensayo.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Texture_base`

`texture`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics.h

**Espacio de nombres**: Concurrency:: Graphics

##  <a name="dtor"></a> ~texture

Destruye el objeto `texture`.

```
~texture() restrict(cpu);
```

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

Obtiene el [accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

Copia la `texture` objeto en el destino, haciendo una copia en profundidad.

```
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parámetros

*_Dest*<br/>
Para copiar en el objeto.

*_Rank*<br/>
El rango de la textura.

*value_type*<br/>
El tipo de los elementos de la textura.

##  <a name="data"></a> Datos

Devuelve un puntero de CPU a los datos sin procesar de esta textura.

```
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

Un puntero a los datos sin procesar de la textura.

##  <a name="depth_pitch"></a> depth_pitch

Obtiene el número de bytes entre cada segmento de profundidad en una textura de ensayo de 3D en la CPU.

```
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

##  <a name="get"></a> Obtener

Devuelve el valor del elemento en el índice especificado.

```
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice del elemento.

### <a name="return-value"></a>Valor devuelto

Valor del elemento en el índice especificado.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

Devuelve el accelerator_view que es el destino preferido para que esta textura se copie.

```
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

El [accelerator_view](accelerator-view-class.md) que es el destino preferido para que esta textura se copie.

##  <a name="get_depth_pitch"></a> get_depth_pitch

Devuelve el número de bytes entre cada segmento de profundidad en una textura de la CPU de ensayo de 3D.

```
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

El número de bytes entre cada segmento de profundidad en una textura de la CPU de ensayo de 3D.

##  <a name="get_row_pitch"></a> get_row_pitch

Devuelve el número de bytes entre cada fila de una textura de ensayo de 2 dimensiones o entre cada fila de un segmento de profundidad de textura de ensayo de 3 dimensiones.

```
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

El número de bytes entre cada fila de una textura de ensayo de 2 dimensiones o entre cada fila de un segmento de profundidad de textura de ensayo de 3 dimensiones.

##  <a name="operator_call"></a> operator()

Devuelve el valor del elemento especificado por los parámetros.

```
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
Índice.

*_I0*<br/>
El componente más significativo del índice.

*_I1*<br/>
El siguiente-a-componente más significativo del índice.

*_I2*<br/>
El componente menos significativo del índice.

*_Rank*<br/>
El rango del índice.

### <a name="return-value"></a>Valor devuelto

El valor del elemento especificado por los parámetros.

##  <a name="operator_at"></a> operator[]

Devuelve el elemento que se encuentra en el índice especificado.

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice.

*_I0*<br/>
Índice.

### <a name="return-value"></a>Valor devuelto

El elemento que se encuentra en el índice especificado.

##  <a name="operator_eq"></a> operator=

Copia especificado [textura](texture-class.md) objeto a ésta.

```
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
La `texture` objeto que se va a copiar desde.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `texture` objeto.

##  <a name="rank"></a> rango

Obtiene el rango de la `texture` objeto.

```
static const int rank = _Rank;
```

##  <a name="row_pitch"></a> row_pitch

Obtiene el número de bytes entre cada fila de una 2D o 3D la textura en la CPU de ensayo.

```
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

##  <a name="set"></a> Conjunto

Establece el valor del elemento en el índice especificado.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice del elemento.

*_Rank*<br/>
El rango del índice.

*value*<br/>
Nuevo valor del elemento.

##  <a name="ctor"></a> Textura

Inicializa una nueva instancia de la clase `texture`.

```
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
El [accelerator_view](accelerator-view-class.md) que especifica la ubicación de la textura.

*_Av*<br/>
El [accelerator_view](accelerator-view-class.md) que especifica la ubicación de la textura.

*_Associated_av*<br/>
Una accelerator_view que especifica el destino preferido para copias a o desde esta textura.

*_Bits_per_scalar_element*<br/>
El número de bits por cada elemento escalar en el tipo escalar subyacente de la textura. En general, el valor admitido son 8, 16, 32 y 64. Si se especifica 0, el número de bits es el mismo que el scalar_type subyacente. 64 solo es válida para las texturas basadas en double.

*_Ext*<br/>
La extensión de cada dimensión de la textura.

*_E0*<br/>
El componente más significativo de la textura.

*_E1*<br/>
El siguiente-a-componente más significativo de la textura.

*_E2*<br/>
El componente menos significativo de la extensión de la textura.

*_Input_iterator*<br/>
El tipo del iterador de entrada.

*_Mipmap_levels*<br/>
El número de niveles de mipmap en la textura subyacente. Si se especifica 0, la textura tendrá la gama completa de los niveles de mipmap hasta el tamaño más pequeño posible para la extensión especificada.

*_Rank*<br/>
El rango de la extensión.

*_Source*<br/>
Un puntero a un búfer de host.

*_Src*<br/>
Para Texturizar la copia.

*_Src_byte_size*<br/>
El número de bytes del búfer de origen.

*_Src_first*<br/>
Un iterador inicial en el contenedor de origen.

*_Src_last*<br/>
Un iterador final en el contenedor de origen.

*_Other*<br/>
Otro origen de datos.

*_Rank*<br/>
El rango de la sección.

## <a name="see-also"></a>Vea también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
