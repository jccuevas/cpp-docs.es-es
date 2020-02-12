---
title: array (Clase)
ms.date: 11/04/2016
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: efea8dabb69a48e69d68a86110fdf9bc7664948b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127117"
---
# <a name="array-class"></a>array (Clase)

Representa un contenedor de datos que se usa para trasladar datos a un acelerador.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
Tipo de elemento de los datos.

*_Rank*<br/>
El rango de la matriz.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de matriz](#ctor)|Inicializa una nueva instancia de la clase `array`.|
|[~ array (destructor)](#dtor)|Destruye el objeto `array`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[copy_to](#copy_to)|Copia el contenido de la matriz en otra matriz.|
|[data](#data)|Devuelve un puntero a los datos sin formato de la matriz.|
|[get_accelerator_view](#get_accelerator_view)|Devuelve el objeto [accelerator_view](accelerator-view-class.md) que representa la ubicación a la que se asigna la matriz. Solo se puede tener acceso a esta propiedad en la CPU.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Obtiene el segundo objeto [accelerator_view](accelerator-view-class.md) que se pasa como parámetro cuando se llama a un constructor de ensayo para crear una instancia del objeto `array`.|
|[get_cpu_access_type](#get_cpu_access_type)|Devuelve el [access_type](concurrency-namespace-enums-amp.md#access_type) de la matriz. Solo se puede tener acceso a este método en la CPU.|
|[get_extent](#get_extent)|Devuelve el objeto de [extensión](extent-class.md) de la matriz.|
|[reinterpret_as](#reinterpret_as)|Devuelve una matriz unidimensional que contiene todos los elementos del objeto `array`.|
|[section](#section)|Devuelve una subsección del objeto `array` que está en el origen especificado y, opcionalmente, tiene la extensión especificada.|
|[view_as](#view_as)|Devuelve un objeto [array_view](array-view-class.md) que se construye a partir del objeto `array`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operador STD:: Vector&lt;value_type&gt;](#operator_vec)|Utiliza `copy(*this, vector)` para convertir implícitamente la matriz en un objeto STD::[Vector](../../../standard-library/vector-class.md) .|
|[operator()](#operator_call)|Devuelve el valor del elemento especificado por los parámetros.|
|[operator\[\]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator=](#operator_eq)|Copia el contenido del objeto `array` especificado en este.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank)|Almacena el rango de la matriz.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Obtiene el objeto [accelerator_view](accelerator-view-class.md) que representa la ubicación a la que se asigna la matriz. Solo se puede tener acceso a esta propiedad en la CPU.|
|[associated_accelerator_view](#associated_accelerator_view)|Obtiene el segundo objeto [accelerator_view](accelerator-view-class.md) que se pasa como parámetro cuando se llama a un constructor de ensayo para crear una instancia del objeto `array`.|
|[cpu_access_type](#cpu_access_type)|Obtiene el [access_type](concurrency-namespace-enums-amp.md#access_type) que representa el modo en que la CPU puede tener acceso al almacenamiento de la matriz.|
|[extent](#extent)|Obtiene la extensión que define la forma de la matriz.|

## <a name="remarks"></a>Observaciones

El tipo `array<T,N>` representa una matriz de *N*dimensiones densa y normal (no escalonada) que se encuentra en una ubicación concreta, como un acelerador o la CPU. El tipo de datos de los elementos de la matriz es `T`, que debe ser de un tipo que sea compatible con el acelerador de destino. Aunque el rango, `N`(de la matriz se determina estáticamente y forma parte del tipo, el tiempo de ejecución determina la extensión de la matriz y se expresa mediante la `extent<N>`de clase.

Una matriz puede tener cualquier número de dimensiones, aunque algunas funciones se especializan en `array` objetos con rango uno, dos y tres. Si omite el argumento de dimensión, el valor predeterminado es 1.

Los datos de la matriz se colocan de forma contigua en la memoria. Los elementos que difieren en uno en la dimensión menos significativa son adyacentes en memoria.

Las matrices se consideran lógicamente tipos de valor, porque cuando una matriz se copia en otra matriz, se realiza una copia en profundidad. Dos matrices nunca apuntan a los mismos datos.

El tipo de `array<T,N>` se usa en varios escenarios:

- Como contenedor de datos que se puede usar en los cálculos de un acelerador.

- Como contenedor de datos para almacenar la memoria en la CPU del host (que se puede usar para copiar en otras matrices y desde otras).

- Como un objeto de almacenamiento provisional que actúa como un intermediario rápido en copias de host a dispositivo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`array`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="dtor"></a>~ array

Destruye el objeto `array`.

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a>accelerator_view

Obtiene el objeto [accelerator_view](accelerator-view-class.md) que representa la ubicación a la que se asigna la matriz. Solo se puede tener acceso a esta propiedad en la CPU.

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="ctor"></a>matriz

Inicializa una nueva instancia de la [clase de matriz](array-class.md). No hay ningún constructor predeterminado para `array<T,N>`. Todos los constructores solo se ejecutan en la CPU. No se pueden ejecutar en un destino de Direct3D.

```cpp
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

explicit array(
    int _E0) restrict(cpu);

explicit array(
    int _E0,
    int _E1) restrict(cpu);

explicit array(
    int _E0,
    int _E1,
    int _E2) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av,
    accelerator_view _Associated_Av) restrict(cpu);

array(const array& _Other) restrict(cpu);

array(array&& _Other) restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Associated_Av*<br/>
Accelerator_view que especifica la ubicación de destino preferida de la matriz.

*_Av*<br/>
Objeto [accelerator_view](accelerator-view-class.md) que especifica la ubicación de la matriz.

*_Cpu_access_type*<br/>
[Access_type](concurrency-namespace-enums-amp.md#access_type) deseada para la matriz de la CPU. Este parámetro tiene un valor predeterminado de `access_type_auto` que se sale de la CPU `access_type` la determinación en el tiempo de ejecución. El `access_type` de CPU real de la matriz se puede consultar mediante el método `get_cpu_access_type`.

*_Extent*<br/>
La extensión de cada dimensión de la matriz.

*_E0*<br/>
El componente más significativo de la extensión de esta sección.

*_E1*<br/>
El siguiente componente más significativo de la extensión de esta sección.

*_E2*<br/>
El componente menos significativo de la extensión de esta sección.

*_InputIterator*<br/>
El tipo de iterador de entrada.

*_Src*<br/>
Objeto que se va a copiar.

*_Src_first*<br/>
Un iterador inicial en el contenedor de origen.

*_Src_last*<br/>
Un iterador final en el contenedor de origen.

*_Other*<br/>
Otro origen de datos.

*_Rank*<br/>
Rango de la sección.

*value_type*<br/>
El tipo de datos de los elementos que se copian.

## <a name="associated_accelerator_view"></a>associated_accelerator_view

Obtiene el segundo objeto [accelerator_view](accelerator-view-class.md) que se pasa como parámetro cuando se llama a un constructor de ensayo para crear una instancia del objeto `array`.

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

Copia el contenido del `array` en otro `array`.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>Parámetros

*_Dest*<br/>
Objeto de [array_view](array-view-class.md) en el que se va a copiar.

## <a name="cpu_access_type"></a>cpu_access_type

Obtiene el access_type de CPU permitido para esta matriz.

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a>Data

Devuelve un puntero a los datos sin procesar del `array`.

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valor devuelto

Puntero a los datos sin formato de la matriz.

## <a name="extent"></a>expresa

Obtiene el objeto de [extensión](extent-class.md) que define la forma de la `array`.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a>get_accelerator_view

Devuelve el objeto [accelerator_view](accelerator-view-class.md) que representa la ubicación a la que se asigna el objeto `array`. Solo se puede tener acceso a esta propiedad en la CPU.

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `accelerator_view` que representa la ubicación a la que se asigna el objeto `array`.

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

Obtiene el segundo objeto [accelerator_view](accelerator-view-class.md) que se pasa como parámetro cuando se llama a un constructor de ensayo para crear una instancia del objeto `array`.

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>Valor devuelto

Segundo objeto [accelerator_view](accelerator-view-class.md) pasado al constructor de ensayo.

## <a name="get_cpu_access_type"></a>get_cpu_access_type

Devuelve el access_type de CPU permitido para esta matriz.

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

## <a name="get_extent"></a>get_extent

Devuelve el objeto de [extensión](extent-class.md) de la `array`.

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

El objeto `extent` de `array`.

## <a name="operator_vec"></a>operador STD:: Vector&lt;value_type&gt;

Utiliza `copy(*this, vector)` para convertir implícitamente la matriz en un objeto STD:: Vector.

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
Tipo de datos de los elementos del vector.

### <a name="return-value"></a>Valor devuelto

Un objeto de tipo `vector<T>` que contiene una copia de los datos contenidos en la matriz.

## <a name="operator_call"></a>operador ()

Devuelve el valor del elemento especificado por los parámetros.

```cpp
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);

value_type& operator() (int _I0, int _I1) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;

value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Ubicación del elemento.

*_I0*<br/>
Componente más significativo del origen de esta sección.

*_I1*<br/>
El siguiente componente más significativo del origen de esta sección.

*_I2*<br/>
El componente menos significativo del origen de esta sección.

*_I*<br/>
Ubicación del elemento.

### <a name="return-value"></a>Valor devuelto

Valor del elemento especificado por los parámetros.

## <a name="operator_at"></a>operador []

Devuelve el elemento que se encuentra en el índice especificado.

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice.

*_I*<br/>
El índice.

### <a name="return-value"></a>Valor devuelto

Elemento que se encuentra en el índice especificado.

## <a name="operator_eq"></a>operador =

Copia el contenido del objeto `array` especificado.

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto de `array` del que se va a copiar.

*_Src*<br/>
Objeto de `array` del que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `array`.

## <a name="rank"></a>criterios

Almacena el rango del `array`.

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a>reinterpret_as

Reinterpreta la matriz a través de una array_view unidimensional, que opcionalmente puede tener un tipo de valor distinto de la matriz de origen.

### <a name="syntax"></a>Sintaxis

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Value_type2*<br/>
El tipo de datos de los datos devueltos.

### <a name="return-value"></a>Valor devuelto

Un objeto array_view o const array_view basado en la matriz, con el tipo de elemento reinterpretado de T a ElementType y el rango reducido de N a 1.

### <a name="remarks"></a>Observaciones

A veces es conveniente ver una matriz multidimensional como si se tratase de una matriz lineal y unidimensional, posiblemente con un tipo de valor distinto de la matriz de origen. Puede utilizar este método para lograrlo.
**PRECAUCIÓN** Reinterpretar un objeto de matriz mediante un tipo de valor diferente es una operación potencialmente insegura. Se recomienda usar esta funcionalidad con cuidado.

En el código siguiente se muestra un ejemplo.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>transversal

Devuelve una subsección del objeto `array` que está en el origen especificado y, opcionalmente, tiene la extensión especificada.

```cpp
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);

array_view<value_type,1> section(
    int _I0,
    int _E0) restrict(amp,cpu);

array_view<const value_type,1> section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view<value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) restrict(amp,cpu);

array_view<const value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view<value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) restrict(amp,cpu);

array_view<const value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_E0*<br/>
El componente más significativo de la extensión de esta sección.

*_E1*<br/>
El siguiente componente más significativo de la extensión de esta sección.

*_E2*<br/>
El componente menos significativo de la extensión de esta sección.

*_Ext*<br/>
Objeto de [extensión](extent-class.md) que especifica la extensión de la sección. El origen es 0.

*_Idx*<br/>
Objeto de [Índice](index-class.md) que especifica la ubicación del origen. La subsección es el resto de la extensión.

*_I0*<br/>
Componente más significativo del origen de esta sección.

*_I1*<br/>
El siguiente componente más significativo del origen de esta sección.

*_I2*<br/>
El componente menos significativo del origen de esta sección.

*_Rank*<br/>
Rango de la sección.

*_Section_extent*<br/>
Objeto de [extensión](extent-class.md) que especifica la extensión de la sección.

*_Section_origin*<br/>
Objeto de [Índice](index-class.md) que especifica la ubicación del origen.

*value_type*<br/>
El tipo de datos de los elementos que se copian.

### <a name="return-value"></a>Valor devuelto

Devuelve una subsección del objeto `array` que está en el origen especificado y, opcionalmente, tiene la extensión especificada. Cuando solo se especifica el objeto `index`, la subsección contiene todos los elementos de la cuadrícula asociada que tienen índices mayores que los índices de los elementos del objeto `index`.

## <a name="view_as"></a>view_as

Reinterpreta esta matriz como una [array_view](array-view-class.md) de un rango diferente.

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_New_rank*<br/>
Rango del objeto de `extent` que se pasa como parámetro.

*_View_extent*<br/>
La extensión que se usa para construir el nuevo objeto [array_view](array-view-class.md) .

*value_type*<br/>
El tipo de datos de los elementos en el objeto de `array` original y en el objeto de `array_view` devuelto.

### <a name="return-value"></a>Valor devuelto

Objeto [array_view](array-view-class.md) que se construye.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
