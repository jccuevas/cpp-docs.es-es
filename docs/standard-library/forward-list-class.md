---
title: forward_list (Clase)
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.openlocfilehash: f1015e53e137b9001bd90233c281345d474bc03f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689697"
---
# <a name="forward_list-class"></a>forward_list (Clase)

Describe un objeto que controla una secuencia de elementos de longitud variable. La secuencia se almacena como una lista de nodos vinculada individualmente, cada uno de los cuales contiene un miembro de tipo `Type`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>Parámetros

Escriba * \
Tipo de datos de elemento que se almacenará en forward_list.

@No__t_1 de *asignador*
Objeto de asignador almacenado que encapsula detalles sobre la asignación y desasignación de memoria de forward_list. Este parámetro es opcional. El valor predeterminado es allocator<`Type`>.

## <a name="remarks"></a>Comentarios

Un objeto `forward_list` asigna y libera almacenamiento para la secuencia que controla a través de un objeto almacenado de clase *allocator* que se basa en la [clase allocator](../standard-library/allocator-class.md) (conocida comúnmente como `std::allocator)`. Para obtener más información, vea [Asignadores](../standard-library/allocators.md). Un objeto de asignador debe tener la misma interfaz externa que un objeto de tipo `allocator`.

> [!NOTE]
> El objeto de asignador almacenado no se copia cuando se asigna el objeto contenedor.

Los iteradores, punteros y referencias pueden llegar a no ser válidos cuando los elementos de su secuencia controlada se borran mediante `forward_list`. Las inserciones y uniones realizados en la secuencia controlada mediante `forward_list` no invalidan los iteradores.

Las adiciones a la secuencia controlada pueden realizarse mediante llamadas a [forward_list::insert_after](#insert_after), que es la única función miembro que llama al constructor `Type(const  T&)`. `forward_list` también puede llamar a constructores de movimiento. Si una expresión de ese tipo produce una excepción, el objeto contenedor no inserta ningún elemento nuevo y vuelve a producir la excepción. Por lo tanto, un objeto de tipo `forward_list` se deja en un estado conocido cuando se producen esas excepciones.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[forward_list](#forward_list)|Construye un objeto de tipo `forward_list`.|

### <a name="typedefs"></a>Definiciones de tipo

|||
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase de asignador de un objeto de lista de reenvíos.|
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador constante para la lista de reenvíos.|
|[const_pointer](#const_pointer)|Un tipo que proporciona un puntero a un elemento **const** de una lista de reenvíos.|
|[const_reference](#const_reference)|Tipo que proporciona una referencia constante a un elemento de la lista de reenvíos.|
|[difference_type](#difference_type)|Tipo entero con signo que se puede usar para representar el número de elementos de una lista de reenvíos en un intervalo entre elementos a los que apuntan los iteradores.|
|[iterator](#iterator)|Tipo que proporciona un iterador para la lista de reenvíos.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de la lista de reenvíos.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento de la lista de reenvíos.|
|[size_type](#size_type)|Tipo que representa la distancia sin signo entre dos elementos.|
|[value_type](#value_type)|Tipo que representa el tipo de elemento almacenado en una lista de reenvíos.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[assign](#assign)|Borra elementos de una lista de reenvíos y copia un nuevo conjunto de elementos a una lista de reenvíos de destino.|
|[before_begin](#before_begin)|Devuelve un iterador que direcciona la posición anterior al primer elemento de una lista de reenvíos.|
|[begin](#begin)|Devuelve un iterador que direcciona el primer elemento de una lista de reenvíos.|
|[cbefore_begin](#cbefore_begin)|Devuelve un iterador const que direcciona la posición anterior al primer elemento de una lista de reenvíos.|
|[cbegin](#cbegin)|Devuelve un iterador const que direcciona el primer elemento de una lista de reenvíos.|
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de una lista de reenvíos.|
|[clear](#clear)|Borra todos los elementos de una lista de reenvíos.|
|[emplace_after](#emplace_after)|Construye con movimiento un nuevo elemento después de una posición especificada.|
|[emplace_front](#emplace_front)|Agrega un elemento construido al principio de la lista.|
|[empty](#empty)|Comprueba si una lista de reenvíos está vacía.|
|[end](#end)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de una lista de reenvíos.|
|[erase_after](#erase_after)|Quita de la lista de reenvíos los elementos situados después de una posición especificada.|
|[front](#front)|Devuelve una referencia al primer elemento de una lista de reenvíos.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto de asignador utilizado para construir una lista de reenvíos.|
|[insert_after](#insert_after)|Agrega elementos a la lista de reenvíos después de una posición especificada.|
|[max_size](#max_size)|Devuelve la longitud máxima de una lista de reenvíos.|
|[merge](#merge)|Quita los elementos de la lista de argumentos, los inserta en la lista de reenvíos de destino y ordena el nuevo conjunto combinado de elementos en orden ascendente o en otro orden especificado.|
|[pop_front](#pop_front)|Elimina el elemento situado al principio de una lista de reenvíos.|
|[push_front](#push_front)|Agrega un elemento al principio de una lista de reenvíos.|
|[remove](#remove)|Borra elementos de una lista de reenvíos que coincide con un valor especificado.|
|[remove_if](#remove_if)|Borra elementos de una lista de reenvíos para la que se cumple el predicado especificado.|
|[resize](#resize)|Especifica un nuevo tamaño de una lista de reenvíos.|
|[reverse](#reverse)|Invierte el orden en que aparecen los elementos en una lista de reenvíos.|
|[sort](#sort)|Organiza los elementos en orden ascendente o con un orden especificado por un predicado.|
|[splice_after](#splice_after)|Vuelve a unir vínculos entre nodos.|
|[swap](#swap)|Intercambia los elementos de dos listas de reenvío.|
|[unique](#unique)|Quita los elementos adyacentes que superan una prueba especificada.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator=](#op_eq)|Reemplaza los elementos de la lista de reenvíos con una copia de otra lista de reenvíos.|

## <a name="allocator_type"></a>allocator_type

Tipo que representa la clase de asignador de un objeto de lista de reenvíos.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Comentarios

`allocator_type` es un sinónimo del parámetro de plantilla Allocator.

## <a name="assign"></a>quitar

Borra elementos de una lista de reenvíos y copia un nuevo conjunto de elementos a una lista de reenvíos de destino.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parámetros

*primer* \
Principio del intervalo de reemplazo.

*última* \
Final del intervalo de reemplazo.

*recuento* \
Número de elementos que se van a asignar.

\ *Val*
Valor que se va a asignar a cada elemento.

*Escribir* \
Tipo del valor.

*IList* \
initializer_list que se va a copiar.

### <a name="remarks"></a>Comentarios

Si forward_list es un tipo entero, la primera función miembro tiene el mismo comportamiento que `assign((size_type)First, (Type)Last)`. De lo contrario, la primera función miembro reemplaza la secuencia controlada por `*this` con la secuencia [ `First, Last)`, que no debe superponerse a la secuencia controlada inicial.

La segunda función miembro reemplaza la secuencia controlada por `*this` con una repetición de `Count` elementos de valor `Val`.

La tercera función miembro copia los elementos de initializer_list a forward_list.

## <a name="before_begin"></a>before_begin

Devuelve un iterador que direcciona la posición anterior al primer elemento de una lista de reenvíos.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Valor devuelto

Un iterador hacia delante que apunta inmediatamente antes del primer elemento de la secuencia (o inmediatamente antes del final de una secuencia vacía).

### <a name="remarks"></a>Comentarios

## <a name="begin"></a>inicia

Devuelve un iterador que direcciona el primer elemento de una lista de reenvíos.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Un iterador hacia delante que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía).

### <a name="remarks"></a>Comentarios

## <a name="cbefore_begin"></a>cbefore_begin

Devuelve un iterador const que direcciona la posición anterior al primer elemento de una lista de reenvíos.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador hacia delante que apunta inmediatamente antes del primer elemento de la secuencia (o inmediatamente antes del final de una secuencia vacía).

### <a name="remarks"></a>Comentarios

## <a name="cbegin"></a>cbegin (

Devuelve un iterador **const** que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador de acceso hacia delante **constante** que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere `Container` ser un contenedor modificable (no **const**) de cualquier tipo que admita `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Devuelve un iterador **const** que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador hacia delante que apunta justo después del final del intervalo.

### <a name="remarks"></a>Comentarios

`cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere `Container` ser un contenedor modificable (no **const**) de cualquier tipo que admita `end()` y `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="clear"></a>claridad

Borra todos los elementos de una lista de reenvíos.

```cpp
void clear();
```

### <a name="remarks"></a>Comentarios

La función miembro llama a `erase_after(before_begin(), end()).`.

## <a name="const_iterator"></a>const_iterator

Tipo que proporciona un iterador constante para la lista de reenvíos.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Comentarios

`const_iterator` describe un objeto que puede actuar como un iterador de avance constante de la secuencia controlada. Aquí se describe como sinónimo de un tipo definido por implementación.

## <a name="const_pointer"></a>const_pointer

Un tipo que proporciona un puntero a un elemento **const** de una lista de reenvíos.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Comentarios

## <a name="const_reference"></a>const_reference

Tipo que proporciona una referencia constante a un elemento de la lista de reenvíos.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Comentarios

## <a name="difference_type"></a>difference_type

Tipo entero con signo que se puede usar para representar el número de elementos de una lista de reenvíos en un intervalo entre elementos a los que apuntan los iteradores.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Comentarios

`difference_type` describe un objeto que puede representar la diferencia entre las direcciones de dos elementos cualesquiera de la secuencia controlada.

## <a name="emplace_after"></a>emplace_after

Construye con movimiento un nuevo elemento después de una posición especificada.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Parámetros

*Dónde* \
Posición de la lista de reenvíos de destino donde se crea el nuevo elemento.

\ *Val*
El argumento del constructor.

### <a name="return-value"></a>Valor devuelto

Iterador que designa al elemento recién insertado.

### <a name="remarks"></a>Comentarios

Esta función miembro inserta un elemento con los argumentos de constructor *Val* justo después del elemento *al que apunta en la* secuencia controlada. De lo contrario, su comportamiento es el mismo que [forward_list::insert_after](#insert_after).

## <a name="emplace_front"></a>emplace_front

Agrega un elemento construido al principio de la lista.

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parámetros

\ *Val*
El elemento que se agrega al principio de la lista de reenvíos.

### <a name="remarks"></a>Comentarios

Esta función miembro inserta un elemento con los argumentos de constructor `_ val` al final de la secuencia controlada.

Si se inicia una excepción, el contenedor se deja sin modificar y se vuelve a iniciar la excepción.

## <a name="empty"></a>vacía

Comprueba si una lista de reenvíos está vacía.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si la lista de reenvíos está vacía; en caso contrario, **false**.

## <a name="end"></a>extremo

Devuelve un iterador que direcciona la ubicación que sigue al último elemento de una lista de reenvíos.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Valor devuelto

Un iterador hacia delante que apunta inmediatamente después del final de la secuencia.

## <a name="erase_after"></a>erase_after

Quita de la lista de reenvíos los elementos situados después de una posición especificada.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Parámetros

*Dónde* \
Posición de la lista de reenvíos de destino donde se borra el elemento.

*primer* \
Comienzo del intervalo que se va a borrar.

*última* \
Final del intervalo que se va a borrar.

### <a name="return-value"></a>Valor devuelto

Un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o [forward_list::end](#end) si no existe ese elemento.

### <a name="remarks"></a>Comentarios

La primera función miembro quita el elemento de la secuencia controlada justo después de *Where*.

La segunda función miembro quita los elementos de la secuencia controlada en el intervalo `( first,  last)` (no se incluye ningún extremo).

Al borrar `N` elementos, se producen `N` llamadas de destructor. Se produce una [reasignación](../standard-library/forward-list-class.md), de modo que los iteradores y las referencias dejan de ser válidos para los elementos borrados.

Las funciones miembro nunca producen una excepción.

## <a name="forward_list"></a>forward_list

Construye un objeto de tipo `forward_list`.

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

*Al* \
La clase de asignador que se usa con este objeto.

*Recuento* \
Número de elementos de la lista construida.

@No__t_1 *Val*
Valor de los elementos de la lista construida.

@No__t_1 *derecha*
Lista de la que la lista construida va a ser una copia.

*Primer* \
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*Última* \
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

*IList* \
initializer_list que se va a copiar.

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un [asignador](../standard-library/allocator-class.md) e inicializan la secuencia controlada. El objeto de asignador es el argumento *al*, si está presente. Para el constructor de copias, es ` right.get_allocator()`. De lo contrario, es `Allocator()`.

Los dos primeros constructores especifican una secuencia controlada inicial vacía.

El tercer constructor especifica una repetición de elementos de *recuento* de valores `Type()`.

Los constructores cuarto y quinto especifican una repetición de elementos de *recuento* de valor *Val*.

El sexto constructor especifica una copia de la secuencia controlada por la *derecha*. Si `InputIterator` es un tipo entero, los dos constructores siguientes especifican una repetición de elementos `(size_type)First` de valor `(Type)Last`. De lo contrario, los dos constructores siguientes especifican la secuencia `[First, Last)`.

Los constructores noveno y décimo son iguales que el sexto, pero con una referencia [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

El último constructor especifica la secuencia controlada inicial con un objeto de clase `initializer_list<Type>`.

## <a name="front"></a>end

Devuelve una referencia al primer elemento de una lista de reenvíos.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al primer elemento de la secuencia controlada, que no debe estar vacío.

## <a name="get_allocator"></a>get_allocator

Devuelve una copia del objeto de asignador utilizado para construir una lista de reenvíos.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El objeto de [asignador](../standard-library/allocator-class.md) almacenado.

## <a name="insert_after"></a>insert_after

Agrega elementos a la lista de reenvíos después de una posición especificada.

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parámetros

*Dónde* \
Posición de la lista de reenvíos de destino donde se inserta el primer elemento.

*Recuento* \
Número de elementos que se van a insertar.

*Primer* \
Principio del intervalo de inserción.

*Última* \
Final del intervalo de inserción.

@No__t_1 *Val*
Elemento agregado a la lista de reenvíos.

*IList* \
initializer_list que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Iterador que designa el elemento recién insertado (primera y última funciones miembro solamente).

### <a name="remarks"></a>Comentarios

Cada una de las funciones miembro inserta, justo después del elemento *al que apunta en la* secuencia controlada, una secuencia especificada por los operandos restantes.

La primera función miembro inserta un elemento que tiene el valor *Val* y devuelve un iterador que designa el elemento recién insertado.

La segunda función miembro inserta una repetición de elementos *Count* de Value *Val*.

Si `InputIterator` es un tipo entero, la tercera función miembro se comporta igual que `insert(it, (size_type)First, (Type)Last)`. De lo contrario, inserta la secuencia `[First, Last)`, que no se debe superponer a la secuencia controlada inicial.

La cuarta función miembro inserta la secuencia especificada por un objeto de clase `initializer_list<Type>`.

La última función miembro es igual que la primera, pero con una referencia [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

La inserción de `N` elementos produce `N` llamadas de constructor. Se realiza una [reasignación](../standard-library/forward-list-class.md), pero los iteradores o las referencias no dejan de ser válidos.

Si se produce una excepción durante la inserción de uno o más elementos, el contenedor permanece inalterado y se vuelve a producir la excepción.

## <a name="iterator"></a>apunta

Tipo que proporciona un iterador para la lista de reenvíos.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Comentarios

`iterator` describe un objeto que puede actuar como un iterador de avance de la secuencia controlada. Aquí se describe como sinónimo de un tipo definido por implementación.

## <a name="max_size"></a>max_size

Devuelve la longitud máxima de una lista de reenvíos.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud de la secuencia más larga que puede controlar el objeto.

### <a name="remarks"></a>Comentarios

## <a name="merge"></a>sin

Combina dos secuencias ordenadas en una única secuencia ordenada en tiempo lineal. Quita los elementos de la lista de argumentos y los inserta en esta `forward_list`. Las dos listas deben ordenarse por el mismo objeto de función de comparación antes de llamar a `merge`. La lista combinada se ordenará por ese objeto de función de comparación.

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
La lista de reenvíos desde la que se combinará.

\ *COMP*
El objeto de función de comparación que se usa para ordenar elementos.

### <a name="remarks"></a>Comentarios

`forward_list::merge` quita los elementos del `right` de `forward_list` y los inserta en este `forward_list`. Ambas secuencias deben estar ordenadas por el mismo predicado, que se describe a continuación. La secuencia combinada también está ordenada por ese objeto de función de comparación.

Para los iteradores `Pi` y `Pj` que designan elementos en posiciones `i` y `j`, la primera función miembro impone el orden `!(*Pj < *Pi)` siempre que `i < j`. (Los elementos se ordenan en `ascending` orden). La segunda función miembro impone el orden `! comp(*Pj, *Pi)` cada vez que `i < j`.

Ningún par de elementos de la secuencia controlada original se invierte en la secuencia controlada resultante. Si un par de elementos de la secuencia controlada resultante equivale a (`!(*Pi < *Pj) && !(*Pj < *Pi)`), un elemento de la secuencia controlada original aparece antes de un elemento de la secuencia controlada por `right`.

Se produce una excepción solo si `comp` inicia una excepción. En ese caso, la secuencia controlada se deja en un orden no especificado y se vuelve a iniciar la excepción.

## <a name="op_eq"></a>operador =

Reemplaza los elementos de la lista de reenvíos con una copia de otra lista de reenvíos.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
La lista de reenvíos que se copia en la lista de reenvíos.

*IList* \
Una lista de inicializador entre llaves, que se comporta como una secuencia de elementos de tipo `Type`.

### <a name="remarks"></a>Comentarios

El primer operador miembro reemplaza la secuencia controlada por una copia de la secuencia controlada por la *derecha*.

El segundo operador miembro reemplaza la secuencia controlada a partir de un objeto de clase `initializer_list<Type>`.

El tercer operador miembro es igual que el primero, pero con una referencia [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="pointer"></a>puntero

Tipo que proporciona un puntero a un elemento de la lista de reenvíos.

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a>pop_front

Elimina el elemento situado al principio de una lista de reenvíos.

```cpp
void pop_front();
```

### <a name="remarks"></a>Comentarios

El primer elemento de la lista de reenvíos no puede estar vacío.

Las funciones miembro nunca lanzan una excepción.

## <a name="push_front"></a>push_front

Agrega un elemento al principio de una lista de reenvíos.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parámetros

\ *Val*
El elemento que se agrega al principio de la lista de reenvíos.

### <a name="remarks"></a>Comentarios

Si se inicia una excepción, el contenedor se deja sin modificar y se vuelve a iniciar la excepción.

## <a name="reference"></a>referencia

Tipo que proporciona una referencia a un elemento de la lista de reenvíos.

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a>retirar

Borra elementos de una lista de reenvíos que coincide con un valor especificado.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parámetros

\ *Val*
Valor que, si lo contiene un elemento, hará que se quite ese elemento de la lista.

### <a name="remarks"></a>Comentarios

La función miembro quita de la secuencia controlada todos los elementos, designados por el iterador `P`, para el que `*P ==  val`.

Las funciones miembro nunca lanzan una excepción.

## <a name="remove_if"></a>remove_if

Borra elementos de una lista de reenvíos para la que se cumple el predicado especificado.

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>Parámetros

*pred* \
Predicado unario que, si lo satisface un elemento, da lugar a la eliminación de ese elemento de la lista.

### <a name="remarks"></a>Comentarios

La función miembro quita de la secuencia controlada todos los elementos, designados por el iterador `P`, para el que ` pred(*P)` es True.

Solo se produce una excepción si *Pred* produce una excepción. En ese caso, la secuencia controlada se deja en un estado no especificado y se vuelve a iniciar la excepción.

## <a name="resize"></a>cambiar el tamaño

Especifica un nuevo tamaño de una lista de reenvíos.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Newsize*
Número de elementos de la lista de reenvíos a la que se le ha cambiado el tamaño.

\ *Val*
Valor que se va a usar para el relleno.

### <a name="remarks"></a>Comentarios

Las funciones miembro garantizan que el número de elementos de la lista es *_Newsize*. Si debe hacer que la secuencia controlada sea más larga, la primera función miembro anexa elementos con el valor `Type()`, mientras que la segunda función miembro anexa elementos con el valor *Val*. Para que la secuencia controlada sea más corta, ambas funciones miembro llaman de forma eficaz a `erase_after(begin() + _Newsize - 1, end())`.

## <a name="reverse"></a>viceversa

Invierte el orden en que aparecen los elementos en una lista de reenvíos.

```cpp
void reverse();
```

## <a name="size_type"></a>size_type

Tipo que representa la distancia sin signo entre dos elementos.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Comentarios

El tipo de entero sin signo describe un objeto que puede representar la longitud de cualquier secuencia controlada.

## <a name="sort"></a>clasificación

Organiza los elementos en orden ascendente o con un orden especificado por un predicado.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Parámetros

*pred* \
El predicado de ordenación.

### <a name="remarks"></a>Comentarios

Ambas funciones miembro ordenan los elementos de la secuencia controlada por un predicado, que se describe a continuación.

Para los iteradores `Pi` y `Pj` que designan elementos en posiciones `i` y `j`, la primera función miembro impone el orden `!(*Pj < *Pi)` siempre que `i < j`. (Los elementos se ordenan en `ascending` orden). La función de plantilla miembro impone el orden `! pred(*Pj, *Pi)` cada vez que `i < j`. Ningún par ordenado de elementos de la secuencia controlada original se invierte en la secuencia controlada resultante. (El criterio de ordenación es estable).

Solo se produce una excepción si *Pred* produce una excepción. En ese caso, la secuencia controlada se deja en un orden no especificado y se vuelve a iniciar la excepción.

## <a name="splice_after"></a>splice_after

Quita elementos de una forward_list de origen y los inserta en una forward_list de destino.

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>Parámetros

*Dónde* \
La posición de la forward_list de destino después de la cual se insertan.

*Source*\
La forward_list de origen que debe insertarse en la forward_list de destino.

@No__t_1 *ITER*
El elemento que debe insertarse de la forward_list de origen.

*Primer* \
El elemento del intervalo que debe insertarse de la forward_list de origen.

*Última* \
La primera posición de después del intervalo que debe insertarse de la forward_list de origen.

### <a name="remarks"></a>Comentarios

El primer par de funciones miembro inserta la secuencia controlada por el *origen* justo después del elemento en la secuencia controlada a *la que apunta.* También quita todos los elementos del *origen*. (`&Source` no **debe ser igual**que).

El segundo par de funciones miembro quita el elemento justo después del *ITER* en la secuencia controlada por el *origen* y lo inserta justo después del elemento en la secuencia controlada a la *que apunta.* (Si `Where == Iter || Where == ++Iter`, no ocurre ningún cambio.)

El tercer par de funciones miembro (empalme de intervalo) inserta el subintervalo designado por `(First, Last)` de la secuencia controlada por el *origen* justo después del elemento de la secuencia controlada apuntado por, *donde*. También quita el subintervalo original de la secuencia controlada por el *origen*. (Si `&Source == this`, el intervalo `(First, Last)` no debe incluir el elemento al que apunta *Where*).

Si la unión del intervalo inserta `N` elementos y `&Source != this`, un objeto de clase [iterator](#iterator) se incrementa `N` veces.

Ningún iterador, puntero ni referencia que designe elementos insertados deja de ser válido.

### <a name="example"></a>Ejemplo

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a>pasar

Intercambia los elementos de dos listas de reenvío.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
La lista de reenvíos que proporciona los elementos que se van a intercambiar.

### <a name="remarks"></a>Comentarios

La función miembro intercambia las secuencias controladas entre `*this` y *right*. Si `get_allocator() ==  right.get_allocator()`, lo hace en tiempo constante, no inicia ninguna excepción y no invalida ninguna referencia, puntero o iterador que designen elementos en las dos secuencias controladas. De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.

## <a name="unique"></a>espeficarse

Elimina todo menos el primer elemento de cada grupo consecutivo de elementos iguales.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Parámetros

\ *COMP*
El predicado binario que se usa para comparar los elementos sucesivos.

### <a name="remarks"></a>Comentarios

Mantiene el primero de cada elemento único y elimina el resto. Los elementos deben estar ordenados para que los elementos del mismo valor sean adyacentes en la lista.

La primera función miembro quita de la secuencia controlada todos los elementos que equivalen al elemento anterior. Para los iteradores `Pi` y `Pj` que designan elementos en posiciones `i` y `j`, la segunda función miembro quita todos los elementos para los que `i + 1 == j &&  comp(*Pi, *Pj)`.

Para una secuencia controlada de longitud `N` (> 0), el predicado ` comp(*Pi, *Pj)` se evalúa `N - 1` veces.

Se produce una excepción solo si `comp` inicia una excepción. En ese caso, la secuencia controlada se deja en un estado no especificado y se vuelve a iniciar la excepción.

## <a name="value_type"></a>value_type

Tipo que representa el tipo de elemento almacenado en una lista de reenvíos.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla _ `Ty`.
