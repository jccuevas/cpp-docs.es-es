---
title: array_view (Clase)
ms.date: 11/04/2016
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: 2aef75eedcde2a2064fe12815d9afd21fee2c293
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127142"
---
# <a name="array_view-class"></a>array_view (Clase)

Representa una vista de N dimensiones sobre los datos contenidos en otro contenedor.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename value_type,
    int _Rank = 1
>
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;

template <
    typename value_type,
    int _Rank
>
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
Tipo de datos de los elementos del objeto `array_view`.

*_Rank*<br/>
Rango del objeto de `array_view`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de array_view](#ctor)|Inicializa una nueva instancia de la clase `array_view`. No hay ningún constructor predeterminado para `array<T,N>`. Todos los constructores están restringidos para ejecutarse solo en la CPU y no se pueden ejecutar en un destino de Direct3D.|
|[~ array_view destructor](#ctor)|Destruye el objeto `array_view`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[copy_to](#copy_to)|Copia el contenido del objeto `array_view` en el destino especificado llamando a `copy(*this, dest)`.|
|[data](#data)|Devuelve un puntero a los datos sin procesar del `array_view`.|
|[discard_data](#discard_data)|Descarta los datos actuales subyacentes de esta vista.|
|[get_extent](#get_extent)|Devuelve el objeto extent del objeto array_view.|
|[get_ref](#get_ref)|Devuelve una referencia al elemento indizado.|
|[get_source_accelerator_view](#get_source_accelerator_view)|Devuelve el [accelerator_view](accelerator-view-class.md) en el que se encuentra el origen de datos de la `array_view`.|
|[actualizaciones](#refresh)|Notifica al objeto `array_view` que su memoria enlazada se ha modificado fuera de la interfaz `array_view`. Una llamada a este método representa toda la información almacenada en caché obsoleta.|
|[reinterpret_as](#reinterpret_as)|Devuelve una matriz unidimensional que contiene todos los elementos del objeto `array_view`.|
|[section](#section)|Devuelve una subsección del objeto `array_view` que está en el origen especificado y, opcionalmente, tiene la extensión especificada.|
|[synchronize](#synchronize)|Sincroniza las modificaciones realizadas en el objeto de `array_view` de nuevo con sus datos de origen.|
|[synchronize_async](#synchronize_async)|Sincroniza asincrónicamente cualquier modificación realizada en el objeto `array_view` a sus datos de origen.|
|[synchronize_to](#synchronize_to)|Sincroniza cualquier modificación realizada en el objeto `array_view` con el [accelerator_view](accelerator-view-class.md)especificado.|
|[synchronize_to_async](#synchronize_to_async)|Sincroniza de forma asincrónica las modificaciones realizadas en el objeto `array_view` en el [accelerator_view](accelerator-view-class.md)especificado.|
|[view_as](#view_as)|Genera un objeto `array_view` de un rango diferente utilizando los datos de este objeto `array_view`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator()](#operator_call)|Devuelve el valor del elemento especificado por el parámetro o los parámetros.|
|[operator\[\]](#operator_at)|Devuelve el elemento especificado por los parámetros.|
|[operator=](#operator_eq)|Copia el contenido del objeto `array_view` especificado en este.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[Rank (constante)](#rank)|Almacena el rango del objeto `array_view`.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[extent](#extent)|Obtiene el objeto `extent` que define la forma del objeto `array_view`.|
|[source_accelerator_view](#source_accelerator_view)|Obtiene el [accelerator_view](accelerator-view-class.md) en el que se encuentra el origen de datos del `array_view`|
|[value_type](#value_type)|El tipo de valor de la `array_view` y la matriz enlazada.|

## <a name="remarks"></a>Observaciones

La clase `array_view` representa una vista de los datos contenidos en un objeto de [matriz](array-class.md) o una subsección de un objeto `array`.

Puede tener acceso al objeto de `array_view` en el que se encuentran los datos de origen (localmente) o en un acelerador o dominio de coherencia diferente (de forma remota). Al tener acceso al objeto de forma remota, las vistas se copian y se almacenan en caché según sea necesario. A excepción de los efectos del almacenamiento en caché automático, `array_view` objetos tienen un perfil de rendimiento similar al de `array` objetos. Hay una pequeña reducción del rendimiento cuando se tiene acceso a los datos a través de las vistas.

Hay tres escenarios de uso remoto:

- Una vista de un puntero de memoria del sistema se pasa por medio de una llamada [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) a un acelerador y al que se tiene acceso en el acelerador.

- Una vista a una matriz ubicada en un acelerador se pasa por medio de una llamada `parallel_for_each` a otro acelerador y se obtiene acceso a ella.

- Se tiene acceso a una vista a una matriz ubicada en un acelerador en la CPU.

En cualquiera de estos escenarios, el tiempo de ejecución copia las vistas a las que se hace referencia en la ubicación remota y, si las modifican las llamadas al objeto `array_view`, se vuelven a copiar en la ubicación local. El tiempo de ejecución podría optimizar el proceso de copia de los cambios, puede copiar solo los elementos modificados o copiar también las partes sin cambios. No se garantiza la superposición de objetos `array_view` en un origen de datos para mantener la integridad referencial en una ubicación remota.

Debe sincronizar cualquier acceso multiproceso con el mismo origen de datos.

El tiempo de ejecución de hace las siguientes garantías respecto al almacenamiento en caché de datos en objetos de `array_view`:

- Todos los accesos bien sincronizados a un objeto `array` y un objeto `array_view` en él en el orden del programa obedecen a una relación de sucede en serie antes.

- Todos los accesos bien sincronizados a objetos de `array_view` superpuestos en el mismo acelerador en un único objeto de `array` tienen un alias a través del objeto `array`. Inducen una relación de tiene lugar total: antes que obedece el orden del programa. No hay almacenamiento en caché. Si los objetos de `array_view` se ejecutan en aceleradores diferentes, el orden de acceso es indefinido, lo que crea una condición de carrera.

Al crear un objeto de `array_view` mediante un puntero en la memoria del sistema, debe cambiar el objeto de `array_view` de vista solo a través del puntero de `array_view`. Como alternativa, debe llamar a `refresh()` en uno de los objetos `array_view` asociados al puntero del sistema, si la memoria nativa subyacente cambia directamente, en lugar de a través del objeto `array_view`.

Cualquier acción notifica al objeto `array_view` que la memoria nativa subyacente cambia y que las copias que se encuentran en un acelerador están obsoletas. Si sigue estas instrucciones, las vistas basadas en punteros son idénticas a las que se proporcionan a las vistas de matrices paralelas de datos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="dtor"></a>~ array_view

Destruye el objeto `array_view`.

```cpp
~array_view()restrict(amp,cpu);
```

## <a name="ctor"></a>array_view

Inicializa una nueva instancia de la clase `array_view`.

```cpp
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view& _Other)restrict(amp,cpu);

explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    _Container& _Src) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    int _E0,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _Container& _Src);

explicit array_view(
    int _E0,
    _In_ value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    _In_ value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _In_ value_type* _Src)restrict(amp,cpu);

array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const _Container& _Src) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    const _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    int _E0,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    int _E2,
    const _Container& _Src);

array_view(
    int _E0,
    const value_type* _Src)restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    const value_type* _Src) restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    int _E2,
    const value_type* _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Arr_type*<br/>
El tipo de elemento de una matriz de estilo C desde la que se proporcionan los datos.

*_Container*<br/>
Un argumento de plantilla que debe especificar un contenedor lineal que admita `data()` y `size()` miembros.

*_E0*<br/>
El componente más significativo de la extensión de esta sección.

*_E1*<br/>
El siguiente componente más significativo de la extensión de esta sección.

*_E2*<br/>
El componente menos significativo de la extensión de esta sección.

*_Extent*<br/>
La extensión de cada dimensión de este `array_view`.

*_Other*<br/>
Objeto de tipo `array_view<T,N>` a partir del cual se inicializará el nuevo `array_view`.

*_Size*<br/>
Tamaño de una matriz de estilo C desde la que se proporcionan los datos.

*_Src*<br/>
Puntero a los datos de origen que se copiarán en la nueva matriz.

## <a name="copy_to"></a>copy_to

Copia el contenido del objeto `array_view` en el objeto de destino especificado llamando a `copy(*this, dest)`.

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>Parámetros

*_Dest*<br/>
El objeto en el que se copia.

## <a name="data"></a>Data

Devuelve un puntero a los datos sin procesar del `array_view`.

```cpp
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>Valor devuelto

Puntero a los datos sin procesar del `array_view`.

## <a name="discard_data"></a>discard_data

Descarta los datos actuales subyacentes de esta vista. Se trata de una sugerencia de optimización para el tiempo de ejecución que se usa para evitar copiar el contenido actual de la vista en una `accelerator_view` de destino a la que se tiene acceso, y se recomienda su uso si no se necesita el contenido existente. Este método es una operación no operativa cuando se usa en un contexto de restricción (amp)

```cpp
void discard_data() const restrict(cpu);
```

## <a name="extent"></a>expresa

Obtiene el objeto `extent` que define la forma del objeto `array_view`.

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_extent"></a>get_extent

Devuelve el objeto [extent](extent-class.md) del objeto `array_view`.

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>Valor devuelto

Objeto `extent` del objeto `array_view`.

## <a name="get_ref"></a>get_ref

Obtiene una referencia al elemento indizado por _Index. A diferencia de otros operadores de indización para tener acceso al array_view en la CPU, este método no sincroniza implícitamente el contenido de este array_view con la CPU. Después de obtener acceso a la array_view en una ubicación remota o de realizar una operación de copia que implique a este array_view los usuarios son responsables de sincronizar explícitamente el array_view con la CPU antes de llamar a este método. Si no lo hace, se producirá un comportamiento indefinido.

```cpp
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice.

### <a name="return-value"></a>Valor devuelto

Referencia al elemento indizado por _Index

## <a name="get_source_accelerator_view"></a>get_source_accelerator_view

Devuelve el accelerator_view en el que se encuentra el origen de datos de la array_view. Si el array_view no tiene un origen de datos, esta API inicia una runtime_exception

```cpp
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="operator_call"></a>operador ()

Devuelve el valor del elemento especificado por el parámetro o los parámetros.

```cpp
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Ubicación del elemento.

*_I0*<br/>
Índice de la primera dimensión.

*_I1*<br/>
Índice de la segunda dimensión.

*_I2*<br/>
Índice de la tercera dimensión.

*_I*<br/>
Ubicación del elemento.

### <a name="return-value"></a>Valor devuelto

Valor del elemento especificado por el parámetro o los parámetros.

## <a name="operator_at"></a>operador []

Devuelve el elemento especificado por los parámetros.

```cpp
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice.

*_I*<br/>
El índice.

### <a name="return-value"></a>Valor devuelto

El valor del elemento en el índice o un `array_view` proyectado en la dimensión más significativa.

## <a name="operator_eq"></a>operador =

Copia el contenido del objeto `array_view` especificado en este.

```cpp
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto de `array_view` del que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `array_view`.

## <a name="rank"></a>criterios

Almacena el rango del objeto `array_view`.

```cpp
static const int rank = _Rank;
```

## <a name="refresh"></a>actualizaciones

Notifica al objeto `array_view` que su memoria enlazada se ha modificado fuera de la interfaz `array_view`. Una llamada a este método representa toda la información almacenada en caché obsoleta.

```cpp
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a>reinterpret_as

Reinterpreta el array_view a través de un array_view unidimensional, que, como opción, puede tener un tipo de valor distinto al de la array_view de origen.

### <a name="syntax"></a>Sintaxis

```cpp
template <
    typename _Value_type2
>
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);

template <
    typename _Value_type2
>
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Value_type2*<br/>
El tipo de datos del nuevo objeto de `array_view`.

### <a name="return-value"></a>Valor devuelto

Un objeto `array_view` o un objeto `array_view` const que se basa en este `array_view`, con el tipo de elemento convertido de `T` a `_Value_type2`y el rango reducido de *N* a 1.

### <a name="remarks"></a>Observaciones

A veces es conveniente ver una matriz multidimensional como una matriz lineal y unidimensional, que puede tener un tipo de valor distinto de la matriz de origen. Puede conseguirlo en un `array_view` mediante este método.

**ADVERTENCIA** de Reinterpretar un objeto array_view mediante un tipo de valor diferente es una operación potencialmente insegura. Esta funcionalidad debe usarse con cuidado.

Este es un ejemplo:

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>transversal

Devuelve una subsección del objeto `array_view` que está en el origen especificado y, opcionalmente, tiene la extensión especificada.

```cpp
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view section(
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

### <a name="return-value"></a>Valor devuelto

Subsección del objeto `array_view` que está en el origen especificado y, opcionalmente, que tiene la extensión especificada. Cuando solo se especifica el objeto `index`, la subsección contiene todos los elementos de la extensión asociada que tienen índices mayores que los índices de los elementos del objeto `index`.

## <a name="source_accelerator_view"></a>source_accelerator_view

Obtiene el accelerator_view de origen al que está asociado este array_view.

```cpp
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

## <a name="synchronize"></a>sincronizándose

Sincroniza las modificaciones realizadas en el objeto de `array_view` de nuevo con sus datos de origen.

```cpp
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Access_type*<br/>
[Access_type](concurrency-namespace-enums-amp.md#access_type) previsto en el [accelerator_view](accelerator-view-class.md)de destino. Este parámetro tiene un valor predeterminado de `access_type_read`.

## <a name="synchronize_async"></a>synchronize_async

Sincroniza asincrónicamente cualquier modificación realizada en el objeto `array_view` a sus datos de origen.

```cpp
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Access_type*<br/>
[Access_type](concurrency-namespace-enums-amp.md#access_type) previsto en el [accelerator_view](accelerator-view-class.md)de destino. Este parámetro tiene un valor predeterminado de `access_type_read`.

### <a name="return-value"></a>Valor devuelto

Un futuro en el que esperar a que se complete la operación.

## <a name="synchronize_to"></a>synchronize_to

Sincroniza las modificaciones realizadas en este array_view con el accelerator_view especificado.

```cpp
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Accl_view*<br/>
Accelerator_view de destino en el que se va a sincronizar.

*_Access_type*<br/>
Access_type deseada en el accelerator_view de destino. Este parámetro tiene un valor predeterminado de access_type_read.

## <a name="synchronize_to_async"></a>synchronize_to_async

Sincroniza de forma asincrónica las modificaciones realizadas en este array_view en el accelerator_view especificado.

```cpp
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Accl_view*<br/>
Accelerator_view de destino en el que se va a sincronizar.

*_Access_type*<br/>
Access_type deseada en el accelerator_view de destino. Este parámetro tiene un valor predeterminado de access_type_read.

### <a name="return-value"></a>Valor devuelto

Un futuro en el que esperar a que se complete la operación.

## <a name="value_type"></a>value_type

El tipo de valor de la array_view y la matriz enlazada.

```cpp
typedef typenamevalue_type value_type;
```

## <a name="view_as"></a>view_as

Reinterpreta este `array_view` como un `array_view` de un rango diferente.

```cpp
template <
    int _New_rank
>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

template <
    int _New_rank
>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_New_rank*<br/>
Rango del nuevo objeto de `array_view`.

*_View_extent*<br/>
`extent`de remodelado.

*value_type*<br/>
El tipo de datos de los elementos en el objeto de [matriz](array-class.md) original y en el objeto de `array_view` devuelto.

### <a name="return-value"></a>Valor devuelto

Objeto `array_view` que se construye.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
