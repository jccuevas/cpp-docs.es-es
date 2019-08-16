---
title: shared_ptr (Clase)
ms.date: 07/29/2019
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
ms.openlocfilehash: 59346dfded63aec315304f76c9bed753a4db1224
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682442"
---
# <a name="sharedptr-class"></a>shared_ptr (Clase)

Encapsula un puntero inteligente en el que se cuentan las referencias alrededor de un objeto asignado dinámicamente.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>Comentarios

La `shared_ptr` clase describe un objeto que utiliza el recuento de referencias para administrar recursos. Un objeto `shared_ptr` contiene eficazmente un puntero al recurso que posee o contiene un puntero null. Un recurso puede ser propiedad de más de un objeto `shared_ptr`; cuando se destruye el último objeto `shared_ptr` que posee un recurso determinado, se libera el recurso.

Un `shared_ptr` detiene el propietario de un recurso cuando se reasigna o se restablece.

El argumento de plantilla `T` puede ser un tipo incompleto, salvo lo indicado para ciertas funciones miembro.

Cuando se construye un objeto `shared_ptr<T>` desde un puntero de recursos de tipo `G*` o desde un `shared_ptr<G>`, el tipo de puntero `G*` debe poder convertirse a `T*`. Si no se pueden convertir, el código no se compilará. Por ejemplo:

```cpp
#include <memory>
using namespace std;

class F {};
class G : public F {};

shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>
shared_ptr<int> sp5(new G); // error, G* not convertible to int*
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>
```

Un objeto `shared_ptr` posee un recurso:

- si se construyó con un puntero a ese recurso,

- si se construyó desde un objeto `shared_ptr` que posee ese recurso,

- Si se construyó a partir de un objeto [weak_ptr](weak-ptr-class.md) que apunta a ese recurso, o

