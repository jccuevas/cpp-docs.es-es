---
title: Funciones &lt;memory&gt;
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: fa8f0dd7e5588891aeef4fbe04a907fbbfc52b52
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447399"
---
# <a name="ltmemorygt-functions"></a>Funciones &lt;memory&gt;

## <a name="addressof"></a>AddressOf

Obtiene la dirección real de un objeto.

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>Parámetros

*value*\
Objeto o función para el que se va a obtener la dirección real.

### <a name="return-value"></a>Valor devuelto

La dirección real del objeto o la función a la que hace referencia el *valor*, incluso si existe una `operator&()` sobrecargada.

### <a name="remarks"></a>Observaciones

## <a name="align"></a>alinea

Ajusta el almacenamiento del tamaño especificado, alineado según la especificación de alineación indicada, en la primera dirección posible del almacenamiento especificado.

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>Parámetros

\ de *alineación*
Límite de alineación que se va a intentar.

*size*\
Tamaño en bytes del almacenamiento alineado.

\ *ptr*
Dirección inicial del bloque de almacenamiento contiguo disponible que se va a usar. Este parámetro también es un parámetro de salida y se establece para que contenga la nueva dirección de inicio si la alineación se realiza correctamente. Si `align()` no se realiza correctamente, este parámetro no se modifica.

*espacio*\
Espacio total disponible para `align()` que se va a usar para crear el almacenamiento alineado. Este parámetro también es un parámetro de salida, y contiene espacio ajustado que queda en el búfer de almacenamiento después de restar el almacenamiento alineado y cualquier sobrecarga asociada.

Si `align()` no se realiza correctamente, este parámetro no se modifica.

### <a name="return-value"></a>Valor devuelto

Un puntero NULL si el búfer alineado solicitado no cabría en el espacio disponible; de lo contrario, el nuevo valor de *ptr*.

### <a name="remarks"></a>Observaciones

Los parámetros *ptr* y *Space* modificados permiten llamar a `align()` de forma repetida en el mismo búfer, posiblemente con valores diferentes para la *alineación* y *el tamaño*. En el fragmento de código siguiente se muestra un uso de `align()`.

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>allocate_shared

Crea una [shared_ptr](shared-ptr-class.md) a objetos asignados y construidos para un tipo determinado mediante un asignador especificado. Devuelve `shared_ptr`.

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>Parámetros

\ de *asignación*
Asignador usado para crear objetos.

\ *args*
Cero o más argumentos que se convierten en los objetos.

### <a name="remarks"></a>Observaciones

