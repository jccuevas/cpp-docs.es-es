---
title: scoped_allocator_adaptor (clase)
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
ms.openlocfilehash: b08cf1858cb0f9bf4dc6201edc2502d48754ff77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373397"
---
# <a name="scoped_allocator_adaptor-class"></a>scoped_allocator_adaptor (clase)

Representa una anidación de asignadores.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Observaciones

La plantilla de clase encapsula un nido de uno o varios asignadores. Cada clase tiene un asignador exterior de tipo `outer_allocator_type`, un sinónimo de `Outer`, que es una base pública del objeto `scoped_allocator_adaptor`. `Outer` se usa para asignar la memoria que va a usar un contenedor. Puede obtener una referencia a este objeto base de asignador mediante una llamada a `outer_allocator`.

El resto de la anidación tiene el tipo `inner_allocator_type`. Un asignador interno se usa para asignar memoria para los elementos dentro de un contenedor. Puede obtener una referencia al objeto almacenado de este tipo mediante una llamada a `inner_allocator`. Si `Inner...` no está vacío, `inner_allocator_type` tiene el tipo `scoped_allocator_adaptor<Inner...>` y `inner_allocator` designa un objeto miembro. De lo contrario, `inner_allocator_type` tiene el tipo `scoped_allocator_adaptor<Outer>` y `inner_allocator` designa el objeto completo.

La anidación se comporta como si tuviera una profundidad arbitraria, y replica su asignador interior encapsulado según sea necesario.

Varios conceptos que no forman parte de la interfaz visible ayudan a describir el comportamiento de esta plantilla de clase. Un *asignador exterior* media en todas las llamadas a los métodos de construcción y destrucción. Se define eficazmente mediante la función recursiva `OUTERMOST(X)`, donde `OUTERMOST(X)` es uno de los siguientes.

- Si `X.outer_allocator()` está bien formado, entonces `OUTERMOST(X)` es `OUTERMOST(X.outer_allocator())`.

- En caso contrario, `OUTERMOST(X)` es `X`.

Como ejemplo, se definen tres tipos:

|Tipo|Descripción|
|----------|-----------------|
|`Outermost`|Tipo de `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Constructores

|Nombre|Descripción|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Construye un objeto `scoped_allocator_adaptor`.|

### <a name="typedefs"></a>Typedefs

|Nombre|Descripción|
|----------|-----------------|
|`const_pointer`|Este tipo es un sinónimo del `const_pointer` que está asociado con el asignador `Outer`.|
|`const_void_pointer`|Este tipo es un sinónimo del `const_void_pointer` que está asociado con el asignador `Outer`.|
|`difference_type`|Este tipo es un sinónimo del `difference_type` que está asociado con el asignador `Outer`.|
|`inner_allocator_type`|Este tipo es un sinónimo del tipo del adaptador anidado `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Este tipo es un sinónimo del tipo del asignador base `Outer`.|
|`pointer`|Este tipo es un sinónimo del `pointer` asociado con el asignador `Outer`.|
|`propagate_on_container_copy_assignment`|El tipo es verdadero solo si `Outer_traits::propagate_on_container_copy_assignment` es verdadero o `inner_allocator_type::propagate_on_container_copy_assignment` es verdadero.|
|`propagate_on_container_move_assignment`|El tipo es verdadero solo si `Outer_traits::propagate_on_container_move_assignment` es verdadero o `inner_allocator_type::propagate_on_container_move_assignment` es verdadero.|
|`propagate_on_container_swap`|El tipo es verdadero solo si `Outer_traits::propagate_on_container_swap` es verdadero o `inner_allocator_type::propagate_on_container_swap` es verdadero.|
|`size_type`|Este tipo es un sinónimo del `size_type` asociado con el asignador `Outer`.|
|`value_type`|Este tipo es un sinónimo del `value_type` asociado con el asignador `Outer`.|
|`void_pointer`|Este tipo es un sinónimo del `void_pointer` asociado con el asignador `Outer`.|

### <a name="structs"></a>Estructuras

