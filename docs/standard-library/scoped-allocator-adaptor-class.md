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
ms.openlocfilehash: c02f5171fac862b6f79e194f5940b0adeb2e93e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601427"
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor (clase)

Representa una anidación de asignadores.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Comentarios

La clase de plantilla encapsula una anidación de uno o más asignadores. Cada clase tiene un asignador exterior de tipo `outer_allocator_type`, un sinónimo de `Outer`, que es una base pública del objeto `scoped_allocator_adaptor`. `Outer` se usa para asignar la memoria que va a usar un contenedor. Puede obtener una referencia a este objeto base de asignador mediante una llamada a `outer_allocator`.

El resto de la anidación tiene el tipo `inner_allocator_type`. Un asignador interno se usa para asignar memoria para los elementos dentro de un contenedor. Puede obtener una referencia al objeto almacenado de este tipo mediante una llamada a `inner_allocator`. Si `Inner...` no está vacío, `inner_allocator_type` tiene el tipo `scoped_allocator_adaptor<Inner...>` y `inner_allocator` designa un objeto miembro. De lo contrario, `inner_allocator_type` tiene el tipo `scoped_allocator_adaptor<Outer>` y `inner_allocator` designa el objeto completo.

La anidación se comporta como si tuviera una profundidad arbitraria, y replica su asignador interior encapsulado según sea necesario.

Varios conceptos que no forman parte de la interfaz visible ayudan a describir el comportamiento de esta clase de plantilla. Un *asignador exterior* media en todas las llamadas a los métodos de construcción y destrucción. Se define eficazmente mediante la función recursiva `OUTERMOST(X)`, donde `OUTERMOST(X)` es uno de los siguientes.

- Si `X.outer_allocator()` está bien formado, entonces `OUTERMOST(X)` es `OUTERMOST(X.outer_allocator())`.

- En caso contrario, `OUTERMOST(X)` es `X`.

Como ejemplo, se definen tres tipos:

|Tipo|Descripción|
|----------|-----------------|
|`Outermost`|Tipo de `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Constructores

|nombre|Descripción|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Construye un objeto `scoped_allocator_adaptor`.|

### <a name="typedefs"></a>Typedefs

|Name|Descripción|
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

|nombre|Descripción|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind (Struct)](#rebind_struct)|Define el tipo `Outer::rebind\<Other>::other` como sinónimo de `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Métodos