- si se le asignó la propiedad de ese recurso, ya sea con [shared_ptr::operator=](#op_eq) o mediante una llamada a la función miembro [shared_ptr::reset](#reset).

Los objetos `shared_ptr` que poseen un recurso comparten un bloque de control. El bloque de control contiene:

- el número de objetos `shared_ptr` que poseen el recurso,

- el número de objetos `weak_ptr` que apuntan al recurso,

- el eliminador para ese recurso, si existe,

- el asignador personalizado para el bloque de control, si tiene alguno.

Un objeto `shared_ptr` que se inicializa mediante un puntero NULL tiene un bloque de control y no está vacío. Después de que un objeto `shared_ptr` libera un recurso, ya no posee ese recurso. Después de que un objeto `weak_ptr` libera un recurso, ya no apunta a ese recurso.

Cuando el número de objetos `shared_ptr` que poseen un recurso es cero, el recurso se libera eliminándolo o pasando su dirección a un eliminador, según cómo se creara originalmente la propiedad del recurso. Cuando el número de objetos `shared_ptr` que poseen un recurso es cero, y el número de objetos `weak_ptr` que apuntan a ese recurso es cero, el bloque de control se libera, utilizando el asignador personalizado para el bloque de control si tiene alguno.

Un objeto `shared_ptr` vacío no posee ningún recurso y no tiene ningún bloque de control.

Un eliminador es un objeto de función que tiene una función miembro `operator()`. Su tipo se debe poder construir mediante copia, y su constructor y destructor de copias no deben producir excepciones. Acepta un parámetro: el objeto que se va a eliminar.

Algunas funciones toman una lista de argumentos que define propiedades del objeto `shared_ptr<T>` o `weak_ptr<T>` resultante. Hay varias maneras de especificar esta lista de argumentos:

sin argumentos: el objeto resultante es un objeto `shared_ptr` o `weak_ptr` vacío.

`ptr`: puntero de tipo `Other*` al recurso que se va a administrar. `T` debe ser un tipo completo. Si se produce un error en la función (porque no se puede asignar el bloque de control) `delete ptr`, evalúa la expresión.

`ptr, deleter`: puntero de tipo `Other*` al recurso que se va a administrar y un eliminador para ese recurso. Si se produce un error en la función (porque no se puede asignar el bloque `deleter(ptr)`de control), llama a, que debe estar bien definido.

`ptr, deleter, alloc`: puntero de tipo `Other*` al recurso que se va a administrar, un eliminador para ese recurso y un asignador para administrar cualquier almacenamiento que se deba asignar y liberar. Si se produce un error en la función (porque no se puede asignar el bloque `deleter(ptr)`de control), llama a, que debe estar bien definido.

`sp`: objeto `shared_ptr<Other>` que posee el recurso que se va a administrar.

`wp`: objeto `weak_ptr<Other>` que apunta al recurso que se va a administrar.

`ap`: objeto `auto_ptr<Other>` que contiene un puntero al recurso que se va a administrar. Si la función se ejecuta correctamente, llama `ap.release()`a; de lo `ap` contrario, deja sin modificar.

En todos los casos, el tipo de puntero `Other*` debe poder convertirse a `T*`.

## <a name="thread-safety"></a>Seguridad para subprocesos

Varios subprocesos pueden leer y escribir diferentes objetos `shared_ptr` al mismo tiempo, incluso cuando los objetos son copias que comparten la propiedad.

## <a name="members"></a>Miembros

|||
|-|-|
| **Constructores** | |
|[shared_ptr](#shared_ptr)|Construye un objeto `shared_ptr`.|
|[~ shared_ptr](#dtorshared_ptr)|Destruye un objeto `shared_ptr`.|
| **Typedefs** | |
|[element_type](#element_type)|El tipo de un elemento.|
|[weak_type](#weak_type)|El tipo de un puntero débil a un elemento.|
| **Funciones miembro** | |
|[get](#get)|Obtiene la dirección del recurso propio.|
|[owner_before](#owner_before)|Devuelve true si este `shared_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.|
|[reset](#reset)|Reemplaza el recurso propio.|
|[swap](#swap)|Intercambia dos objetos `shared_ptr`.|
|[unique](#unique)|Comprueba si el recurso propio es único.|
|[use_count](#use_count)|Cuenta los números de propietarios del recurso.|
| **Operadores** | |
|[operator bool](#op_bool)|Comprueba si existe un recurso propio.|
|[operator*](#op_star)|Obtiene el valor designado.|
|[operator=](#op_eq)|Reemplaza el recurso propio.|
|[Operator&gt;](#op_arrow)|Obtiene un puntero al valor designado.|

## <a name="element_type"></a>element_type

El tipo de un elemento.

```cpp
typedef T element_type;                  // before C++17
using element_type = remove_extent_t<T>; // C++17
```

### <a name="remarks"></a>Comentarios

El `element_type` tipo es un sinónimo del parámetro `T`de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="get"></a>Obtener

Obtiene la dirección del recurso propio.

```cpp
element_type* get() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la dirección del recurso propietario. Si el objeto no posee un recurso, devuelve 0.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}
```

```Output
sp0.get() == 0 == true
*sp1.get() == 5
```

## <a name="op_bool"></a>operador bool

Comprueba si existe un recurso propio.

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>Comentarios

El operador devuelve un valor de **true** cuando `get() != nullptr`, de lo contrario, **es false**.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_operator_bool.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
(bool)sp1 == true
```

## <a name="op_star"></a>Operator

Obtiene el valor designado.

```cpp
T& operator*() const noexcept;
```

### <a name="remarks"></a>Comentarios

El operador de direccionamiento indirecto devuelve `*get()`. Por tanto, el puntero almacenado no debe ser null.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_operator_st.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
```

## <a name="op_eq"></a> operator=

Reemplaza el recurso propio.

```cpp
shared_ptr& operator=(const shared_ptr& sp) noexcept;

shared_ptr& operator=(shared_ptr&& sp) noexcept;

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp) noexcept;

template <class Other>
shared_ptr& operator=(shared_ptr<Other>&& sp) noexcept;

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);    // deprecated in C++11, removed in C++17

template <class Other, class Deleter>
shared_ptr& operator=(unique_ptr<Other, Deleter>&& up);
```

### <a name="parameters"></a>Parámetros

*dañado*\
Puntero compartido del que se va a copiar o cambiar.

*aislamiento*\
Puntero automático que se va a desplace. La `auto_ptr` sobrecarga está en desuso en c++ 11 y se ha quitado en c++ 17.

*los*\
Puntero único al objeto del que se va a adoptar la propiedad. *up* no posee ningún objeto después de la llamada.

*Distinta*\
Tipo del objeto al que apunta *SP*, *AP*o *up*.

*Eliminador*\
Tipo del eliminador del objeto propietario, almacenado para la eliminación posterior del objeto.

### <a name="remarks"></a>Comentarios

Todos los operadores disminuyen el recuento de referencias para el recurso que posee actualmente `*this` y asignan la propiedad del recurso denominado por la secuencia de operandos a `*this`. Si el recuento de referencias llega a cero, se libera el recurso. Si se produce un error en un `*this` operador, deja sin modificar.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::unique_ptr<int> up(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = up;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}
```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="op_arrow"></a>operador->

Obtiene un puntero al valor designado.

```cpp
T* operator->() const noexcept;
```

### <a name="remarks"></a>Comentarios

El operador de selección devuelve `get()`, de modo que la expresión `sp->member` se comporta igual que `(sp.get())->member` donde `sp` es un objeto de clase `shared_ptr<T>`. Por tanto, el puntero almacenado no debe ser null, y `T` debe ser una clase, estructura o tipo de unión con un miembro `member`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_operator_ar.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}
```

```Output
sp0->first == 1
sp0->second == 2
```

## <a name="owner_before"></a>owner_before

Devuelve true si este `shared_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>Parámetros

*anota*\
Una referencia lvalue a `shared_ptr` `weak_ptr`o a.

### <a name="remarks"></a>Comentarios

La función miembro de plantilla devuelve true `*this` si se ordena `ptr`antes que.

## <a name="reset"></a>determinado

Reemplaza el recurso propio.

```cpp
void reset() noexcept;

template <class Other>
void reset(Other *ptr);

template <class Other, class Deleter>
void reset(
    Other *ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
void reset(
    Other *ptr,
    Deleter deleter,
    Allocator alloc);
```

### <a name="parameters"></a>Parámetros

*Distinta*\
Tipo controlado por el puntero de argumento.

*Eliminador*\
Tipo del eliminador.

*anota*\
Puntero que se va a copiar.

*Eliminador*\
El eliminador que se va a copiar.

*Asignador*\
Tipo del asignador.

*Alloc*\
El asignador que se va a copiar.

### <a name="remarks"></a>Comentarios

Todos los operadores disminuyen el recuento de referencias para el recurso que posee actualmente `*this` y asignan la propiedad del recurso denominado por la secuencia de operandos a `*this`. Si el recuento de referencias llega a cero, se libera el recurso. Si se produce un error en un `*this` operador, deja sin modificar.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}
```

```Output
*sp == 5
(bool)sp == false
*sp == 10
*sp == 15
```

## <a name="shared_ptr"></a>shared_ptr

Construye un objeto `shared_ptr`.

```cpp
constexpr shared_ptr() noexcept;

constexpr shared_ptr(nullptr_t) noexcept : shared_ptr() {}

shared_ptr(const shared_ptr& sp) noexcept;

shared_ptr(shared_ptr&& sp) noexcept;

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class Deleter>
shared_ptr(
    Other* ptr,
    Deleter deleter);

template <class Deleter>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter);

template <class Other, class Deleter, class Allocator>
shared_ptr(
    Other* ptr,
    Deleter deleter,
    Allocator alloc);

template <class Deleter, class Allocator>
shared_ptr(
    nullptr_t ptr,
    Deleter deleter,
    Allocator alloc);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp) noexcept;

template <class Other>
explicit shared_ptr(
    const weak_ptr<Other>& wp);

template <class &>
shared_ptr(
    std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(
    std::auto_ptr<Other>&& ap);

template <class Other, class Deleter>
shared_ptr(
    unique_ptr<Other, Deleter>&& up);

template <class Other>
shared_ptr(
    const shared_ptr<Other>& sp,
    element_type* ptr) noexcept;

template <class Other>
shared_ptr(
    shared_ptr<Other>&& sp,
    element_type* ptr) noexcept;

template <class Other, class Deleter>
shared_ptr(
    const unique_ptr<Other, Deleter>& up) = delete;
```

### <a name="parameters"></a>Parámetros

*Distinta*\
Tipo controlado por el puntero de argumento.

*anota*\
Puntero que se va a copiar.

*Eliminador*\
Tipo del eliminador.

*Asignador*\
Tipo del asignador.

*Eliminador*\
Eliminador.

*Alloc*\
Asignador.

*dañado*\
El puntero inteligente que se va a copiar.

*WP*\
El puntero débil.

*aislamiento*\
El puntero automático que se va a copiar.

### <a name="remarks"></a>Comentarios

Los constructores crean un objeto que posee el recurso denominado por la secuencia de operandos. El constructor `shared_ptr(const weak_ptr<Other>& wp)` produce un objeto de excepción de tipo [bad_weak_ptr](bad-weak-ptr-class.md) si `wp.expired()`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}
```

```Output
(bool)sp0 == false
*sp1 == 5
*sp2 == 10
*sp3 == 10
*sp4 == 10
*sp5 == 15
```

## <a name="dtorshared_ptr"></a>~ shared_ptr

Destruye un objeto `shared_ptr`.

```cpp
~shared_ptr();
```

### <a name="remarks"></a>Comentarios

El destructor disminuye el recuento de referencias para el recurso que posee actualmente `*this`. Si el recuento de referencias llega a cero, se libera el recurso.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
use count == 1
*sp2 == 5
use count == 2
use count == 1
```

## <a name="swap"></a>pasar

Intercambia dos objetos `shared_ptr`.

```cpp
void swap(shared_ptr& sp) noexcept;
```

### <a name="parameters"></a>Parámetros

*dañado*\
El puntero compartido que se va a intercambiar.

### <a name="remarks"></a>Comentarios

La función miembro deja el recurso que `*this` poseía originalmente el *SP*, y el recurso originalmente perteneciente a *SP* es propiedad de. `*this` La función no modifica los recuentos de referencia para los dos recursos y no inicia ninguna excepción.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5
*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="unique"></a>espeficarse

Comprueba si el recurso propio es único. Esta función quedó en desuso en C++ 17 y se quitó en C++ 20.

```cpp
bool unique() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve **true** si ningún otro `shared_ptr` objeto posee el recurso `*this`que es propiedad de; de lo contrario, es **false**.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}
```

```Output
sp1.unique() == true
sp1.unique() == false
```

## <a name="use_count"></a>use_count

Cuenta los números de propietarios del recurso.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de objetos `shared_ptr` que poseen el recurso que es propiedad de `*this`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__shared_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}
```

```Output
sp1.use_count() == 1
sp1.use_count() == 2
```

## <a name="weak_type"></a>weak_type

El tipo de un puntero débil a un elemento.

```cpp
using weak_type = weak_ptr<T>; // C++17
```

### <a name="remarks"></a>Comentarios

La `weak_type` definición se agregó en c++ 17.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[unique_ptr](unique-ptr-class.md)\
[clase weak_ptr](weak-ptr-class.md)
