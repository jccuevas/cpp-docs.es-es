---
title: concurrent_vector (clase)
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: 002f1e3f691de3315810efed8f7d8f6c547cf653
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854228"
---
# <a name="concurrent_vector-class"></a>concurrent_vector (clase)

La clase `concurrent_vector` es una clase de contenedor de secuencia que permite el acceso aleatorio a cualquier elemento. Habilita las operaciones de anexión segura para simultaneidad, acceso de elemento, acceso de iterador e iterador transversal. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de datos de los elementos que se van a almacenar en el vector.

*_Ax*<br/>
El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo. Este argumento es opcional y el valor predeterminado es `allocator<T>`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`allocator_type`|Tipo que representa la clase de asignador para el vector simultáneo.|
|`const_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer un elemento de `const` en un vector simultáneo.|
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento en un vector simultáneo.|
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en un vector simultáneo para leer y realizar operaciones de `const`.|
|`const_reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento `const` del vector simultáneo.|
|`difference_type`|Un tipo que proporciona la distancia con signo entre dos elementos de un vector simultáneo.|
|`iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento de un vector simultáneo. La modificación de un elemento mediante el iterador no es segura para simultaneidad.|
|`pointer`|Un tipo que proporciona un puntero a un elemento en un vector simultáneo.|
|`reference`|Un tipo que proporciona una referencia a un elemento almacenado en un vector simultáneo.|
|`reverse_iterator`|Un tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento en un vector simultáneo invertido. La modificación de un elemento mediante el iterador no es segura para simultaneidad.|
|`size_type`|Tipo que cuenta el número de elementos de un vector simultáneo.|
|`value_type`|Tipo que representa el tipo de datos almacenado en un vector simultáneo.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[concurrent_vector](#ctor)|Sobrecargado. Construye un vector simultáneo.|
|[~ concurrent_vector destructor](#dtor)|Borra todos los elementos y destruye este vector simultáneo.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[assign](#assign)|Sobrecargado. Borra los elementos del vector simultáneo y les asigna `_N` copias de `_Item`o los valores especificados por el intervalo de iterador [`_Begin`, `_End`). Este método no es seguro para la simultaneidad.|
|[at](#at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad en las operaciones de lectura y, al mismo tiempo, aumenta el vector, siempre y cuando se haya asegurado de que el valor `_Index` sea menor que el tamaño del vector simultáneo.|
|[back](#back)|Sobrecargado. Devuelve una referencia o una referencia `const` al último elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|
|[begin](#begin)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[capacidad](#capacity)|Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.|
|[cbegin](#cbegin)|Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[cend](#cend)|Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[clear](#clear)|Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.|
|[crbegin](#crbegin)|Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[crend](#crend)|Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[empty](#empty)|Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.|
|[end](#end)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[front](#front)|Sobrecargado. Devuelve una referencia o una referencia `const` al primer elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.|
|[get_allocator](#get_allocator)|Devuelve una copia del asignador utilizado para construir el vector simultáneo. Este método es seguro para simultaneidad.|
|[grow_by](#grow_by)|Sobrecargado. Amplía este vector simultáneo por `_Delta` elementos. Este método es seguro para simultaneidad.|
|[grow_to_at_least](#grow_to_at_least)|Aumenta este vector simultáneo hasta que tiene al menos `_N` elementos. Este método es seguro para simultaneidad.|
|[max_size](#max_size)|Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.|
|[push_back](#push_back)|Sobrecargado. Anexa el elemento especificado al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[rbegin](#rbegin)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.|
|[rend](#rend)|Sobrecargado. Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.|
|[reserve](#reserve)|Asigna espacio suficiente para aumentar el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.|
|[resize](#resize)|Sobrecargado. Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando los elementos según sea necesario. Este método no es seguro para la simultaneidad.|
|[shrink_to_fit](#shrink_to_fit)|Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.|
|[size](#size)|Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.|
|[swap](#swap)|Intercambia el contenido de dos vectores simultáneos. Este método no es seguro para la simultaneidad.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator\[\]](#operator_at)|Sobrecargado. Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad en las operaciones de lectura y, al mismo tiempo, aumenta el vector, siempre que el se haya asegurado de que el valor `_Index` sea menor que el tamaño del vector simultáneo.|
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_vector` a este. Este método no es seguro para la simultaneidad.|