|Name|Descripción|
|----------|-----------------|
|[allocate](#allocate)|Asigna memoria usando el asignador `Outer`.|
|[construct](#construct)|Construye un objeto.|
|[deallocate](#deallocate)|Desasigna los objetos mediante el asignador exterior.|
|[destroy](#destroy)|Destruye un objeto especificado.|
|[inner_allocator](#inner_allocator)|Recupera una referencia al objeto almacenado de tipo `inner_allocator_type`.|
|[max_size](#max_size)|Determina el número máximo de objetos que el asignador exterior puede asignar.|
|[outer_allocator](#outer_allocator)|Recupera una referencia al objeto almacenado de tipo `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Crea un nuevo objeto `scoped_allocator_adaptor` con cada objeto de asignador almacenado inicializado mediante una llamada a `select_on_container_copy_construction` para cada asignador correspondiente.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<scoped_allocator>

**Espacio de nombres:** std

## <a name="allocate"></a>  scoped_allocator_adaptor::Allocate

Asigna memoria usando el asignador `Outer`.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parámetros

*count*<br/>
Número de elementos para los que se va a asignar suficiente espacio de almacenamiento.

*Sugerencia*<br/>
Un puntero que es posible que ayude el objeto de asignador ubicando la dirección de un objeto asignado antes de la solicitud.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve `Outer_traits::allocate(outer_allocator(), count)`. La segunda función miembro devuelve `Outer_traits::allocate(outer_allocator(), count, hint)`.

## <a name="construct"></a>  scoped_allocator_adaptor::construct

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

*ptr*<br/>
Un puntero a la ubicación de memoria donde se va a crear el objeto.

*args*<br/>
Una lista de argumentos.

*first*<br/>
Un objeto del primer tipo en un par.

*segundo*<br/>
Un objeto del segundo tipo en un par.

*right*<br/>
Un objeto existente para mover o copiar.

### <a name="remarks"></a>Comentarios

El primer método construye el objeto en *ptr* mediante una llamada a `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, donde `xargs...` es uno de los siguientes.

- Si `uses_allocator<Ty, inner_allocator_type>` es falso `xargs...` es `args...`.

- Si `uses_allocator<Ty, inner_allocator_type>` es verdadero y `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` es verdadero, entonces `xargs...` es `allocator_arg, inner_allocator(), args...`.

- Si `uses_allocator<Ty, inner_allocator_type>` es verdadero y `is_constructible<Ty, args..., inner_allocator()>` es verdadero, entonces `xargs...` es `args..., inner_allocator()`.

El segundo método construye el objeto de par en *ptr* mediante una llamada a `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, donde `xargs...` es `first...` modificado como en la lista anterior, y `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, donde `xargs...` es `second...` modificado como se muestra en la lista anterior.

El tercer método se comporta igual que `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

El cuarto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

El quinto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

El sexto método se comporta igual que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="deallocate"></a>  scoped_allocator_adaptor::DEALLOCATE

Desasigna los objetos mediante el asignador exterior.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
Puntero a la ubicación inicial de los objetos que se van a desasignar.

*count*<br/>
Número de objetos que se van a desasignar.

## <a name="destroy"></a>  scoped_allocator_adaptor::Destroy

Destruye un objeto especificado.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
Un puntero al objeto que se va a destruir.

### <a name="return-value"></a>Valor devuelto

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>  scoped_allocator_adaptor::inner_allocator

Recupera una referencia al objeto almacenado de tipo `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al objeto almacenado de tipo `inner_allocator_type`.

## <a name="max_size"></a>  scoped_allocator_adaptor::max_size

Determina el número máximo de objetos que el asignador exterior puede asignar.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Valor devuelto

`Outer_traits::max_size(outer_allocator())`

## <a name="outer_allocator"></a>  scoped_allocator_adaptor::outer_allocator

Recupera una referencia al objeto almacenado de tipo `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al objeto almacenado de tipo `outer_allocator_type`.

## <a name="rebind_struct"></a>  scoped_allocator_adaptor::rebind (Struct)

Define el tipo `Outer::rebind\<Other>::other` como sinónimo de `scoped_allocator_adaptor\<Other, Inner...>`.

struct reenlace {typedef Other_traits::rebind\<otros > Other_alloc; typedef scoped_allocator_adaptor ()\<Other_alloc, interna... > other;};

## <a name="scoped_allocator_adaptor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor (constructor)

Construye un objeto `scoped_allocator_adaptor`.

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
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Un `scoped_allocator_adaptor` existente.

*Al*<br/>
Un asignador existente que se usará como el asignador exterior.

*REST*<br/>
Una lista de asignadores que se usarán como los asignadores exteriores.

### <a name="remarks"></a>Comentarios

El primer constructor construye de manera predeterminada sus objetos de asignador almacenado. Cada uno de los tres constructores siguientes construye los objetos de asignador almacenado de los objetos correspondientes en *derecho*. El último constructor construye los objetos de asignador almacenado a partir de los argumentos correspondientes en la lista de argumentos.

## <a name="select_on_container_copy_construction"></a>  scoped_allocator_adaptor::select_on_container_copy_construction

Crea un nuevo objeto `scoped_allocator_adaptor` con cada objeto de asignador almacenado inicializado mediante una llamada a `select_on_container_copy_construction` para cada asignador correspondiente.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve eficazmente `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. El resultado es un nuevo `scoped_allocator_adaptor` objeto con cada objeto de asignador almacenado inicializado mediante una llamada a `al.select_on_container_copy_construction()` para el correspondiente asignador *al*.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