|Nombre|Descripción|
|----------|-----------------|
|[scoped_allocator_adaptor::Reenlazar Struct](#rebind_struct)|Define el tipo `Outer::rebind\<Other>::other` como sinónimo de `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Métodos

|Nombre|Descripción|
|----------|-----------------|
|[Asignar](#allocate)|Asigna memoria usando el asignador `Outer`.|
|[Construir](#construct)|Construye un objeto.|
|[deallocate](#deallocate)|Desasigna los objetos mediante el asignador exterior.|
|[Destruir](#destroy)|Destruye un objeto especificado.|
|[inner_allocator](#inner_allocator)|Recupera una referencia al objeto almacenado de tipo `inner_allocator_type`.|
|[max_size](#max_size)|Determina el número máximo de objetos que el asignador exterior puede asignar.|
|[outer_allocator](#outer_allocator)|Recupera una referencia al objeto almacenado de tipo `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Crea un nuevo objeto `scoped_allocator_adaptor` con cada objeto de asignador almacenado inicializado mediante una llamada a `select_on_container_copy_construction` para cada asignador correspondiente.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_as)||
|[operadora](#op_eq_eq)||
|[¡Operador!](#op_noeq)||

## <a name="requirements"></a>Requisitos

**Encabezado:** \<scoped_allocator>

**Espacio de nombres:** std

## <a name="scoped_allocator_adaptorallocate"></a><a name="allocate"></a>scoped_allocator_adaptor::asignar

Asigna memoria usando el asignador `Outer`.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parámetros

*Contar*\
El número de elementos para los que se puede asignar suficiente espacio de almacenamiento.

*Pista*\
Un puntero que es posible que ayude el objeto de asignador ubicando la dirección de un objeto asignado antes de la solicitud.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve `Outer_traits::allocate(outer_allocator(), count)`. La segunda función miembro devuelve `Outer_traits::allocate(outer_allocator(), count, hint)`.

## <a name="scoped_allocator_adaptorconstruct"></a><a name="construct"></a>scoped_allocator_adaptor::construcción

Construye un objeto.

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>Parámetros

*Ptr*\
Un puntero a la ubicación de memoria donde se va a crear el objeto.

*Args*\
Una lista de argumentos.

*Primero*\
Un objeto del primer tipo en un par.

*Segundo*\
Un objeto del segundo tipo en un par.

*Correcto*\
Un objeto existente para mover o copiar.

### <a name="remarks"></a>Observaciones

El primer método construye el objeto `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`en `xargs...` *ptr* llamando a , donde es uno de los siguientes.

- Si `uses_allocator<Ty, inner_allocator_type>` es falso `xargs...` es `args...`.

- Si `uses_allocator<Ty, inner_allocator_type>` es verdadero y `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` es verdadero, entonces `xargs...` es `allocator_arg, inner_allocator(), args...`.

- Si `uses_allocator<Ty, inner_allocator_type>` es verdadero y `is_constructible<Ty, args..., inner_allocator()>` es verdadero, entonces `xargs...` es `args..., inner_allocator()`.

El segundo método construye el objeto `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`de `xargs...` par `first...` en ptr llamando a `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, `xargs...` `second...` donde se modifica como en la lista anterior y , donde se modifica como en la lista anterior. *ptr*

El tercer método se comporta igual que `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

El cuarto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

El quinto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

El sexto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="scoped_allocator_adaptordeallocate"></a><a name="deallocate"></a>scoped_allocator_adaptor::deallocate

Desasigna los objetos mediante el asignador exterior.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parámetros

*Ptr*\
Puntero a la ubicación inicial de los objetos que se van a desasignar.

*Contar*\
Número de objetos que se van a desasignar.

## <a name="scoped_allocator_adaptordestroy"></a><a name="destroy"></a>scoped_allocator_adaptor::destroy

Destruye un objeto especificado.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parámetros

*Ptr*\
Un puntero al objeto que se va a destruir.

### <a name="return-value"></a>Valor devuelto

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="scoped_allocator_adaptorinner_allocator"></a><a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

Recupera una referencia al objeto almacenado de tipo `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al objeto almacenado de tipo `inner_allocator_type`.

## <a name="scoped_allocator_adaptormax_size"></a><a name="max_size"></a>scoped_allocator_adaptor::max_size

Determina el número máximo de objetos que el asignador exterior puede asignar.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Valor devuelto

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameop_as--scoped_allocator_adaptoroperator"></a><a name="op_as">scoped_allocator_adaptor::operador ?

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameop_eq_eq--scoped_allocator_adaptoroperator"></a><a name="op_eq_eq">scoped_allocator_adaptor::operador

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameop_noeq--scoped_allocator_adaptoroperator"></a><a name="op_noeq">scoped_allocator_adaptor::operador!

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="scoped_allocator_adaptorouter_allocator"></a><a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

Recupera una referencia al objeto almacenado de tipo `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al objeto almacenado de tipo `outer_allocator_type`.

## <a name="scoped_allocator_adaptorrebind-struct"></a><a name="rebind_struct"></a>scoped_allocator_adaptor::Reenlazar Struct

Define el tipo `Outer::rebind\<Other>::other` como sinónimo de `scoped_allocator_adaptor\<Other, Inner...>`.

struct rebind- typedef Other_traits::rebind\<Other>\<Other_alloc; typedef scoped_allocator_adaptor Other_alloc, Inner...> other;

## <a name="scoped_allocator_adaptorscoped_allocator_adaptor-constructor"></a><a name="scoped_allocator_adaptor"></a>Constructor scoped_allocator_adaptor::scoped_allocator_adaptor

Construye un objeto `scoped_allocator_adaptor`. También incluye un destructor.

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;

~scoped_allocator_adaptor();
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Un `scoped_allocator_adaptor` existente.

*al*\
Un asignador existente que se usará como el asignador exterior.

*reposo*\
Una lista de asignadores que se usarán como los asignadores exteriores.

### <a name="remarks"></a>Observaciones

El primer constructor construye de manera predeterminada sus objetos de asignador almacenado. Cada uno de los tres constructores siguientes construye sus objetos de asignador almacenados a partir de los objetos correspondientes a *la derecha.* El último constructor construye los objetos de asignador almacenado a partir de los argumentos correspondientes en la lista de argumentos.

## <a name="scoped_allocator_adaptorselect_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction

Crea un nuevo objeto `scoped_allocator_adaptor` con cada objeto de asignador almacenado inicializado mediante una llamada a `select_on_container_copy_construction` para cada asignador correspondiente.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve eficazmente `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. El resultado es `scoped_allocator_adaptor` un nuevo objeto con cada `al.select_on_container_copy_construction()` objeto de asignador almacenado inicializado llamando al asignador correspondiente *al*.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
