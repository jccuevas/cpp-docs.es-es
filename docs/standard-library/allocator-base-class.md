---
title: allocator_base (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c078933ad35cff1a52de433b1ae5d321db1985c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="allocatorbase-class"></a>allocator_base (Clase)

Define la clase base y las funciones comunes necesarias para crear un asignador definido por el usuario a partir de un filtro de sincronización.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`Type`|Tipo de elementos que asigna el asignador.|
|`Sync`|Directiva de sincronización del asignador, que es [sync_none (Clase)](../standard-library/sync-none-class.md), [sync_per_container (Clase)](../standard-library/sync-per-container-class.md), [sync_per_thread (Clase)](../standard-library/sync-per-thread-class.md) o [sync_shared (Clase)](../standard-library/sync-shared-class.md).|

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[allocator_base](#allocator_base)|Construye un objeto de tipo `allocator_base`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero constante al tipo de objeto administrado por el asignador.|
|[const_reference](#const_reference)|Tipo que proporciona una referencia constante al tipo de objeto administrado por el asignador.|
|[difference_type](#difference_type)|Tipo entero con signo que puede representar la diferencia entre valores de punteros que señalan al tipo de objeto administrado por el asignador.|
|[pointer](#pointer)|Tipo que proporciona un puntero al tipo de objeto administrado por el asignador.|
|[reference](#reference)|Tipo que proporciona una referencia al tipo de objeto administrado por el asignador.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar la longitud de cualquier secuencia que un objeto de clase de plantilla `allocator_base` puede asignar.|
|[value_type](#value_type)|Tipo administrado por el asignador.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[_Charalloc](#charalloc)|Asigna almacenamiento para una matriz de tipo `char`.|
|[_Chardealloc](#chardealloc)|Libera almacenamiento para la matriz que contiene elementos de tipo `char`.|
|[address](#address)|Encuentra la dirección de un objeto cuyo valor se especifica.|
|[allocate](#allocate)|Asigna un bloque de memoria lo suficientemente grande como para almacenar al menos un número especificado de elementos.|
|[construct](#construct)|Crea un tipo concreto de objeto en una dirección especificada que se inicializa con un valor especificado.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|
|[destroy](#destroy)|Llama a un destructor de objetos sin desasignar la memoria donde el objeto se almacena.|
|[max_size](#max_size)|Devuelve el número de elementos de tipo `Type` que podría asignar un objeto de clase allocator antes de que la memoria libre se agote.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="charalloc"></a>  allocator_base::_Charalloc

Asigna almacenamiento para una matriz de tipo `char`.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`count`|El número de elementos de la matriz que se van a asignar.|

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto asignado.

### <a name="remarks"></a>Comentarios

Los contenedores usan esta función miembro cuando se compilan con un compilador que no puede compilar el reenlace. Implementa `_Charalloc` para el asignador definido por el usuario al devolver el resultado de una llamada a la función `allocate` del filtro de sincronización.

## <a name="chardealloc"></a>  allocator_base::_Chardealloc

Libera almacenamiento para la matriz que contiene elementos de tipo `char`.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Un puntero al primer objeto que se va a desasignar del almacenamiento.|
|`count`|El número de objetos que se van a desasignar del almacenamiento.|

### <a name="remarks"></a>Comentarios

Los contenedores usan esta función miembro cuando se compilan con un compilador que no puede compilar el reenlace. Implementa `_Chardealloc` para el asignador definido por el usuario al llamar a la función `deallocate` del filtro de sincronización. En el caso de un objeto de asignador igual a `*this`, el puntero ptr debe haber sido devuelto anteriormente por una llamada a `_Charalloc`, asignando un objeto de matriz del mismo tamaño y tipo. `_Chardealloc` nunca inicia una excepción.

## <a name="address"></a>  allocator_base::address

Encuentra la dirección de un objeto cuyo valor se especifica.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parámetros

`val` El valor de constante o nonconst del objeto cuya dirección se va a buscar.

### <a name="return-value"></a>Valor devuelto

Puntero const o nonconst al objeto encontrado de valor const o nonconst respectivamente.

### <a name="remarks"></a>Comentarios

Esta función miembro se implementa para el asignador definido por el usuario al devolver `&val`.

## <a name="allocate"></a>  allocator_base::allocate

Asigna un bloque de memoria lo suficientemente grande como para almacenar al menos un número especificado de elementos.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`_Nx`|El número de elementos de la matriz que se van a asignar.|
|`_Hint`|Este parámetro se ignora.|

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto asignado.

### <a name="remarks"></a>Comentarios

La función miembro implementa la asignación de memoria para el asignador definido por el usuario al devolver el resultado de una llamada a la función `allocate` del filtro de sincronización de tipo `*` si `_Nx == 1`, en caso contrario, al devolver el resultado de una llamada a la conversión `operator new(_Nx * sizeof(Type))` al tipo `*`.

## <a name="allocator_base"></a>  allocator_base::allocator_base

Construye un objeto de tipo `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`right`|Objeto de asignador que se va a copiar.|

### <a name="remarks"></a>Comentarios

El primer constructor crea una instancia [allocator_base](../standard-library/allocator-base-class.md). El segundo constructor crea una instancia `allocator_base` como la creada para cualquier instancia `allocator_base<Type, _Sync>` `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="const_pointer"></a>  allocator_base::const_pointer

Tipo que proporciona un puntero constante al tipo de objeto administrado por el asignador.

```cpp
typedef const Type *const_pointer;
```

## <a name="const_reference"></a>  allocator_base::const_reference

Tipo que proporciona una referencia constante al tipo de objeto administrado por el asignador.

```cpp
typedef const Type& const_reference;
```

## <a name="construct"></a>  allocator_base::construct

Crea un tipo concreto de objeto en una dirección especificada que se inicializa con un valor especificado.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Puntero a la ubicación donde se va a crear el objeto.|
|`val`|Valor con el que se va a inicializar el objeto que se está creando.|

### <a name="remarks"></a>Comentarios

Esta función miembro se implementa para el asignador definido por el usuario al llamar a `new((void*)ptr Type(val)`.

## <a name="deallocate"></a>  allocator_base::deallocate

Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Un puntero al primer objeto que se va a desasignar del almacenamiento.|
|`_Nx`|El número de objetos que se van a desasignar del almacenamiento.|

### <a name="remarks"></a>Comentarios

Esta función miembro se implementa para el asignador definido por el usuario al llamar a `deallocate(ptr)` en el filtro de sincronización `Sync` si `_Nx == 1`, en caso contrario, al llamar a `operator delete(_Nx * ptr)`.

## <a name="destroy"></a>  allocator_base::destroy

Llama a un destructor de objetos sin desasignar la memoria donde el objeto se almacena.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Puntero que designa la dirección del objeto que se va a destruir.|

### <a name="remarks"></a>Comentarios

Esta función miembro se implementa para el asignador definido por el usuario al llamar a `ptr->~Type()`.

## <a name="difference_type"></a>  allocator_base::difference_type

Tipo entero con signo que puede representar la diferencia entre valores de punteros que señalan al tipo de objeto administrado por el asignador.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="max_size"></a>  allocator_base::max_size

Devuelve el número de elementos de tipo `Type` que podría asignar un objeto de clase allocator antes de que la memoria libre se agote.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos que se pueden asignar.

### <a name="remarks"></a>Comentarios

Esta función miembro se implementa para el asignador definido por el usuario al devolver `(size_t)-1 / sizeof(Type)` si `0 < (size_t)-1 / sizeof(Type)`, de lo contrario, `1`.

## <a name="pointer"></a>  allocator_base::pointer

Tipo que proporciona un puntero al tipo de objeto administrado por el asignador.

```cpp
typedef Type *pointer;
```

## <a name="reference"></a>  allocator_base::reference

Tipo que proporciona una referencia al tipo de objeto administrado por el asignador.

```cpp
typedef Type& reference;
```

## <a name="size_type"></a>  allocator_base::size_type

Tipo entero sin signo que puede representar la longitud de cualquier secuencia que un objeto de clase de plantilla `allocator_base` puede asignar.

```cpp
typedef std::size_t size_type;
```

## <a name="value_type"></a>  allocator_base::value_type

Tipo administrado por el asignador.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
