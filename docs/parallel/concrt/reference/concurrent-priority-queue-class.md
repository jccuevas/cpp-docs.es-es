---
title: concurrent_priority_queue (clase)
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 1d8651d1391ded2970a00a7429c36f341a438659
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143217"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue (clase)

La clase `concurrent_priority_queue` es un contenedor que permite que varios subprocesos inserten y extraigan elementos de forma simultánea. Los elementos se extraen en orden de prioridad donde la prioridad viene determinada por un functor proporcionado como un argumento de plantilla.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de datos de los elementos que se van a almacenar en la cola de prioridad.

*_Compare*<br/>
Tipo del objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en la cola de prioridad. Este argumento es opcional y el predicado binario `less<T>` es el valor predeterminado.

*_Ax*<br/>
Tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre la asignación y desasignación de memoria para la cola de prioridad simultánea. Este argumento es opcional y el valor predeterminado es `allocator<T>`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`allocator_type`|Tipo que representa la clase de asignador para la cola de prioridad simultánea.|
|`const_reference`|Tipo que representa una referencia const a un elemento del tipo almacenado en una cola de prioridad simultánea.|
|`reference`|Tipo que representa una referencia a un elemento del tipo almacenado en una cola de prioridad simultánea.|
|`size_type`|Tipo que cuenta el número de elementos de una cola de prioridad simultánea.|
|`value_type`|Tipo que representa el tipo de datos almacenado en una cola de prioridad simultánea.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Sobrecargado. Construye una cola de prioridad simultánea.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[clear](#clear)|Borra todos los elementos de la prioridad simultánea. Este método no es seguro para la simultaneidad.|
|[empty](#empty)|Comprueba si la cola de prioridad simultánea está vacía en el momento en que se llama a este método. Este método es seguro para simultaneidad.|
|[get_allocator](#get_allocator)|Devuelve una copia del asignador utilizado para construir la cola de prioridad simultánea. Este método es seguro para simultaneidad.|
|[push](#push)|Sobrecargado. Agrega un elemento a la cola de prioridad simultánea. Este método es seguro para simultaneidad.|
|[size](#size)|Devuelve el número de elementos de la cola de prioridad simultánea. Este método es seguro para simultaneidad.|
|[swap](#swap)|Intercambia el contenido de dos colas de prioridad simultáneas. Este método no es seguro para la simultaneidad.|
|[try_pop](#try_pop)|Quita y devuelve el elemento de prioridad más alto de la cola si la cola no está vacía. Este método es seguro para simultaneidad.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_priority_queue` a este. Este método no es seguro para la simultaneidad.|

## <a name="remarks"></a>Observaciones

Para obtener información detallada sobre la clase `concurrent_priority_queue`, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`concurrent_priority_queue`

## <a name="requirements"></a>Requisitos

**Encabezado:** concurrent_priority_queue. h

**Espacio de nombres:** simultaneidad

## <a name="clear"></a>claridad

Borra todos los elementos de la prioridad simultánea. Este método no es seguro para la simultaneidad.

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

`clear` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso está invocando métodos en la cola de prioridad simultánea al llamar a este método. `clear` no libera memoria.

## <a name="ctor"></a>concurrent_priority_queue

Construye una cola de prioridad simultánea.

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>Parámetros

*_InputIterator*<br/>
El tipo de iterador de entrada.

*_Al*<br/>
La clase de asignador que se usa con este objeto.

*_Init_capacity*<br/>
Capacidad inicial del objeto `concurrent_priority_queue`.

*_Begin*<br/>
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*_End*<br/>
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

*_Src*<br/>
El objeto de origen `concurrent_priority_queue` del que copiar o mover elementos.

### <a name="remarks"></a>Observaciones

Todos los constructores almacenan un objeto de asignador `_Al` e inicializan la cola de prioridad.

El primer constructor especifica una cola de prioridad inicial vacía y, opcionalmente, especifica un asignador.

El segundo constructor especifica una cola de prioridad con una capacidad inicial `_Init_capacity` y, opcionalmente, especifica un asignador.

El tercer constructor especifica los valores proporcionados por el intervalo de iterador [`_Begin`, `_End`) y, opcionalmente, especifica un asignador.

Los constructores cuarto y quinto especifican una copia de la cola de prioridad `_Src`.

Los constructores sexto y séptimo especifican un movimiento del `_Src`de la cola de prioridad.

## <a name="empty"></a>vacía

Comprueba si la cola de prioridad simultánea está vacía en el momento en que se llama a este método. Este método es seguro para simultaneidad.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si la cola de prioridad estaba vacía en el momento en que se llamó a la función; de lo contrario, **false** .

## <a name="get_allocator"></a>get_allocator

Devuelve una copia del asignador utilizado para construir la cola de prioridad simultánea. Este método es seguro para simultaneidad.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Una copia del asignador utilizado para construir el objeto de `concurrent_priority_queue`.

## <a name="operator_eq"></a>operador =

Asigna el contenido de otro objeto `concurrent_priority_queue` a este. Este método no es seguro para la simultaneidad.

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Objeto `concurrent_priority_queue` de origen.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `concurrent_priority_queue`.

## <a name="push"></a>enviar

Agrega un elemento a la cola de prioridad simultánea. Este método es seguro para simultaneidad.

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Parámetros

*_Elem*<br/>
Elemento que se va a agregar a la cola de prioridad simultánea.

## <a name="size"></a>ajusta

Devuelve el número de elementos de la cola de prioridad simultánea. Este método es seguro para simultaneidad.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de este objeto `concurrent_priority_queue`.

### <a name="remarks"></a>Observaciones

Se garantiza que el tamaño devuelto incluye todos los elementos agregados por las llamadas a la función `push`. Sin embargo, puede que no refleje los resultados de operaciones simultáneas pendientes.

## <a name="swap"></a>pasar

Intercambia el contenido de dos colas de prioridad simultáneas. Este método no es seguro para la simultaneidad.

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Parámetros

*_Queue*<br/>
Objeto `concurrent_priority_queue` con el que se va a intercambiar el contenido.

## <a name="try_pop"></a>try_pop

Quita y devuelve el elemento de prioridad más alto de la cola si la cola no está vacía. Este método es seguro para simultaneidad.

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Parámetros

*_Elem*<br/>
Referencia a una variable que se rellenará con el elemento de prioridad más alto, si la cola no está vacía.

### <a name="return-value"></a>Valor devuelto

**true** si se ha extraído un valor; de lo contrario, **false** .

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)