## <a name="remarks"></a>Observaciones

Para obtener información detallada sobre la clase `concurrent_vector`, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Requisitos

**Encabezado:** concurrent_vector. h

**Espacio de nombres:** simultaneidad

## <a name="assign"></a>quitar

Borra los elementos del vector simultáneo y les asigna `_N` copias de `_Item`o los valores especificados por el intervalo de iterador [`_Begin`, `_End`). Este método no es seguro para la simultaneidad.

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parámetros

*_InputIterator*<br/>
Tipo del iterador especificado.

*_N*<br/>
Número de elementos que se van a copiar en el vector simultáneo.

*_Item*<br/>
Referencia a un valor que se usa para rellenar el vector simultáneo.

*_Begin*<br/>
Un iterador al primer elemento del intervalo de origen.

*_End*<br/>
Un iterador a uno más allá del último elemento del intervalo de origen.

### <a name="remarks"></a>Observaciones

`assign` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso está invocando métodos en el vector simultáneo al llamar a este método.

## <a name="at"></a>Veamos

Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad en las operaciones de lectura y, al mismo tiempo, aumenta el vector, siempre y cuando se haya asegurado de que el valor `_Index` sea menor que el tamaño del vector simultáneo.

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Referencia al elemento en el índice especificado.

### <a name="remarks"></a>Observaciones

La versión de la función `at` que devuelve una referencia que no es de `const` no se puede usar para escribir simultáneamente en el elemento de distintos subprocesos. Se debe usar un objeto de sincronización distinto para sincronizar las operaciones de lectura y escritura simultáneas en el mismo elemento de datos.

El método produce `out_of_range` si `_Index` es mayor o igual que el tamaño del vector simultáneo y `range_error` si el índice es para una parte rota del vector. Para obtener más información sobre cómo se puede interrumpir un vector, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="back"></a>Atrás

Devuelve una referencia o una referencia `const` al último elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a `const` referencia al último elemento del vector simultáneo.

## <a name="begin"></a>inicia

Devuelve un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `iterator` o `const_iterator` al principio del vector simultáneo.

## <a name="capacity"></a>incapacidad

Devuelve el tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria. Este método es seguro para simultaneidad.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño máximo que puede alcanzar el vector simultáneo sin tener que asignar más memoria.

### <a name="remarks"></a>Observaciones

A diferencia de C++ una biblioteca estándar `vector`, un objeto `concurrent_vector` no mueve los elementos existentes si asigna más memoria.

## <a name="cbegin"></a>cbegin (

Devuelve un iterador de tipo `const_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_iterator` al principio del vector simultáneo.

## <a name="cend"></a>cend

Devuelve un iterador de tipo `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_iterator` al final del vector simultáneo.

## <a name="clear"></a>claridad

Borra todos los elementos del vector simultáneo. Este método no es seguro para la simultaneidad.

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

`clear` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso está invocando métodos en el vector simultáneo al llamar a este método. `clear` no libera las matrices internas. Para liberar matrices internas, llame a la función `shrink_to_fit` después de `clear`.

## <a name="ctor"></a>concurrent_vector

Construye un vector simultáneo.

