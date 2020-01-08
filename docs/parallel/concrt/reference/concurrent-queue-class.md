---
title: concurrent_queue (clase)
ms.date: 11/04/2016
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: 7f87ead486d635c933ad356f9868c22344601eda
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298628"
---
# <a name="concurrent_queue-class"></a>concurrent_queue (clase)

La clase `concurrent_queue` es una clase de contenedor de secuencias que permite el acceso primero en entrar, primero en salir a sus elementos. Habilita un conjunto limitado de operaciones seguras para simultaneidad, como `push` y `try_pop`. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado.

## <a name="syntax"></a>Sintaxis

```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

#### <a name="parameters"></a>Parameters

*T*<br/>
Tipo de datos de los elementos que se van a almacenar en la cola.

*_Ax*<br/>
Tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre la asignación y desasignación de memoria para esta cola simultánea. Este argumento es opcional y el valor predeterminado es `allocator<T>`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Typedefs públicos

|Name|Descripción|
|----------|-----------------|
|`allocator_type`|Tipo que representa la clase de asignador para la cola simultánea.|
|`const_iterator`|Tipo que representa un iterador `const` no seguro para subprocesos sobre los elementos de una cola simultánea.|
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en una cola simultánea para leer y realizar operaciones de `const`.|
|`difference_type`|Un tipo que proporciona la distancia con signo entre dos elementos de una cola simultánea.|
|`iterator`|Tipo que representa un iterador no seguro para subprocesos sobre los elementos de una cola simultánea.|
|`reference`|Un tipo que proporciona una referencia a un elemento almacenado en una cola simultánea.|
|`size_type`|Tipo que cuenta el número de elementos de una cola simultánea.|
|`value_type`|Tipo que representa el tipo de datos almacenado en una cola simultánea.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[concurrent_queue](#ctor)|Sobrecargado. Construye una cola simultánea.|
|[~ concurrent_queue destructor](#dtor)|Destruye la cola simultánea.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[clear](#clear)|Borra la cola simultánea, destruyendo todos los elementos actualmente puestos en cola. Este método no es seguro para la simultaneidad.|
|[empty](#empty)|Comprueba si la cola simultánea está vacía en el momento en que se llama a este método. Este método es seguro para simultaneidad.|
|[get_allocator](#get_allocator)|Devuelve una copia del asignador utilizado para construir la cola simultánea. Este método es seguro para simultaneidad.|
|[push](#push)|Sobrecargado. Pone en cola un elemento al final de la cola simultánea. Este método es seguro para simultaneidad.|
|[try_pop](#try_pop)|Quita de la cola un elemento de la cola si hay alguno disponible. Este método es seguro para simultaneidad.|
|[unsafe_begin](#unsafe_begin)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al principio de la cola simultánea. Este método no es seguro para la simultaneidad.|
|[unsafe_end](#unsafe_end)|Sobrecargado. Devuelve un iterador de tipo `iterator` o `const_iterator` al final de la cola simultánea. Este método no es seguro para la simultaneidad.|
|[unsafe_size](#unsafe_size)|Devuelve el número de elementos de la cola. Este método no es seguro para la simultaneidad.|

## <a name="remarks"></a>Notas

Para obtener más información, consulte [Parallel containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`concurrent_queue`

## <a name="requirements"></a>Requisitos de

**Encabezado:** concurrent_queue. h

**Espacio de nombres:** simultaneidad

##  <a name="clear"></a>claridad

Borra la cola simultánea, destruyendo todos los elementos actualmente puestos en cola. Este método no es seguro para la simultaneidad.

```
void clear();
```

##  <a name="ctor"></a>concurrent_queue

Construye una cola simultánea.

```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parameters

*_InputIterator*<br/>
Tipo del iterador de entrada que especifica un intervalo de valores.

*_Al*<br/>
La clase de asignador que se usa con este objeto.

*_OtherQ*<br/>
El objeto de origen `concurrent_queue` del que copiar o mover elementos.

*_Begin*<br/>
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*_End*<br/>
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

### <a name="remarks"></a>Notas