La función crea el objeto `shared_ptr<T>`, un puntero a `T(args...)` como asignado y construido por *Alloc*.

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Constante convertida en [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parámetros

*T*\
Tipo controlado por el puntero compartido devuelto.

*Otros*\
Tipo controlado por el puntero compartido de argumento.

\ *SP*
Puntero compartido de argumento.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve un objeto de `shared_ptr` vacío si `const_cast<T*>(sp.get())` devuelve un puntero nulo. en caso contrario, devuelve un objeto `shared_ptr<T>` que posee el recurso que posee *SP*. La expresión `const_cast<T*>(sp.get())` debe ser válida.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>declare_no_pointers

Informa a un recolector de elementos no usados de que los caracteres del bloque de memoria definidos por un puntero de dirección base y el tamaño del bloque no contienen punteros rastreables.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Dirección del primer carácter que ya no contiene punteros rastreables.

*size*\
Tamaño del bloque que se inicia en *ptr* y que no contiene punteros rastreables.

### <a name="remarks"></a>Observaciones

La función informa a cualquier recolector de elementos no utilizados de que las direcciones del intervalo `[ ptr, ptr + size)` ya no contienen punteros rastreables. (Los punteros al almacenamiento asignado no se deben desreferenciar a menos que se pueda tener acceso a ellos).

## <a name="declare_reachable"></a>declare_reachable

Informa a la recolección de elementos no utilizados de que la dirección indicada es para el almacenamiento asignado y es accesible.

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Un puntero para un área de almacenamiento válida, asignada, accesible.

### <a name="remarks"></a>Observaciones

Si *ptr* no es null, la función informa a cualquier recolector de elementos no utilizados de que *ptr* es ahora accesible, es decir, apunta a un almacenamiento asignado válido.

## <a name="default_delete"></a>default_delete

Elimina los objetos asignados con el **operador New**. Adecuado para su uso con [unique_ptr](unique-ptr-class.md).

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Puntero al objeto que se va a eliminar.

*Otros*\
Tipo de los elementos de la matriz que se va a borrar.

### <a name="remarks"></a>Observaciones

La plantilla de clase describe un eliminador que elimina objetos escalares asignados con el **operador New**, adecuado para su uso con la plantilla de clase `unique_ptr`. También tiene la especialización explícita `default_delete<T[]>`.

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

Igual que `location->~T()`.

## <a name="destroy"></a>borrar

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

Igual que:

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

Igual que:

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

Conversión dinámica a [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parámetros

*T*\
Tipo controlado por el puntero compartido devuelto.

*Otros*\
Tipo controlado por el puntero compartido de argumento.

\ *SP*
Puntero compartido de argumento.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve un objeto de `shared_ptr` vacío si `dynamic_cast<T*>(sp.get())` devuelve un puntero nulo. en caso contrario, devuelve un objeto `shared_ptr<T>` que posee el recurso que posee *SP*. La expresión `dynamic_cast<T*>(sp.get())` debe ser válida.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a>get_deleter

Obtiene el eliminador de un [shared_ptr](shared-ptr-class.md).

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>Parámetros

\ *eliminador*
Tipo del eliminador.

*T*\
Tipo controlado por el puntero compartido.

\ *SP*
El puntero compartido.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve un puntero al eliminador de tipo *eliminador* que pertenece al `shared_ptr` objeto *SP*. Si *SP* no tiene ningún eliminador o si su eliminador no es de tipo *eliminar*, la función devuelve 0.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>get_pointer_safety

Devuelve el tipo de seguridad del puntero asumido por cualquier recolector de elementos no utilizados.

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>Observaciones

La función devuelve el tipo de seguridad del puntero asumido por cualquier recolector de elementos no utilizados automática.

## <a name="get_temporary_buffer"></a>get_temporary_buffer

Asigna almacenamiento temporal para una secuencia de elementos que no supera un número especificado de elementos.

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>Parámetros

*recuento*\
El número máximo de elementos solicitados para los que va a asignarse la memoria.

### <a name="return-value"></a>Valor devuelto

Un `pair` cuyo primer componente es un puntero a la memoria que se ha asignado, y cuyo segundo componente proporciona el tamaño del búfer, que indica el número máximo de elementos que puede almacenar.

### <a name="remarks"></a>Observaciones

La función realiza una solicitud para la memoria y puede que no se realice correctamente. Si no se asigna ningún búfer, entonces la función devuelve un par, con el segundo componente igual a cero y el primer componente igual al puntero nulo.

Use esta función solo para la memoria que sea temporal.

### <a name="example"></a>Ejemplo

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>make_shared

Crea y devuelve un [shared_ptr](shared-ptr-class.md) que apunta a los objetos asignados que se construyen a partir de cero o más argumentos mediante el asignador predeterminado. Asigna y crea tanto un objeto del tipo especificado como un `shared_ptr` para administrar una propiedad compartida del objeto y devuelve el elemento `shared_ptr`.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>Parámetros

\ *args*
Cero o más argumentos de constructor. La función deduce qué sobrecarga de constructor invocar según los argumentos que se proporcionan.

### <a name="remarks"></a>Observaciones

Use `make_shared` como una manera más eficaz y sencilla de crear un objeto y un `shared_ptr` para administrar el acceso compartido al objeto al mismo tiempo. Semánticamente, estas dos instrucciones son equivalentes:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Sin embargo, la primera instrucción hace dos asignaciones y, si en la asignación de `shared_ptr` se produce un error después de que la asignación del objeto `Example` se haya realizado correctamente, el objeto `Example` sin nombre se pierde. La instrucción que usa `make_shared` es más sencilla porque hay solo una llamada a función implicada. Es más eficaz porque la biblioteca puede realizar una única asignación para tanto el objeto como el puntero inteligente. Esta función es más rápida y genera menos fragmentación de la memoria, y no hay ninguna posibilidad de que se produzca una excepción en una asignación, pero no en la otra. El rendimiento mejora por el mejor emplazamiento del código que hace referencia al objeto y que actualiza los recuentos de referencia en el puntero inteligente.

Considere la posibilidad de utilizar [make_unique](memory-functions.md#make_unique) si no necesita acceso compartido al objeto. Use [allocate_shared](memory-functions.md#allocate_shared) si necesita especificar un asignador personalizado para el objeto. No se puede usar `make_shared` si el objeto requiere un eliminador personalizado, porque no hay ninguna manera de pasar el eliminador como argumento.

En el ejemplo siguiente se muestra cómo crear punteros compartidos a un tipo invocando determinadas sobrecargas de constructor.

### <a name="example"></a>Ejemplo

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

El ejemplo produce la siguiente salida:

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>make_unique

Crea y devuelve un elemento [unique_ptr](unique-ptr-class.md) a un objeto del tipo especificado, que se construye con los argumentos especificados.

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>Parámetros

*T*\
Tipo del objeto al que apuntará el `unique_ptr`.

\ *args*
Tipos de los argumentos de constructor especificados por *args*.

\ *args*
Argumentos que se van a pasar al constructor del objeto de tipo *T*.

*elementos*\
Matriz de elementos de tipo *T*.

*size*\
Número de elementos para los que se va a asignar espacio en la nueva matriz.

### <a name="remarks"></a>Observaciones

La primera sobrecarga se utiliza para los objetos únicos. La segunda sobrecarga se invoca para las matrices. La tercera sobrecarga impide especificar un tamaño de matriz en el argumento de tipo (make_unique\<T [N] >); Esta construcción no es compatible con el estándar actual. Cuando se utiliza `make_unique` para crear un `unique_ptr` para una matriz, se deben inicializar los elementos de la matriz por separado. En lugar de usar esta sobrecarga, quizás una mejor opción es usar [STD:: Vector](vector-class.md).

Puesto que `make_unique` se implementa con cuidado para la seguridad de las excepciones, se recomienda utilizar `make_unique` en lugar de llamar directamente a los constructores de `unique_ptr`.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `make_unique`. Para obtener más ejemplos, vea [Cómo: Crear y usar instancias de unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Cuando aparezca el error C2280 con respecto a un `unique_ptr`, es casi seguro que está intentando invocar su constructor de copias, que es una función eliminada.

## <a name="owner_less"></a>owner_less

Permite realizar comparaciones mixtas basadas en la propiedad de punteros compartidos y parciales. Devuelve **true** si el parámetro izquierdo se ordena delante del parámetro Right por la función miembro `owner_before`.

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Un puntero compartido o no seguro.

\ *derecha*
Un puntero compartido o no seguro.

### <a name="remarks"></a>Observaciones

Las plantillas de clase definen todos sus operadores de miembro como si devolvieran `left.owner_before(right)`.

## <a name="reinterpret_pointer_cast"></a>reinterpret_pointer_cast

Crea un nuevo `shared_ptr` a partir de un puntero compartido existente mediante una conversión.

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Referencia a un `shared_ptr<U>`.

### <a name="remarks"></a>Observaciones

Si *ptr* está vacío, el nuevo `shared_ptr` también está vacío; en caso contrario, comparte la propiedad con *ptr*. El nuevo puntero compartido es el resultado de evaluar `reinterpret_cast<Y*>(ptr.get())`, donde se `typename std::shared_ptr<T>::element_type``Y`. El comportamiento es indefinido si `reinterpret_cast<T*>((U*)nullptr)` no tiene el formato correcto.

La función de plantilla que toma una referencia lvalue es nueva en C++ 17. La función de plantilla que toma una referencia rvalue es nueva en C++ 20.

## <a name="return_temporary_buffer"></a>return_temporary_buffer

Desasigna la memoria temporal que se asignó mediante la función de plantilla `get_temporary_buffer`.

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>Parámetros

\ de *búfer*
Un puntero a la memoria que se va a desasignar.

### <a name="remarks"></a>Observaciones

Use esta función solo para la memoria que sea temporal.

### <a name="example"></a>Ejemplo

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

Conversión estática a [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parámetros

*T*\
Tipo controlado por el puntero compartido devuelto.

*Otros*\
Tipo controlado por el puntero compartido de argumento.

\ *SP*
Puntero compartido de argumento.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve un objeto `shared_ptr` vacío si *SP* es un objeto `shared_ptr` vacío; en caso contrario, devuelve un objeto `shared_ptr<T>` que posee el recurso que posee *SP*. La expresión `static_cast<T*>(sp.get())` debe ser válida.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a>pasar

Intercambie dos [shared_ptr](shared-ptr-class.md), [unique_ptr](unique-ptr-class.md)o [weak_ptr](weak-ptr-class.md) objetos.

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>Parámetros

*T*\
Tipo controlado por el puntero de argumento.

\ *eliminador*
Eliminador del tipo de puntero único.

\ *izquierda*
Puntero izquierdo.

\ *derecha*
Puntero a la derecha.

### <a name="remarks"></a>Observaciones

Las funciones de plantilla llaman a `left.swap(right)`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__swap.cpp
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

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

Informa a un recolector de elementos no utilizados de que los caracteres del bloque de memoria definido por un puntero de dirección base y el tamaño del bloque pueden contener ahora punteros rastreables.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Puntero a la dirección de memoria marcada previamente mediante [declare_no_pointers](#declare_no_pointers).

*size*\
El número de bytes en el intervalo de memoria. Este valor debe ser igual al número usado en la llamada `declare_no_pointers`.

### <a name="remarks"></a>Observaciones

La función informa a cualquier recolector de elementos no utilizados que el intervalo de direcciones `[ptr, ptr + size)` puede contener ahora punteros rastreables.

## <a name="undeclare_reachable"></a>undeclare_reachable

Revoca una declaración de disponibilidad para una ubicación de memoria especificada.

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Puntero a la dirección de memoria marcada previamente mediante [declare_reachable](#declare_reachable).

### <a name="remarks"></a>Observaciones

Si *ptr* no es **nullptr**, la función informa a cualquier recolector de elementos no utilizados de que *ptr* ya no es accesible. Devuelve un puntero derivado de forma segura que se compara con igual a *ptr*.

## <a name="uninitialized_copy"></a>uninitialized_copy

Copia objetos de un intervalo de origen especificado a un intervalo de destino sin inicializar.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo de origen.

*última*\
Iterador de entrada que direcciona el último elemento del intervalo de origen.

\ de *destino*
Iterador hacia delante que direcciona el primer elemento del intervalo de destino.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que dirige a la primera posición más allá del intervalo de destino, a menos que el intervalo de origen esté vacío.

### <a name="remarks"></a>Observaciones

Este algoritmo permite desacoplar la asignación de memoria de la construcción de objetos.

La función de plantilla ejecuta eficazmente:

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

La sobrecarga con una directiva de ejecución es nueva en C++ 17.

### <a name="example"></a>Ejemplo

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

Crea una copia de un número especificado de elementos de un iterador de entrada. Las copias se colocan en un iterador hacia delante.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador de entrada que hace referencia al objeto que se va a copiar.

*recuento*\
Tipo entero con signo o sin signo que especifica el número de veces que se va a copiar el objeto.

\ de *destino*
Iterador hacia delante que hace referencia a dónde van las nuevas copias.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que direcciona la primera posición más allá del destino. Si el intervalo de origen estaba vacío, el iterador se dirige *primero*.

### <a name="remarks"></a>Observaciones

La función de plantilla ejecuta eficazmente el código siguiente:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

La sobrecarga con una directiva de ejecución es nueva en C++ 17.

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

El valor predeterminado crea objetos de la `value_type` de iteradores en el intervalo especificado.

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador que direcciona el primer elemento del intervalo que se va a construir.

*última*\
Iterador que se dirige a una posición después del último elemento del intervalo que se va a construir.

### <a name="remarks"></a>Observaciones

La versión sin una directiva de ejecución es realmente la misma que:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

Si se produce una excepción, los objetos construidos previamente se destruyen en un orden no especificado.

La versión con una directiva de ejecución tiene el mismo resultado, pero se ejecuta de acuerdo con la *Directiva*especificada.

Estas funciones son nuevas en C++ 17.

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

Default crea un número especificado de objetos del `value_type`del iterador, comenzando en la ubicación especificada.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador que direcciona el primer elemento del intervalo de destino que se va a construir.

*recuento*\
Recuento de elementos del intervalo de destino que se va a construir.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que dirige a la primera posición más allá del intervalo de destino, a menos que el intervalo de origen esté vacío.

### <a name="remarks"></a>Observaciones

La versión sin una directiva de ejecución es realmente la misma que:

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

Si se produce una excepción, los objetos construidos previamente se destruyen en un orden no especificado.

La versión con una directiva de ejecución tiene el mismo resultado, pero se ejecuta de acuerdo con la *Directiva*especificada.

Estas funciones son nuevas en C++ 17.

## <a name="uninitialized_fill"></a>uninitialized_fill

Copia objetos de un valor especificado en un intervalo de destino sin inicializar.

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador hacia delante que direcciona el primer elemento del intervalo de destino que se va a inicializar.

*última*\
Iterador hacia delante que direcciona el último elemento del intervalo de destino que se va a inicializar.

*value*\
Valor que se usará para inicializar el intervalo de destino.

### <a name="remarks"></a>Observaciones

Este algoritmo permite desacoplar la asignación de memoria de la construcción de objetos.

La función de plantilla ejecuta eficazmente:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

La sobrecarga con una directiva de ejecución es nueva en C++ 17.

### <a name="example"></a>Ejemplo

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

Copia objetos de un valor especificado en el número especificado de elementos de un intervalo de destino sin inicializar.

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador hacia delante que direcciona el primer elemento del intervalo de destino que se va a inicializar.

*recuento*\
Número de elementos que se van a inicializar.

*value*\
Valor que se va a usar para inicializar el intervalo de destino.

### <a name="remarks"></a>Observaciones

Este algoritmo permite desacoplar la asignación de memoria de la construcción de objetos.

La función de plantilla ejecuta eficazmente:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

La sobrecarga con una directiva de ejecución es nueva en C++ 17.

### <a name="example"></a>Ejemplo

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

Mueve los elementos de un intervalo de origen a un área de memoria de destino sin inicializar.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo de origen que se va a trasladar.

*última*\
Iterador de entrada que se dirige a una posición después del último elemento del intervalo de origen que se va a trasladar.

\ de *destino*
Inicio del intervalo de destino.

### <a name="remarks"></a>Observaciones

La versión sin una directiva de ejecución es realmente la misma que:

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

Si se produce una excepción, es posible que algunos objetos del intervalo de origen se queden en un estado válido pero no especificado. Los objetos construidos previamente se destruyen en un orden no especificado.

La versión con una directiva de ejecución tiene el mismo resultado, pero se ejecuta de acuerdo con la *Directiva*especificada.

Estas funciones son nuevas en C++ 17.

## <a name="uninitialized_move_n"></a>uninitialized_move_n

Mueve un número especificado de elementos de un intervalo de origen a un área de memoria de destino sin inicializar.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo de origen que se va a trasladar.

*recuento*\
Recuento de elementos del intervalo de origen que se van a trasladar.

\ de *destino*
Inicio del intervalo de destino.

### <a name="remarks"></a>Observaciones

La versión sin una directiva de ejecución es realmente la misma que:

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

Si se produce una excepción, es posible que algunos objetos del intervalo de origen se queden en un estado válido pero no especificado. Los objetos construidos previamente se destruyen en un orden no especificado.

La versión con una directiva de ejecución tiene el mismo resultado, pero se ejecuta de acuerdo con la *Directiva*especificada.

Estas funciones son nuevas en C++ 17.

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

Construye objetos de la `value_type` de iteradores por inicialización de valor, en el intervalo especificado.

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador que direcciona el primer elemento de la construcción de intervalo a valor.

*última*\
Iterador que se dirige a una posición después del último elemento de la construcción de intervalo a valor.

### <a name="remarks"></a>Observaciones

La versión sin una directiva de ejecución es realmente la misma que:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

Si se produce una excepción, los objetos construidos previamente se destruyen en un orden no especificado.

La versión con una directiva de ejecución tiene el mismo resultado, pero se ejecuta de acuerdo con la *Directiva*especificada.

Si se produce un error de asignación de memoria, se produce una excepción `std::bad_alloc`.

Estas funciones son nuevas en C++ 17.

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

Construye un número especificado de objetos del `value_type` del iterador por inicialización de valor, comenzando en la ubicación especificada.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parámetros

\ de *Directiva*
Directiva de ejecución que se va a usar.

*primer*\
Iterador que direcciona el primer elemento del intervalo de destino que se va a construir.

*recuento*\
Recuento de elementos del intervalo de destino que se va a construir.

### <a name="remarks"></a>Observaciones

La versión sin una directiva de ejecución es realmente la misma que:

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

Si se produce una excepción, los objetos construidos previamente se destruyen en un orden no especificado.

La versión con una directiva de ejecución tiene el mismo resultado, pero se ejecuta de acuerdo con la *Directiva*especificada.

Si se produce un error de asignación de memoria, se produce una excepción `std::bad_alloc`.

Estas funciones son nuevas en C++ 17.

## <a name="uses_allocator_v"></a>uses_allocator_v

Una plantilla de variable auxiliar para tener acceso al valor de la plantilla `uses_allocator`.

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>Consulte también

[\<memory>](memory.md)
