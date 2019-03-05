---
title: concurrent_priority_queue (Clase)
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
ms.openlocfilehash: 5804675ffdaf6de2e73327103398316566b41627
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304787"
---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue (Clase)

La clase `concurrent_priority_queue` es un contenedor que permite que varios subprocesos inserten y extraigan elementos de forma simultánea. Los elementos se extraen en orden de prioridad donde la prioridad viene determinada por un functor proporcionado como un argumento de plantilla.

## <a name="syntax"></a>Sintaxis

```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos que se almacenará en la cola de prioridad.

*_Compare*<br/>
El tipo de objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en la cola de prioridad. Este argumento es opcional y el predicado binario `less<T>` es el valor predeterminado.

*_Ax*<br/>
El tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre la asignación y desasignación de memoria para la cola de prioridad simultáneas. Este argumento es opcional y el valor predeterminado es `allocator<T>`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`allocator_type`|Tipo que representa la clase de asignador de la cola de prioridad simultáneas.|
|`const_reference`|Tipo que representa una referencia constante a un elemento del tipo almacenado en una cola de prioridad simultáneas.|
|`reference`|Tipo que representa una referencia a un elemento del tipo almacenado en una cola de prioridad simultáneas.|
|`size_type`|Un tipo que cuenta el número de elementos de una cola de prioridad simultáneas.|
|`value_type`|Tipo que representa el tipo de datos almacenado en una cola de prioridad simultáneas.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Sobrecargado. Construye una cola de prioridad simultáneas.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[clear](#clear)|Borra todos los elementos en la prioridad simultánea. Este método no es seguro para la simultaneidad.|
|[empty](#empty)|Comprueba si la cola de prioridad simultáneas está vacía en el momento en que se llama a este método. Este método es seguro para simultaneidad.|
|[get_allocator](#get_allocator)|Devuelve una copia del asignador usado para construir la cola de prioridad simultáneas. Este método es seguro para simultaneidad.|
|[push](#push)|Sobrecargado. Agrega un elemento a la cola de prioridad simultáneas. Este método es seguro para simultaneidad.|
|[size](#size)|Devuelve el número de elementos en la cola de prioridad simultáneas. Este método es seguro para simultaneidad.|
|[swap](#swap)|Intercambia el contenido de dos colas de prioridad simultáneas. Este método no es seguro para la simultaneidad.|
|[try_pop](#try_pop)|Quita y devuelve el elemento de prioridad más alto de la cola si la cola no está vacío. Este método es seguro para simultaneidad.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_priority_queue` a este. Este método no es seguro para la simultaneidad.|

## <a name="remarks"></a>Comentarios

Para obtener información detallada sobre la `concurrent_priority_queue` de clases, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`concurrent_priority_queue`

## <a name="requirements"></a>Requisitos

**Encabezado:** concurrent_priority_queue.h

**Espacio de nombres:** simultaneidad

##  <a name="clear"></a> Borrar

Borra todos los elementos en la prioridad simultánea. Este método no es seguro para la simultaneidad.

```
void clear();
```

### <a name="remarks"></a>Comentarios

`clear` no es seguro para simultaneidad. Debe asegurarse de que ningún otro subproceso invoca métodos en la cola de prioridad simultáneas cuando se llama a este método. `clear` no libera memoria.

##  <a name="ctor"></a> concurrent_priority_queue)

Construye una cola de prioridad simultáneas.

```
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

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un objeto de asignador `_Al` e inicializar la cola de prioridad.

El primer constructor especifica una cola de prioridad inicial vacío y, opcionalmente, especifica un asignador.

El segundo constructor especifica una cola de prioridad con una capacidad inicial `_Init_capacity` y, opcionalmente, especifica un asignador.

El tercer constructor especifica los valores proporcionados por el rango de iterador [ `_Begin`, `_End`) y, opcionalmente, especifica un asignador.

Los constructores cuarto y quinto especifican una copia de la cola de prioridad `_Src`.

Los constructores sexto y séptimo especifican un movimiento de la cola de prioridad `_Src`.

##  <a name="empty"></a> vacío

Comprueba si la cola de prioridad simultáneas está vacía en el momento en que se llama a este método. Este método es seguro para simultaneidad.

```
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si la cola de prioridad estaba vacía en el momento en que se llamó a la función, **false** en caso contrario.

##  <a name="get_allocator"></a> get_allocator

Devuelve una copia del asignador usado para construir la cola de prioridad simultáneas. Este método es seguro para simultaneidad.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Una copia de asignador usado para construir el `concurrent_priority_queue` objeto.

##  <a name="operator_eq"></a> operator=

Asigna el contenido de otro objeto `concurrent_priority_queue` a este. Este método no es seguro para la simultaneidad.

```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
Objeto `concurrent_priority_queue` de origen.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `concurrent_priority_queue` objeto.

##  <a name="push"></a> inserción

Agrega un elemento a la cola de prioridad simultáneas. Este método es seguro para simultaneidad.

```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Parámetros

*_Elem*<br/>
El elemento que se agregarán a la cola de prioridad simultáneas.

##  <a name="size"></a> Tamaño

Devuelve el número de elementos en la cola de prioridad simultáneas. Este método es seguro para simultaneidad.

```
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en este `concurrent_priority_queue` objeto.

### <a name="remarks"></a>Comentarios

Se garantiza que el tamaño devuelto para incluir todos los elementos agregados mediante llamadas a la función `push`. Sin embargo, no pueden reflejar los resultados de las operaciones simultáneas pendientes.

##  <a name="swap"></a> intercambio

Intercambia el contenido de dos colas de prioridad simultáneas. Este método no es seguro para la simultaneidad.

```
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Parámetros

*_Queue*<br/>
La `concurrent_priority_queue` objeto que se va a intercambiar el contenido.

##  <a name="try_pop"></a> try_pop

Quita y devuelve el elemento de prioridad más alto de la cola si la cola no está vacío. Este método es seguro para simultaneidad.

```
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Parámetros

*_Elem*<br/>
Una referencia a una variable que se rellenará con el elemento de prioridad más alta, si la cola no está vacío.

### <a name="return-value"></a>Valor devuelto

**True** si se extrae un valor, **false** en caso contrario.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)
