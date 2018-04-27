---
title: unique_ptr (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
dev_langs:
- C++
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6271e028123d3eaba905323cbf220fbd9a6aab85
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="uniqueptr-class"></a>unique_ptr (Clase)

Almacena un puntero a un objeto o matriz en propiedad. El objeto o matriz no es propiedad de ningún otro `unique_ptr`. El objeto o matriz se destruye cuando `unique_ptr` se destruye.

## <a name="syntax"></a>Sintaxis

```cpp
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;


    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```

### <a name="parameters"></a>Parámetros

`Right` A `unique_ptr`.

`Nptr` Un `rvalue` de tipo `std::nullptr_t`.

`Ptr` A `pointer`.

`Deleter` A `deleter` función a la que está enlazado a un `unique_ptr`.

## <a name="exceptions"></a>Excepciones

`unique_ptr` no produce ninguna excepción.

## <a name="remarks"></a>Comentarios

La clase `unique_ptr` reemplaza a `auto_ptr` y se puede usar como un elemento de los contenedores de la biblioteca estándar de C++.

Use la función auxiliar [make_unique](../standard-library/memory-functions.md#make_unique) para crear eficazmente nuevas instancias de `unique_ptr`.

`unique_ptr` administra de forma única un recurso. Cada objeto `unique_ptr` almacena un puntero al objeto que posee o almacena un puntero null. Un recurso no puede ser propiedad de más de un objeto `unique_ptr`. Cuando se destruye un objeto `unique_ptr` que posee un recurso determinado, se libera el recurso. Un objeto `unique_ptr` se puede mover, pero no se puede copiar. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

El recurso se libera llamando a un objeto almacenado `deleter` de tipo `Del` que sabe cómo se asignan los recursos de un `unique_ptr` determinado. El valor predeterminado `deleter` `default_delete<T>` se da por supuesto que el recurso que señala `ptr` se asigna con `new`, y que se puede liberar llamando a `delete _Ptr`. (Una especialización parcial `unique_ptr<T[]>`administra los objetos de matriz asignados con `new[]`, y tiene el `deleter` `default_delete<T[]>` predeterminado, especializado en llamar a delete[] `ptr`.)

El puntero almacenado en un recurso propio, `stored_ptr` tiene el tipo `pointer`. Es `Del::pointer` si se define y `T *` si no se define. El objeto almacenado `deleter` `stored_deleter` no ocupa ningún espacio en el objeto si `deleter` no tiene estado. Observe que `Del` puede ser un tipo de referencia.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[unique_ptr](#unique_ptr)|Hay siete constructores de `unique_ptr`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[deleter_type](#deleter_type)|Sinónimo del parámetro de plantilla `Del`.|
|[element_type](#element_type)|Sinónimo del parámetro de plantilla `T`.|
|[pointer](#pointer)|Sinónimo de `Del::pointer` si se define, si no `T *`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[get](#get)|Devuelve `stored_ptr`.|
|[get_deleter](#get_deleter)|Devuelve una referencia a `stored_deleter`.|
|[release](#release)|Almacena `pointer()` en `stored_ptr` y devuelve su contenido anterior.|
|[reset](#reset)|Libera el recurso actualmente en propiedad y acepta un nuevo recurso.|
|[swap](#swap)|Intercambia el recurso y `deleter` con el `unique_ptr` proporcionado.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|`operator bool`|El operador devuelve un valor de un tipo que pueda convertirse en `bool`. El resultado de la conversión en `bool` es `true` cuando `get() != pointer()`, si no `false`.|
|`operator->`|La función miembro devuelve `stored_ptr`.|
|`operator*`|La función miembro devuelve `*stored_ptr`.|
|[unique_ptr operator=](#unique_ptr_operator_eq)|Asigna el valor de `unique_ptr` (o un `pointer-type`) al `unique_ptr` actual.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<memory>

**Espacio de nombres:** std

## <a name="deleter_type"></a>  deleter_type

El tipo es un sinónimo del parámetro de plantilla `Del`.

```cpp
typedef Del deleter_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Del`.

## <a name="element_type"></a>  element_type

El tipo es un sinónimo del parámetro de plantilla `Type`.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Ty`.

## <a name="get"></a>  unique_ptr::get

Devuelve `stored_ptr`.

```cpp
pointer get() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve `stored_ptr`.

## <a name="get_deleter"></a>  unique_ptr::get_deleter

Devuelve una referencia a `stored_deleter`.

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una referencia a `stored_deleter`.

## <a name="unique_ptr_operator_eq"></a>  unique_ptr operator=

Asigna la dirección del `unique_ptr` proporcionado al actual.

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

### <a name="parameters"></a>Parámetros

Referencia `unique_ptr` usada para asignar el valor correspondiente al `unique_ptr` actual.

### <a name="remarks"></a>Comentarios

Las funciones miembro llaman a `reset(right.release())` mueven `right.stored_deleter` a `stored_deleter` y después devuelven `*this`.

## <a name="pointer"></a>  pointer

Sinónimo de `Del::pointer` si se define, si no `Type *`.

```cpp
typedef T1 pointer;
```

### <a name="remarks"></a>Comentarios

Tipo sinónimo de `Del::pointer` si se define; de lo contrario, es `Type *`.

## <a name="release"></a>  unique_ptr::release

Libera la propiedad del puntero almacenado devuelto al llamador y establece el valor del puntero almacenado en `nullptr`.

```cpp
pointer release();
```

### <a name="remarks"></a>Comentarios

Use `release` para asumir la propiedad del puntero sin formato almacenado por `unique_ptr`. El llamador es responsable de la eliminación del puntero devuelto. `unique-ptr` se establece en el estado vacío construido de forma predeterminada. Puede asignar otro puntero de tipo compatible al valor `unique_ptr` después de la llamada a `release`.

### <a name="example"></a>Ejemplo

Este ejemplo muestra cómo el llamador de versión es responsable del objeto devuelto:

```cpp
// stl_release_unique.cpp
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp
#include <iostream>
#include <memory>

struct Sample {
   int content_;
   Sample(int content) : content_(content) {
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;
   }
   ~Sample() {
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;
   }
};

void ReleaseUniquePointer() {
   // Use make_unique function when possible.
   auto up1 = std::make_unique<Sample>(3);
   auto up2 = std::make_unique<Sample>(42);

   // Take over ownership from the unique_ptr up2 by using release
   auto ptr = up2.release();
   if (up2) {
      // This statement does not execute, because up2 is empty.
      std::cout << "up2 is not empty." << std::endl;
   }
   // We are now responsible for deletion of ptr.
   delete ptr;
   // up1 deletes its stored pointer when it goes out of scope.
}

int main() {
   ReleaseUniquePointer();
}
```

Salida del equipo:

```Output
Constructing Sample(3)
Constructing Sample(42)
Deleting Sample(42)
Deleting Sample(3)

```

## <a name="reset"></a>  unique_ptr::reset

Toma posesión del parámetro de puntero y, luego, elimina el puntero almacenado original. Si el nuevo puntero es el mismo que el puntero almacenado original, `reset` elimina el puntero y establece el puntero almacenado en `nullptr`.

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Puntero al recurso del que tomar posesión.|

### <a name="remarks"></a>Comentarios

Use `reset` para cambiar el [puntero](#pointer) almacenado propiedad de `unique_ptr` a `ptr` y, luego, eliminar el puntero almacenado original. Si `unique_ptr` no estaba vacío, `reset` invoca la función eliminadora devuelta por [get_deleter](#get_deleter) en el puntero almacenado original.

Como `reset` almacena en primer lugar el nuevo puntero `ptr` y, después, elimina el puntero almacenado original, es posible que `reset` elimine de forma inmediata `ptr` si es el mismo que el puntero almacenado original.

## <a name="swap"></a>  unique_ptr::swap

Intercambia los punteros entre dos objetos `unique_ptr`.

```cpp
void swap(unique_ptr& right);
```

### <a name="parameters"></a>Parámetros

`right` Un `unique_ptr` usado para intercambiar punteros.

### <a name="remarks"></a>Comentarios

La función miembro cambia `stored_ptr` por `right.stored_ptr` y `stored_deleter` por `right.stored_deleter`.

## <a name="unique_ptr"></a>  unique_ptr::unique_ptr

Hay siete constructores de `unique_ptr`.

```cpp
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,
    typename conditional<
    is_reference<Del>::value,
    Del,
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>
unique_ptr(unique_ptr<Ty2, Del2>&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Puntero al recurso que se va a asignar a un `unique_ptr.`.|
|`_Deleter`|`deleter` que se asignará a un `unique_ptr`.|
|`right`|`rvalue reference` a un `unique_ptr` desde el que los campos `unique_ptr` se asignan al `unique_ptr` recién construido.|

### <a name="remarks"></a>Comentarios

Los dos primeros constructores construyen un objeto que no administra ningún recurso. El tercer constructor almacena `ptr` en `stored_ptr`. El cuarto constructor almacena `ptr` en `stored_ptr` y `deleter` en `stored_deleter`.

El quinto constructor almacena `ptr` en `stored_ptr` y coloca `deleter` dentro de `stored_deleter`. El sexto y el séptimo constructor almacenan `right.release()` en `stored_ptr` y colocan `right.get_deleter()` dentro de `stored_deleter`.

## <a name="dtorunique_ptr"></a>  unique_ptr ~unique_ptr

El destructor de `unique_ptr` destruye un objeto `unique_ptr`.

```cpp
~unique_ptr();
```

### <a name="remarks"></a>Comentarios

El destructor llama a `get_deleter()(stored_ptr)`.

## <a name="see-also"></a>Vea también

[\<memory>](../standard-library/memory.md)<br/>