Todos los constructores almacenan un objeto de asignador `_Al` e inicializan la cola.

El primer constructor especifica una cola inicial vacía y especifica explícitamente el tipo de asignador que se va a usar.

El segundo constructor especifica una copia de la cola simultánea `_OtherQ`.

El tercer constructor especifica un movimiento del `_OtherQ`simultáneo de la cola.

El cuarto constructor especifica los valores proporcionados por el intervalo de iterador [`_Begin`, `_End`).

##  <a name="dtor"></a> ~concurrent_queue

Destruye la cola simultánea.

```
~concurrent_queue();
```

##  <a name="empty"></a>vacía

Comprueba si la cola simultánea está vacía en el momento en que se llama a este método. Este método es seguro para simultaneidad.

```
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si la cola simultánea estaba vacía en el momento en que se buscó; de lo contrario, **false** .

### <a name="remarks"></a>Notas

Aunque este método es seguro para simultaneidad con respecto a las llamadas a los métodos `push`, `try_pop`y `empty`, el valor devuelto puede ser incorrecto en el momento en que lo inspecciona el subproceso que realiza la llamada.

##  <a name="get_allocator"></a> get_allocator

Devuelve una copia del asignador utilizado para construir la cola simultánea. Este método es seguro para simultaneidad.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Una copia del asignador utilizado para construir la cola simultánea.

##  <a name="push"></a>enviar

Pone en cola un elemento al final de la cola simultánea. Este método es seguro para simultaneidad.

```
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>Parameters

*_Src*<br/>
Elemento que se va a agregar a la cola.

### <a name="remarks"></a>Notas

`push` es seguro para simultaneidad con respecto a las llamadas a los métodos `push`, `try_pop`y `empty`.

##  <a name="try_pop"></a>try_pop

Quita de la cola un elemento de la cola si hay alguno disponible. Este método es seguro para simultaneidad.

```
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>Parameters

*_Dest*<br/>
Referencia a una ubicación en la que se va a almacenar el elemento quitado de la cola.

### <a name="return-value"></a>Valor devuelto

**true** si un elemento se quitó correctamente de la cola, **false** en caso contrario.

### <a name="remarks"></a>Notas

Si un elemento se quitó correctamente de la cola, el parámetro `_Dest` recibe el valor quitado de la cola, el valor original mantenido en la cola se destruye y esta función devuelve **true**. Si no hay ningún elemento para quitar de la cola, esta función devuelve `false` sin bloquearse y el contenido del parámetro `_Dest` no está definido.

`try_pop` es seguro para simultaneidad con respecto a las llamadas a los métodos `push`, `try_pop`y `empty`.

##  <a name="unsafe_begin"></a>unsafe_begin

Devuelve un iterador de tipo `iterator` o `const_iterator` al principio de la cola simultánea. Este método no es seguro para la simultaneidad.

```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `iterator` o `const_iterator` al principio del objeto de cola simultáneo.

### <a name="remarks"></a>Notas

Los iteradores de la clase `concurrent_queue` están pensados principalmente para la depuración, ya que son lentos, y la iteración no es segura para simultaneidad con respecto a otras operaciones de cola.

##  <a name="unsafe_end"></a>unsafe_end

Devuelve un iterador de tipo `iterator` o `const_iterator` al final de la cola simultánea. Este método no es seguro para la simultaneidad.

```
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de tipo `iterator` o `const_iterator` al final de la cola simultánea.

### <a name="remarks"></a>Notas

Los iteradores de la clase `concurrent_queue` están pensados principalmente para la depuración, ya que son lentos, y la iteración no es segura para simultaneidad con respecto a otras operaciones de cola.

##  <a name="unsafe_size"></a>unsafe_size

Devuelve el número de elementos de la cola. Este método no es seguro para la simultaneidad.

```
size_type unsafe_size() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño de la cola simultánea.

### <a name="remarks"></a>Notas

`unsafe_size` no es seguro para simultaneidad y puede producir resultados incorrectos si se llama a la vez con llamadas a los métodos `push`, `try_pop`y `empty`.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