```cpp
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>Parámetros

*M*<br/>
El tipo de asignador del vector de origen.

*_InputIterator*<br/>
El tipo de iterador de entrada.

*_Al*<br/>
La clase de asignador que se usa con este objeto.

*_Vector*<br/>
El objeto de origen `concurrent_vector` del que copiar o mover elementos.

*_N*<br/>
Capacidad inicial del objeto `concurrent_vector`.

*_Item*<br/>
El valor de elementos en el objeto construido.

*_Begin*<br/>
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*_End*<br/>
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

### <a name="remarks"></a>Observaciones

Todos los constructores almacenan un objeto de asignador `_Al` e inicializan el vector.

El primer constructor especifica un vector inicial vacío y especifica explícitamente el tipo de asignador. que se va a usar.

El segundo y tercer constructor especifican una copia del vector simultáneo `_Vector`.

El cuarto constructor especifica un movimiento del vector simultáneo `_Vector`.

El quinto constructor especifica una repetición de un número especificado (`_N`) de elementos del valor predeterminado para la clase `T`.

El sexto constructor especifica una repetición de elementos (`_N`) de valor `_Item`.

El último constructor especifica los valores proporcionados por el intervalo de iterador [`_Begin`, `_End`).

## <a name="dtor"></a>~ concurrent_vector

Borra todos los elementos y destruye este vector simultáneo.

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a>crbegin

Devuelve un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_reverse_iterator` al principio del vector simultáneo.

## <a name="crend"></a>crend

Devuelve un iterador de tipo `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `const_reverse_iterator` al final del vector simultáneo.

## <a name="empty"></a>vacía

Comprueba si el vector simultáneo está vacío en el momento en que se llama a este método. Este método es seguro para simultaneidad.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el vector estaba vacío en el momento en que se llamó a la función; de lo contrario, **false** .

## <a name="end"></a>extremo

Devuelve un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `iterator` o `const_iterator` al final del vector simultáneo.

## <a name="front"></a>end

Devuelve una referencia o una referencia `const` al primer elemento del vector simultáneo. Si el vector simultáneo está vacío, el valor devuelto es indefinido. Este método es seguro para simultaneidad.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a `const` referencia al primer elemento del vector simultáneo.

## <a name="get_allocator"></a>get_allocator

Devuelve una copia del asignador utilizado para construir el vector simultáneo. Este método es seguro para simultaneidad.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Una copia del asignador utilizado para construir el objeto de `concurrent_vector`.

## <a name="grow_by"></a>grow_by

Amplía este vector simultáneo por `_Delta` elementos. Este método es seguro para simultaneidad.

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Parámetros

*_Delta*<br/>
Número de elementos que se van a anexar al objeto.

*_Item*<br/>
Valor con el que se van a inicializar los nuevos elementos.

### <a name="return-value"></a>Valor devuelto

Un iterador al primer elemento anexado.

### <a name="remarks"></a>Observaciones

Si no se especifica `_Item`, se construyen los nuevos elementos de forma predeterminada.

## <a name="grow_to_at_least"></a>grow_to_at_least

Aumenta este vector simultáneo hasta que tiene al menos `_N` elementos. Este método es seguro para simultaneidad.

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Parámetros

*_N*<br/>
Nuevo tamaño mínimo del objeto `concurrent_vector`.

### <a name="return-value"></a>Valor devuelto

Un iterador que apunta al principio de la secuencia anexada o al elemento en el índice `_N` si no se anexa ningún elemento.

## <a name="max_size"></a>max_size

Devuelve el número máximo de elementos que puede contener el vector simultáneo. Este método es seguro para simultaneidad.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Número máximo de elementos que puede contener el objeto de `concurrent_vector`.

## <a name="operator_eq"></a>operador =

Asigna el contenido de otro objeto `concurrent_vector` a este. Este método no es seguro para la simultaneidad.

```cpp
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>Parámetros

*M*<br/>
El tipo de asignador del vector de origen.

*_Vector*<br/>
Objeto `concurrent_vector` de origen.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `concurrent_vector`.

## <a name="operator_at"></a>operador []

