---
title: move_iterator (Clase)
ms.date: 03/27/2019
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
ms.openlocfilehash: 17af246a85c4e3f1e0c7eb9d387161ad7b5123a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377418"
---
# <a name="move_iterator-class"></a>move_iterator (Clase)

La plantilla de clase `move_iterator` es un contenedor para un iterador. La plantilla move_iterator ofrece el mismo comportamiento que el iterador que contiene (almacena), con la excepción de que cambia el operador de desreferencia por una referencia rvalue y convierte una copia en un movimiento. Para obtener más información sobre rvalues, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Sintaxis

```cpp
class move_iterator;
```

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que se comporta como un iterador, excepto cuando se desreferencia. Almacena un iterador de acceso aleatorio de tipo `Iterator`, al que se tiene acceso mediante la función miembro `base()`. Todas las operaciones de `move_iterator` se realizan directamente en el iterador almacenado, con la excepción de que el resultado de `operator*` se convierte implícitamente en `value_type&&` para crear una referencia rvalue.

Un `move_iterator` puede llevar a cabo operaciones no definidas por el iterador contenedor. Estas operaciones no se deben usar.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[move_iterator](#move_iterator)|Constructor para los objetos de tipo `move_iterator`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[iterator_type](#iterator_type)|Sinónimo del parámetro de plantilla `RandomIterator`.|
|[iterator_category](#iterator_category)|Un sinónimo de una expresión de nombre `iterator_category` de **tipo** más largo del mismo nombre, identifica las capacidades generales del iterador.|
|[value_type](#value_type)|Un sinónimo de una expresión de nombre `value_type` de **tipo** más largo del mismo nombre, describe qué tipo son los elementos de iterador.|
|[difference_type](#difference_type)|Un sinónimo de una expresión de nombre `difference_type` de **tipo** más largo del mismo nombre, describe el tipo entero necesario para expresar valores de diferencia entre los elementos.|
|[puntero](#pointer)|Sinónimo del parámetro de plantilla `RandomIterator`.|
|[Referencia](#reference)|Sinónimo de la referencia `rvalue``value_type&&`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[base](#base)|La función miembro devuelve el iterador almacenado contenido en este `move_iterator`.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[move_iterator::operador*](#op_star)|Devuelve `(reference)*base().`|
|[move_iterator::operador++](#op_add_add)|Incrementa el iterador almacenado. El comportamiento exacto depende de si se trata de una operación de incremento previo o posterior.|
|[move_iterator::operator--](#operator--)|Disminuye el iterador almacenado. El comportamiento exacto depende de si se trata de una operación de disminución previa o posterior.|
|[move_iterator::operador-&gt;](#op_arrow)|Devuelve `&**this`.|
|[move_iterator::operador-](#operator-)|Devuelve `move_iterator(*this) -=` restando primero el valor situado a la derecha de la posición actual.|
|[move_iterator::operador[]](#op_at)|Devuelve `(reference)*(*this + off)`. Permite especificar una posición de desplazamiento a partir de la base actual para obtener el valor que se encuentra en esa ubicación.|
|[move_iterator::operador+](#op_add)|Devuelve el valor `move_iterator(*this) +=`. Permite agregar una posición de desplazamiento a la base para obtener el valor que se encuentra en esa ubicación.|
|[move_iterator::operador+o](#op_add_eq)|Agrega el valor situado a la derecha del iterador almacenado y devuelve `*this`.|
|[move_iterator::operador-o](#operator-_eq)|Resta el valor situado a la derecha del iterador almacenado y devuelve `*this`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="move_iteratorbase"></a><a name="base"></a>move_iterator::base

Devuelve el iterador almacenado para este `move_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el iterador almacenado.

## <a name="move_iteratordifference_type"></a><a name="difference_type"></a>move_iterator::difference_type

El tipo `difference_type` es un `move_iterator` `typedef` que se basa en el rasgo iterador `difference_type`, y se puede usar indistintamente con este.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Observaciones

Tipo sinónimo del rasgo iterador `typename iterator_traits<RandomIterator>::pointer`.

## <a name="move_iteratoriterator_category"></a><a name="iterator_category"></a>move_iterator::iterator_category

El tipo `iterator_category` es un `move_iterator` `typedef` que se basa en el rasgo iterador `iterator_category`, y se puede usar indistintamente con este.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Observaciones

Tipo sinónimo del rasgo iterador `typename iterator_traits<RandomIterator>::iterator_category`.

## <a name="move_iteratoriterator_type"></a><a name="iterator_type"></a>move_iterator::iterator_type

El tipo `iterator_type` se basa en el parámetro de plantilla `RandomIterator` para la plantilla de clase `move_iterator` y se puede usar indistintamente en su lugar.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `RandomIterator`.

## <a name="move_iteratormove_iterator"></a><a name="move_iterator"></a>move_iterator::move_iterator

Construye un iterador de movimiento. Usa el parámetro como iterador almacenado.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Iterador que se va a usar como iterador almacenado.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa el iterador almacenado con su constructor predeterminado. Los demás constructores inicializan el iterador almacenado con `base.base()`.

## <a name="move_iteratoroperator"></a><a name="op_add_eq"></a>move_iterator::operador+o

Agrega un desplazamiento al iterador almacenado, de modo que el iterador almacenado apunta al elemento en la nueva ubicación actual. Luego, el operador mueve el nuevo elemento actual.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parámetros

*_Off*\
Un desplazamiento para agregar a la posición actual con el fin de determinar la nueva posición actual.

### <a name="return-value"></a>Valor devuelto

Devuelve el nuevo elemento actual.

### <a name="remarks"></a>Observaciones

El operador agrega *_Off* al iterador almacenado. Después devuelve `*this`.

## <a name="move_iteratoroperator-"></a><a name="operator-_eq"></a>move_iterator::operador-o

Se desplaza por un número especificado de elementos anteriores. Este operador resta un desplazamiento al iterador almacenado.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Observaciones

El operador realiza la evaluación `*this += -_Off`. Después devuelve `*this`.

## <a name="move_iteratoroperator"></a><a name="op_add_add"></a>move_iterator::operador++

Incrementa el iterador almacenado que pertenece a este `move_iterator.`. El operador de postincremento accede al elemento actual. El operador de preincremento accede al siguiente elemento.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Observaciones

El primer operador (preincremento) incrementa el iterador almacenado. Después devuelve `*this`.

El segundo operador (postincremento) hace una copia de `*this` y realiza la evaluación `++*this`. Después devuelve la copia.

## <a name="move_iteratoroperator"></a><a name="op_add"></a>move_iterator::operador+

Devuelve la posición del iterador avanzada un número de elementos.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Observaciones

El operador `move_iterator(*this) +=` `_Off`devuelve .

## <a name="move_iteratoroperator"></a><a name="op_at"></a>move_iterator::operador[]

Permite el acceso del índice de matriz a elementos en el rango de `move iterator`.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Observaciones

El operador devuelve `(reference)*(*this + _Off)`.

## <a name="move_iteratoroperator--"></a><a name="operator--"></a>move_iterator::operador--

Los operadores de miembro de predecremento y postdecremento realizan una reducción en el iterador almacenado.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Observaciones

El primer operador de miembro (predecremento) disminuye el iterador almacenado. Después devuelve `*this`.

El segundo operador (postdecremento) hace una copia de `*this` y evalúa `--*this`. Después devuelve la copia.

## <a name="move_iteratoroperator-"></a><a name="operator-"></a>move_iterator::operador-

Disminuye el iterador almacenado y devuelve el valor indicado.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

### <a name="remarks"></a>Observaciones

El operador devuelve `move_iterator(*this) -= _Off`.

## <a name="move_iteratoroperator"></a><a name="op_star"></a>move_iterator::operador*

Desreferencia el iterador almacenado y devuelve el valor. Se comporta como un `rvalue reference` y efectúa una asignación de movimiento. El operador transfiere el elemento actual fuera del iterador base. El elemento que sigue se convierte en el nuevo elemento actual.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Observaciones

El operador devuelve `(reference)*base()`.

## <a name="move_iteratoroperator-gt"></a><a name="op_arrow"></a>move_iterator::operador-&gt;

Al igual que un `RandomIterator` `operator->` normal, proporciona acceso a los campos que pertenecen al elemento actual.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Observaciones

El operador devuelve `&**this`.

## <a name="move_iteratorpointer"></a><a name="pointer"></a>move_iterator::pointer

El `pointer` tipo es una **typedef** `RandomIterator` basada `move_iterator`en el iterador aleatorio para , y se puede utilizar indistintamente.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `RandomIterator`.

## <a name="move_iteratorreference"></a><a name="reference"></a>move_iterator::referencia

El `reference` tipo es un **typedef** basado en `value_type&&` for `move_iterator` `value_type&&`, y se puede utilizar indistintamente con .

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `value_type&&`, que es una referencia rvalue.

## <a name="move_iteratorvalue_type"></a><a name="value_type"></a>move_iterator::value_type

El tipo `value_type` es un `move_iterator` `typedef` que se basa en el rasgo iterador `value_type`, y se puede usar indistintamente con este.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Observaciones

Tipo sinónimo del rasgo iterador `typename iterator_traits<RandomIterator>::value_type`.

## <a name="see-also"></a>Consulte también

[\<iterador>](../standard-library/iterator.md)\
[Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)\
[Mover constructores y mover operadores de asignación (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
