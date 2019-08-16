---
title: weak_ptr (Clase)
ms.date: 07/29/2019
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
ms.openlocfilehash: d4ba30f737bc570a4ee700b3a317b5feebe8a50a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682409"
---
# <a name="weakptr-class"></a>weak_ptr (Clase)

Contiene un puntero débilmente vinculado.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo controlado por el puntero débil.

## <a name="remarks"></a>Comentarios

La clase de plantilla describe un objeto que apunta a un recurso administrado por uno o más objetos [shared_ptr](shared-ptr-class.md) . Los `weak_ptr` objetos que apuntan a un recurso no afectan al recuento de referencias del recurso. Cuando se destruye `shared_ptr` el último objeto que administra ese recurso, el recurso se liberará, aunque `weak_ptr` haya objetos que señalen a ese recurso. Este comportamiento es esencial para evitar ciclos en estructuras de datos.

Un objeto `weak_ptr` apunta a un recurso si se construyó a partir de un objeto `shared_ptr` que posee ese recurso, si se construyó a partir de un objeto `weak_ptr` que apunta a ese recurso o si se le asignó ese recurso con [operator=](#op_eq). Un `weak_ptr` objeto no proporciona acceso directo al recurso al que apunta. El código que debe usar el recurso lo hace a través de un objeto `shared_ptr` que posee ese recurso, creado mediante una llamada a la función miembro [lock](#lock). Un `weak_ptr` objeto ha expirado cuando el recurso al que apunta se ha liberado porque todos los `shared_ptr` objetos que poseen el recurso se han destruido. Llamar a `lock` en un objeto `weak_ptr` que ha expirado crea un objeto shared_ptr vacío.

Un objeto weak_ptr vacío no apunta a ningún recurso y no tiene ningún bloque de control. Su función miembro `lock` devuelve un objeto shared_ptr vacío.

Un ciclo se produce cuando dos o más recursos controlados por objetos `shared_ptr` contienen objetos `shared_ptr` que se hacen referencia mutuamente. Por ejemplo, una lista vinculada circular con tres elementos tiene un nodo principal `N0`; ese nodo contiene un objeto `shared_ptr` que posee el siguiente nodo, `N1`; ese nodo contiene un objeto `shared_ptr` que posee el siguiente nodo, `N2`; ese nodo, a su vez, contiene un objeto `shared_ptr` que posee el nodo principal, `N0`, que cierra el ciclo. En esta situación, los recuentos de referencias nunca se vuelven cero y los nodos del ciclo nunca se liberan. Para eliminar el ciclo, el último nodo `N2` debe contener un objeto `weak_ptr` que apunte a `N0` en lugar de un objeto `shared_ptr`. Dado que `weak_ptr` el objeto no `N0` posee, no `N0`afecta al recuento de referencias de, y cuando se destruye la última referencia al nodo principal del programa, también se destruirán los nodos de la lista.

## <a name="members"></a>Miembros

|||
|-|-|
| **Constructores** | |
|[weak_ptr](#weak_ptr)|Construye un objeto `weak_ptr`.|
| **Destructores** | |
|[~ weak_ptr](#tilde-weak_ptr)|Construye un objeto `weak_ptr`.|
| **Typedefs** | |
|[element_type](#element_type)|Tipo del elemento.|
| **Funciones miembro** | |
|[expired](#expired)|Comprueba si la propiedad ha caducado.|
|[lock](#lock)|Obtiene la propiedad exclusiva de un recurso.|
|[owner_before](#owner_before)|Devuelve **true** si este `weak_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.|
|[reset](#reset)|Libera el recurso poseído.|
|[swap](#swap)|Intercambia dos objetos `weak_ptr`.|
|[use_count](#use_count)|Cuenta el número `shared_ptr` de objetos.|
| **Operadores** | |
|[operator=](#op_eq)|Reemplaza el recurso poseído.|

## <a name="element_type"></a>element_type

Tipo del elemento.

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `T`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a>expirado

Comprueba si la propiedad ha expirado, es decir, se ha eliminado el objeto al que se hace referencia.

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve **true** si `*this` ha expirado; de lo contrario, **es false**.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a>bloquea

Obtiene un `shared_ptr` que comparte la propiedad de un recurso.

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un objeto [shared_ptr](shared-ptr-class.md) vacío si `*this` ha expirado; de lo contrario, `shared_ptr<T>` devuelve un objeto que posee el `*this` recurso al que apunta. Devuelve un valor equivalente a la ejecución atómica de `expired() ? shared_ptr<T>() : shared_ptr<T>(*this)`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="op_eq"></a> operator=

Reemplaza el recurso poseído.

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>Parámetros

*Distinta*\
Tipo controlado por el puntero compartido o débil del argumento.

*anota*\
Puntero débil o puntero compartido que se va a copiar.

### <a name="remarks"></a>Comentarios

Todos los operadores liberan el recurso al que `*this` apunta actualmente y asignan la propiedad del recurso denominado por `*this` *ptr* a. Si se produce un error en un `*this` operador, deja sin modificar. Cada operador tiene un efecto equivalente a `weak_ptr(ptr).swap(*this)`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a>owner_before

Devuelve **true** si este `weak_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.

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

La función miembro de plantilla devuelve true `*this` si se ordena antes que *ptr*.

## <a name="reset"></a>determinado

Libera el recurso de propiedad.

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro libera el recurso al que `*this` apunta y `*this` convierte en un objeto vacío `weak_ptr` .

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}
```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a>pasar

Intercambia dos objetos `weak_ptr`.

```cpp
void swap(weak_ptr& wp) noexcept;
```

También incluye la especialización:

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>Parámetros

*WP*\
El puntero débil que se va a intercambiar.

### <a name="remarks"></a>Comentarios

`*this` `*this`Después de ,elrecursoalqueapuntaoriginalmenteseapuntaporWPyelrecursoalqueapuntaoriginalmenteelWPapuntaa.`swap` La función no cambia los recuentos de referencias para los dos recursos y no inicia ninguna excepción. El efecto de la especialización de la plantilla es el `a.swap(b)`equivalente de.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_swap.cpp
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

## <a name="use_count"></a>use_count

Cuenta el número de `shared_ptr` objetos que poseen el recurso compartido.

```cpp
long use_count() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de objetos `shared_ptr` que poseen el recurso al que apuntaba `*this`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}
```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a>weak_ptr

Construye un objeto `weak_ptr`.

```cpp
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>Parámetros

*Distinta*\
El tipo controlado por el puntero compartido o débil de argumento. Estos constructores no participan en la resolución de sobrecarga a menos que `element_type*` _otros\*_  sea compatible con.

*WP*\
El puntero débil que se va a copiar.

*dañado*\
El puntero compartido que se va a copiar.

### <a name="remarks"></a>Comentarios

El constructor predeterminado crea un objeto vacío `weak_ptr` . Los constructores que toman un argumento crean un objeto vacío `weak_ptr` si el puntero del argumento está vacío. De lo contrario, construyen un `weak_ptr` objeto que apunta al recurso denominado por el argumento. No se cambia el recuento de referencias del objeto compartido.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="tilde-weak_ptr"></a>~ weak_ptr

Destruye un objeto `weak_ptr`.

```cpp
~weak_ptr();
```

### <a name="remarks"></a>Comentarios

El destructor destruye esto `weak_ptr` pero no tiene ningún efecto en el recuento de referencias del objeto al que apunta su puntero almacenado.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[clase shared_ptr](shared-ptr-class.md)