Proporciona acceso al elemento en el índice especificado del vector simultáneo. Este método es seguro para simultaneidad en las operaciones de lectura y, al mismo tiempo, aumenta el vector, siempre que el se haya asegurado de que el valor `_Index` sea menor que el tamaño del vector simultáneo.

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Referencia al elemento en el índice especificado.

### <a name="remarks"></a>Observaciones

La versión de `operator []` que devuelve una referencia no `const` no se puede usar para escribir simultáneamente en el elemento de distintos subprocesos. Se debe usar un objeto de sincronización distinto para sincronizar las operaciones de lectura y escritura simultáneas en el mismo elemento de datos.

No se realiza ninguna comprobación de los límites para asegurarse de que `_Index` sea un índice válido en el vector simultáneo.

## <a name="push_back"></a>push_back

Anexa el elemento especificado al final del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Parámetros

*_Item*<br/>
Valor que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Un iterador al elemento anexado.

## <a name="rbegin"></a>rbegin

Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al principio del vector simultáneo.

## <a name="rend"></a>Rend

Devuelve un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `reverse_iterator` o `const_reverse_iterator` al final del vector simultáneo.

## <a name="reserve"></a>realizan

Asigna espacio suficiente para aumentar el vector simultáneo al tamaño `_N` sin tener que asignar más memoria más adelante. Este método no es seguro para la simultaneidad.

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>Parámetros

*_N*<br/>
Número de elementos para los que se va a reservar espacio.

### <a name="remarks"></a>Observaciones

`reserve` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso está invocando métodos en el vector simultáneo al llamar a este método. La capacidad del vector simultáneo después de la devolución del método puede ser mayor que la reserva solicitada.

## <a name="resize"></a>cambiar el tamaño

Cambia el tamaño del vector simultáneo al tamaño solicitado, eliminando o agregando los elementos según sea necesario. Este método no es seguro para la simultaneidad.

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Parámetros

*_N*<br/>
Nuevo tamaño de la concurrent_vector.

*val*<br/>
Valor de los nuevos elementos agregados al vector si el nuevo tamaño es mayor que el tamaño original. Si se omite el valor, a los nuevos objetos se les asigna el valor predeterminado para su tipo.

### <a name="remarks"></a>Observaciones

Si el tamaño del contenedor es menor que el tamaño solicitado, se agregan elementos al vector hasta que alcanza el tamaño solicitado. Si el tamaño del contenedor es mayor que el tamaño solicitado, se eliminan los elementos más cercanos al final del contenedor hasta que el contenedor alcanza el tamaño `_N`. Si el tamaño actual del contenedor es igual que el tamaño solicitado, no se lleva a cabo ninguna acción.

`resize` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso está invocando métodos en el vector simultáneo al llamar a este método.

## <a name="shrink_to_fit"></a>shrink_to_fit

Compacta la representación interna del vector simultáneo para reducir la fragmentación y optimizar el uso de memoria. Este método no es seguro para la simultaneidad.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Observaciones

Este método reasignará internamente los elementos de movimiento de memoria, invalidando todos los iteradores. `shrink_to_fit` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso está invocando métodos en el vector simultáneo cuando se llama a esta función.

## <a name="size"></a>ajusta

Devuelve el número de elementos del vector simultáneo. Este método es seguro para simultaneidad.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de este objeto `concurrent_vector`.

### <a name="remarks"></a>Observaciones

Se garantiza que el tamaño devuelto incluye todos los elementos anexados mediante llamadas a la función `push_back`, o las operaciones de crecimiento que se han completado antes de invocar este método. Sin embargo, también puede incluir elementos que están asignados pero que todavía están en construcción mediante llamadas simultáneas a cualquiera de los métodos de crecimiento.

## <a name="swap"></a>pasar

Intercambia el contenido de dos vectores simultáneos. Este método no es seguro para la simultaneidad.

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Parámetros

*_Vector*<br/>
Objeto `concurrent_vector` con el que se va a intercambiar el contenido.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)
