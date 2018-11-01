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
ms.openlocfilehash: 5b123eb8d21c7273c41a713de5500df164511dce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537207"
---
# <a name="array-class"></a>array (Clase)

Representa un contenedor de datos que se usa para mover datos a un acelerador.

## <a name="syntax"></a>Sintaxis

```
template <typename value_type, int _Rank>
friend class array;
```

#### <a name="parameters"></a>Parámetros

*value_type*<br/>
El tipo de elemento de los datos.

*_Rank*<br/>
El rango de la matriz.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Constructor de matriz](#ctor)|Inicializa una nueva instancia de la clase `array`.|
|[~ array (destructor)](#dtor)|Destruye el objeto `array`.|
### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[copy_to](#copy_to)|Copia el contenido de la matriz en otra matriz.|
|[data](#data)|Devuelve un puntero a los datos sin procesar de la matriz.|
|[get_accelerator_view](#get_accelerator_view)|Devuelve el [accelerator_view](accelerator-view-class.md) objeto que representa la ubicación donde se asigna la matriz. Puede tener acceso a esta propiedad solo en la CPU.|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|Obtiene el segundo [accelerator_view](accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor provisional para crear una instancia de la `array` objeto.|
|[get_cpu_access_type](#get_cpu_access_type)|Devuelve el [access_type](concurrency-namespace-enums-amp.md#access_type) de la matriz. Puede tener acceso a este método solo en la CPU.|
|[get_extent](#get_extent)|Devuelve el [extensión](extent-class.md) objeto de la matriz.|
|[reinterpret_as](#reinterpret_as)|Devuelve una matriz unidimensional que contiene todos los elementos de la `array` objeto.|
|[section](#section)|Devuelve una subsección de la `array` objeto que está en el origen especificado y, opcionalmente, que tiene la extensión especificada.|
|[view_as](#view_as)|Devuelve un [array_view](array-view-class.md) objeto que se construye a partir del `array` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operador std:: vector&lt;value_type&gt;](#operator_vec)|Usa `copy(*this, vector)` para convertir implícitamente la matriz en un std::[vector](../../../standard-library/vector-class.md) objeto.|
|[operator()](#operator_call)|Devuelve el valor del elemento especificado por los parámetros.|
|[operator[]](#operator_at)|Devuelve el elemento que se encuentra en el índice especificado.|
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `array` objeto en este.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank)|Almacena el rango de la matriz.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|Obtiene el [accelerator_view](accelerator-view-class.md) objeto que representa la ubicación donde se asigna la matriz. Puede tener acceso a esta propiedad solo en la CPU.|
|[associated_accelerator_view](#associated_accelerator_view)|Obtiene el segundo [accelerator_view](accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor provisional para crear una instancia de la `array` objeto.|
|[cpu_access_type](#cpu_access_type)|Obtiene el [access_type](concurrency-namespace-enums-amp.md#access_type) que representa cómo la CPU puede acceder al almacenamiento de la matriz.|
|[extent](#extent)|Obtiene la extensión que define la forma de la matriz.|

## <a name="remarks"></a>Comentarios

El tipo `array<T,N>` representa una densa y regular (no escalonadas) *N*-matriz bidimensional que se encuentra en una ubicación específica, como un acelerador o la CPU. El tipo de datos de los elementos de la matriz es `T`, que debe ser de un tipo que es compatible con el Acelerador de destino. Aunque el rango, `N`, (de la matriz se determina estáticamente y forma parte del tipo, la extensión de la matriz viene determinada por el tiempo de ejecución y se expresa mediante el uso de la clase `extent<N>`.

Una matriz puede tener cualquier número de dimensiones, aunque alguna funcionalidad está especializada para `array` objetos con rango uno, dos y tres. Si se omite el argumento de la dimensión, el valor predeterminado es 1.

Datos de la matriz es contigua en la memoria. Los elementos que difieran en uno en la dimensión menos significativa están adyacentes en la memoria.

Las matrices se consideran lógicamente tipos de valor, ya que cuando se copia una matriz en otra matriz, se realiza una copia en profundidad. Dos matrices nunca apuntan a los mismos datos.

El `array<T,N>` tipo se usa en varios escenarios:

- Como un contenedor de datos que se puede utilizar en cálculos en un acelerador.

- Como contenedor de datos para mantener la memoria en la CPU del host (que puede utilizarse para copiar hacia y desde otras matrices).

- Como un objeto de almacenamiento provisional para que actúe como intermediario rápido en copias del host al dispositivo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`array`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

##  <a name="dtor"></a> ~ matriz

Destruye el objeto `array`.

```
~array() restrict(cpu);
```

##  <a name="accelerator_view"></a> accelerator_view

Obtiene el [accelerator_view](accelerator-view-class.md) objeto que representa la ubicación donde se asigna la matriz. Puede tener acceso a esta propiedad solo en la CPU.

```
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

##  <a name="ctor"></a> matriz

Inicializa una nueva instancia de la [array (clase)](array-class.md). No hay ningún constructor predeterminado para `array<T,N>`. Todos los constructores se ejecutan sólo en la CPU. No se puede ejecutar en un destino Direct3D.

```
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
Un accelerator_view que especifica la ubicación de destino preferida de la matriz.

*_Av*<br/>
Un [accelerator_view](accelerator-view-class.md) objeto que especifica la ubicación de la matriz.

*_Cpu_access_type*<br/>
Deseado [access_type](concurrency-namespace-enums-amp.md#access_type) para la matriz en la CPU. Este parámetro tiene un valor predeterminado de `access_type_auto` dejan la CPU `access_type` determinación al tiempo de ejecución. La CPU real `access_type` para la matriz puede consultarse utilizando el `get_cpu_access_type` método.

*_Extent*<br/>
La extensión de cada dimensión de la matriz.

*_E0*<br/>
El componente más significativo de la extensión de esta sección.

*_E1*<br/>
El siguiente-a-componente más significativo de la extensión de esta sección.

*_E2*<br/>
El componente menos significativo de la extensión de esta sección.

*_InputIterator*<br/>
El tipo del iterador de entrada.

*_Src*<br/>
Para el objeto a copiar.

*_Src_first*<br/>
Un iterador inicial en el contenedor de origen.

*_Src_last*<br/>
Un iterador final en el contenedor de origen.

*_Otro*<br/>
Otro origen de datos.

*_Rank*<br/>
El rango de la sección.

*value_type*<br/>
El tipo de datos de los elementos que se copian.

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

Obtiene el segundo [accelerator_view](accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor provisional para crear una instancia de la `array` objeto.

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

Copia el contenido de la `array` a otro `array`.

```
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>Parámetros

*_Dest*<br/>
El [array_view](array-view-class.md) objeto que se va a copiar en.

##  <a name="cpu_access_type"></a> cpu_access_type

Obtiene el access_type de CPU permitido para esta matriz.

```
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

##  <a name="data"></a> Datos

Devuelve un puntero a los datos sin procesar de la `array`.

```
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>Valor devuelto

Un puntero a los datos sin procesar de la matriz.

##  <a name="extent"></a> extensión

Obtiene el [extensión](extent-class.md) objeto que define la forma de la `array`.

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_accelerator_view"></a> get_accelerator_view

Devuelve el [accelerator_view](accelerator-view-class.md) objeto que representa la ubicación donde el `array` se asigna el objeto. Puede tener acceso a esta propiedad solo en la CPU.

```
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>Valor devuelto

El `accelerator_view` objeto que representa la ubicación donde el `array` se asigna el objeto.

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

Obtiene el segundo [accelerator_view](accelerator-view-class.md) objeto que se pasa como parámetro cuando se llama a un constructor provisional para crear una instancia de la `array` objeto.

```
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>Valor devuelto

El segundo [accelerator_view](accelerator-view-class.md) objeto pasado al constructor de almacenamiento provisional.

##  <a name="get_cpu_access_type"></a> get_cpu_access_type

Devuelve el access_type de CPU permitido para esta matriz.

```
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>Valor devuelto

##  <a name="get_extent"></a> get_extent

Devuelve el [extensión](extent-class.md) objeto de la `array`.

```
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

El `extent` objeto de la `array`.

##  <a name="operator_vec"></a> operador std:: vector&lt;value_type&gt;

Usa `copy(*this, vector)` para convertir implícitamente la matriz a un objeto std:: vector.

```
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
El tipo de datos de los elementos del vector.

### <a name="return-value"></a>Valor devuelto

Un objeto de tipo `vector<T>` que contiene una copia de los datos que se encuentra en la matriz.

##  <a name="operator_call"></a> Operator()

Devuelve el valor del elemento especificado por los parámetros.

```
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
La ubicación del elemento.

*_I0*<br/>
El componente más significativo del origen de esta sección.

*_I1*<br/>
El siguiente-a-componente más significativo del origen de esta sección.

*_I2*<br/>
El componente menos significativo del origen de esta sección.

*_I*<br/>
La ubicación del elemento.

### <a name="return-value"></a>Valor devuelto

El valor del elemento especificado por los parámetros.

##  <a name="operator_at"></a> operator]

Devuelve el elemento que se encuentra en el índice especificado.

```
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice.

*_I*<br/>
Índice.

### <a name="return-value"></a>Valor devuelto

El elemento que se encuentra en el índice especificado.

##  <a name="operator_eq"></a> operator=

Copia el contenido del elemento especificado `array` objeto.

```
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `array` objeto que se va a copiar desde.

*_Src*<br/>
La `array` objeto que se va a copiar desde.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `array` objeto.

##  <a name="rank"></a> rango

Almacena el rango de la `array`.

```
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a> reinterpret_as

Reinterpreta la matriz a través de array_view unidimensional, que opcionalmente puede tener un tipo de valor distinto de la matriz de origen.

### <a name="syntax"></a>Sintaxis

```
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Value_type2*<br/>
El tipo de datos de los datos devueltos.

### <a name="return-value"></a>Valor devuelto

Un array_view o un objeto array_view const que se basa en la matriz, con el tipo de elemento reinterpretado desde T a ElementType y el rango reducido de N a 1.

### <a name="remarks"></a>Comentarios

A veces es conveniente ver una matriz multidimensional como si fuera una matriz lineal y unidimensional, posiblemente con un tipo de valor diferente de la matriz de origen. Puede utilizar este método para lograrlo.
**Precaución** reinterpretar un objeto de matriz mediante el uso de otro tipo de valor es una operación potencialmente insegura. Se recomienda usar esta funcionalidad con cuidado.

El siguiente código proporciona un ejemplo.

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> Sección

Devuelve una subsección de la `array` objeto que está en el origen especificado y, opcionalmente, que tiene la extensión especificada.

```
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
El siguiente-a-componente más significativo de la extensión de esta sección.

*_E2*<br/>
El componente menos significativo de la extensión de esta sección.

*_Ext*<br/>
El [extensión](extent-class.md) objeto que especifica la extensión de la sección. El origen es 0.

*_Idx*<br/>
El [índice](index-class.md) objeto que especifica la ubicación de origen. La subsección es el resto de la extensión.

*_I0*<br/>
El componente más significativo del origen de esta sección.

*_I1*<br/>
El siguiente-a-componente más significativo del origen de esta sección.

*_I2*<br/>
El componente menos significativo del origen de esta sección.

*_Rank*<br/>
El rango de la sección.

*_Section_extent*<br/>
El [extensión](extent-class.md) objeto que especifica la extensión de la sección.

*_Section_origin*<br/>
El [índice](index-class.md) objeto que especifica la ubicación de origen.

*value_type*<br/>
El tipo de datos de los elementos que se copian.

### <a name="return-value"></a>Valor devuelto

Devuelve una subsección de la `array` objeto que está en el origen especificado y, opcionalmente, que tiene la extensión especificada. Cuando solo la `index` objeto se especifica, la subsección contiene todos los elementos de la cuadrícula asociada que tienen índices mayores que los índices de los elementos de la `index` objeto.

##  <a name="view_as"></a> view_as

Reinterpreta esta matriz como un [array_view](array-view-class.md) de un rango diferente.

```
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_New_rank*<br/>
El rango de la `extent` objeto pasado como parámetro.

*_View_extent*<br/>
La medida en que se usa para construir el nuevo [array_view](array-view-class.md) objeto.

*value_type*<br/>
El tipo de datos de los elementos de ambos original `array` devuelto `array_view` objeto.

### <a name="return-value"></a>Valor devuelto

El [array_view](array-view-class.md) objeto construido.

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
