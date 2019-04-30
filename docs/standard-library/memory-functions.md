---
title: Funciones &lt;memory&gt;
ms.date: 02/06/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
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
ms.openlocfilehash: 71cae7bfbb8bfc0bef79a087d4450505c2880e5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412857"
---
# <a name="ltmemorygt-functions"></a>Funciones &lt;memory&gt;

||||
|-|-|-|
|[addressof](#addressof)|[align](#align)|[allocate_shared](#allocate_shared)|
|[const_pointer_cast](#const_pointer_cast)|[declare_no_pointers](#declare_no_pointers)|[declare_reachable](#declare_reachable)|
|[default_delete](#default_delete)|[dynamic_pointer_cast](#dynamic_pointer_cast)|[get_deleter](#get_deleter)|
|[get_pointer_safety](#get_pointer_safety)|[get_temporary_buffer](#get_temporary_buffer)|[make_shared](#make_shared)|
|[make_unique](#make_unique)|[owner_less](#owner_less)|[return_temporary_buffer](#return_temporary_buffer)|
|[static_pointer_cast](#static_pointer_cast)|[swap (Biblioteca estándar de C++)](#swap)|[undeclare_no_pointers](#undeclare_no_pointers)|
|[undeclare_reachable](#undeclare_reachable)|[uninitialized_copy](#uninitialized_copy)|[uninitialized_copy_n](#uninitialized_copy_n)|
|[uninitialized_fill](#uninitialized_fill)|[uninitialized_fill_n](#uninitialized_fill_n)|

## <a name="addressof"></a> addressof

Obtiene la dirección real de un objeto.

```cpp
template <class T>
T* addressof(T& Val);
```

### <a name="parameters"></a>Parámetros

*Val*<br/>
Objeto o función para el que se va a obtener la dirección real.

### <a name="return-value"></a>Valor devuelto

La dirección real del objeto o función al que hace referencia *Val*, incluso si una sobrecarga `operator&()` existe.

### <a name="remarks"></a>Comentarios

## <a name="align"></a> align

Encaja el almacenamiento del tamaño especificado, alineado según la especificación de alineación indicada, en la primera dirección posible del almacenamiento especificado.

```cpp
void* align(
    size_t Alignment, // input
    size_t Size,      // input
    void*& Ptr,        // input/output
    size_t& Space     // input/output
);
```

### <a name="parameters"></a>Parámetros

*Alineación*<br/>
Límite de alineación que se va a intentar.

*Size*<br/>
Tamaño en bytes del almacenamiento alineado.

*Ptr*<br/>
Dirección inicial del bloque de almacenamiento contiguo disponible que se va a usar. Este parámetro también es un parámetro de salida y se establece para que contenga la nueva dirección inicial si la alineación se realiza correctamente. Si `align()` no se realiza correctamente, este parámetro no se modifica.

*Espacio*<br/>
Espacio total disponible para `align()` que se va a usar para crear el almacenamiento alineado. Este parámetro también es un parámetro de salida, y contiene espacio ajustado que queda en el búfer de almacenamiento después de restar el almacenamiento alineado y cualquier sobrecarga asociada.

Si `align()` no se realiza correctamente, este parámetro no se modifica.

### <a name="return-value"></a>Valor devuelto

Un puntero nulo si el búfer alineado solicitado no cabría en el espacio disponible; en caso contrario, el nuevo valor de *Ptr*.

### <a name="remarks"></a>Comentarios

Modificado *Ptr* y *espacio* parámetros permiten llamar a `align()` varias veces en el mismo búfer, posiblemente con valores diferentes para *alineación* y  *Tamaño*. En el fragmento de código siguiente se muestra un uso de `align()`.

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

## <a name="allocate_shared"></a> allocate_shared

Crea un elemento `shared_ptr` en objetos asignados y construidos para un tipo determinado mediante un asignador especificado. Devuelve `shared_ptr`.

```cpp
template <class Type, class Allocator, class... Types>
shared_ptr<Type>
allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Parámetros

*Alloc*<br/>
Asignador usado para crear objetos.

*Args*<br/>
Cero o más argumentos que se convierten en los objetos.

### <a name="remarks"></a>Comentarios

La función crea el objeto `shared_ptr<Type>`, un puntero a `Type(Args...)` asignado y construido por *Alloc*.

## <a name="const_pointer_cast"></a> const_pointer_cast

Constante convertida a shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo controlado por el puntero compartido devuelto.

*Otros problemas*<br/>
Tipo controlado por el puntero compartido de argumento.

*Otros problemas*<br/>
Puntero compartido de argumento.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve un objeto shared_ptr vacío si `const_cast<Ty*>(sp.get())` devuelve un puntero nulo; en caso contrario, devuelve un [shared_ptr (clase)](../standard-library/shared-ptr-class.md)\<Ty > objeto que posee el recurso al que pertenece a `sp`. La expresión `const_cast<Ty*>(sp.get())` debe ser válida.

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

## <a name="declare_no_pointers"></a> declare_no_pointers

Informa a un recolector de elementos no usados de que los caracteres del bloque de memoria definidos por un puntero de dirección base y el tamaño del bloque no contienen punteros rastreables.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*ptr*|Dirección del primer carácter que ya no contiene punteros rastreables.|
|*_Size*|Tamaño de bloque que comienza por *ptr* que no contiene punteros rastreables.|

### <a name="remarks"></a>Comentarios

La función informa a cualquier recolector de elementos no utilizados que el intervalo de direcciones `[ ptr, ptr + _Size)` ya no contienen punteros rastreables. (Todos los punteros a almacenamiento asignado no deben desreferenciar a menos que haga accesible.)

## <a name="declare_reachable"></a> declare_reachable

Informa a la recolección de elementos no utilizados de que la dirección indicada es para el almacenamiento asignado y es accesible.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
Un puntero para un área de almacenamiento válida, asignada, accesible.

### <a name="remarks"></a>Comentarios

Si *ptr* no es null, la función informa a cualquier recolector de elementos no utilizados que *ptr* en lo sucesivo es accesible (señala el almacenamiento asignado válido).

## <a name="default_delete"></a> default_delete

Elimina los objetos asignados con **new (operador)**. Apto para el uso con `unique_ptr`.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
   default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Parámetros

*Ptr*<br/>
Puntero al objeto que se va a eliminar.

*Otros problemas*<br/>
Tipo de los elementos de la matriz que se va a borrar.

### <a name="remarks"></a>Comentarios

La clase de plantilla describe un `deleter` que elimina objetos escalares asignados con **new (operador)**, adecuado para su uso con la clase de plantilla `unique_ptr`. También tiene la especialización explícita `default_delete<Type[]>`.

## <a name="dynamic_pointer_cast"></a> dynamic_pointer_cast

Conversión dinámica a shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo controlado por el puntero compartido devuelto.

*Otros problemas*<br/>
Tipo controlado por el puntero compartido de argumento.

*sp*<br/>
Puntero compartido de argumento.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve un objeto shared_ptr vacío si `dynamic_cast<Ty*>(sp.get())` devuelve un puntero nulo; en caso contrario, devuelve un [shared_ptr (clase)](../standard-library/shared-ptr-class.md)\<Ty > objeto que posee el recurso al que pertenece a *sp* . La expresión `dynamic_cast<Ty*>(sp.get())` debe ser válida.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="get_deleter"></a>  get_deleter

Obtiene el eliminador de shared_ptr.

```cpp
template <class D, class Ty>
D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parámetros

*D*<br/>
Tipo del eliminador.

*Ty*<br/>
Tipo controlado por el puntero compartido.

*sp*<br/>
El puntero compartido.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve un puntero al eliminador de tipo *d.* que pertenece a la [shared_ptr (clase)](../standard-library/shared-ptr-class.md) objeto *sp*. Si *sp* no tiene eliminador o si su eliminador no es de tipo *d.* la función devuelve 0.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct deleter
{
    void operator()(base *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->val = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->val = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a> get_pointer_safety

Devuelve el tipo de seguridad del puntero asumido por cualquier recolector de elementos no utilizados.

```cpp
pointer_safety get_pointer_safety();
```

### <a name="remarks"></a>Comentarios

La función devuelve el tipo de seguridad del puntero asumido por cualquier recolector de elementos no utilizados automática.

## <a name="get_temporary_buffer"></a> get_temporary_buffer

Asigna almacenamiento temporal para una secuencia de elementos que no supere un número especificado de elementos.

```cpp
template <class Type>
pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Parámetros

*count*<br/>
El número máximo de elementos solicitados para los que va a asignarse la memoria.

### <a name="return-value"></a>Valor devuelto

Un `pair` cuyo primer componente es un puntero a la memoria que se ha asignado, y cuyo segundo componente proporciona el tamaño del búfer, que indica el número máximo de elementos que puede almacenar.

### <a name="remarks"></a>Comentarios

La función realiza una solicitud para la memoria y puede que no se realice correctamente. Si no se asigna ningún búfer, entonces la función devuelve un par, con el segundo componente igual a cero y el primer componente igual al puntero nulo.

Esta función solo debe usarse en una memoria que sea temporal.

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
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

## <a name="make_shared"></a> make_shared

Crea y devuelve un `shared_ptr` que apunta a los objetos asignados que se construyen a partir de cero o más argumentos mediante el asignador predeterminado. Asigna y crea tanto un objeto del tipo especificado como un `shared_ptr` para administrar una propiedad compartida del objeto y devuelve el elemento `shared_ptr`.

```cpp
template <class Type, class... Types>
shared_ptr<Type>
make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Args*|Cero o más argumentos de constructor. La función deduce qué sobrecarga de constructor invocar según los argumentos que se proporcionan.|

### <a name="remarks"></a>Comentarios

Use `make_shared` como una manera más eficaz y sencilla de crear un objeto y un `shared_ptr` para administrar el acceso compartido al objeto al mismo tiempo. Semánticamente, estas dos instrucciones son equivalentes:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Sin embargo, la primera instrucción hace dos asignaciones y, si en la asignación de `shared_ptr` se produce un error después de que la asignación del objeto `Example` se haya realizado correctamente, el objeto `Example` sin nombre se pierde. La instrucción que usa `make_shared` es más sencilla porque hay solo una llamada a función implicada. Es más eficaz porque la biblioteca puede realizar una única asignación para tanto el objeto como el puntero inteligente. Esto es más rápido y genera menos fragmentación de la memoria y no hay ninguna posibilidad de una excepción en una asignación, pero no en la otra. El rendimiento mejora por el mejor emplazamiento del código que hace referencia al objeto y que actualiza los recuentos de referencia en el puntero inteligente.

Considere el uso de [make_unique](../standard-library/memory-functions.md#make_unique) si no necesita acceso compartido al objeto. Use [allocate_shared](../standard-library/memory-functions.md#allocate_shared) si necesita especificar un asignador personalizado para el objeto. No puede usar `make_shared` si el objeto requiere un eliminador personalizado, porque no hay ninguna manera de pasar el eliminador como argumento.

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

void CreateSharedPointers() {
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
   for (auto&& sp : playlist) {
      std::wcout << L"Playing " << sp->title_ <<
         L" by " << sp->artist_ << L", use count: " <<
         sp.use_count() << std::endl;
   }
}

int main() {
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

## <a name="make_unique"></a> make_unique

Crea y devuelve un elemento [unique_ptr](../standard-library/unique-ptr-class.md) a un objeto del tipo especificado, que se construye con los argumentos especificados.

```cpp
// make_unique<T>
template <class T, class... Types>
unique_ptr<T>
make_unique(Types&&... Args)
{
    return (unique_ptr<T>(new T(forward<Types>(Args)...)));
}

// make_unique<T[]>
template <class T>
make_unique(size_t Size)
{
    return (unique_ptr<T>(new Elem[Size]()));
}

// make_unique<T[N]> disallowed
template <class T, class... Types>
typename enable_if<extent<T>::value != 0, void>::type
make_unique(Types&&...) = delete;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del objeto al que apuntará el `unique_ptr`.

*Tipos*<br/>
Los tipos de los argumentos de constructor especificados por *Args*.

*Args*<br/>
Los argumentos que se pasarán al constructor del objeto de tipo *T*.

*Elem*<br/>
Una matriz de elementos de tipo *T*.

*Size*<br/>
Número de elementos para los que se va a asignar espacio en la nueva matriz.

### <a name="remarks"></a>Comentarios

La primera sobrecarga se utiliza para objetos individuales, la segunda sobrecarga se invoca para las matrices y la tercera sobrecarga impide que pueda especificar un tamaño de matriz en el argumento de tipo (make_unique\<T [N] >); esta construcción no es compatible con la actual estándar. Cuando se utiliza `make_unique` para crear un `unique_ptr` para una matriz, se deben inicializar los elementos de la matriz por separado. Si está considerando la posibilidad de usar esta sobrecarga, quizás sea mejor usar [std::vector](../standard-library/vector-class.md).

Puesto que `make_unique` se implementa con cuidado para la seguridad de las excepciones, se recomienda utilizar `make_unique` en lugar de llamar directamente a los constructores de `unique_ptr`.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `make_unique`. Para obtener más ejemplos, vea [Cómo: Crear y usar instancias de unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Cuando aparezca el error C2280 con respecto a un `unique_ptr`, es casi seguro que está intentando invocar su constructor de copias, que es una función eliminada.

## <a name="owner_less"></a> owner_less

Permite realizar comparaciones mixtas basadas en la propiedad de punteros compartidos y parciales. Devuelve **true** si el parámetro izquierdo se ordena antes de parámetro derecho mediante la función miembro `owner_before`.

```cpp
template <class Type>
struct owner_less; // not defined

template <class Type>
struct owner_less<shared_ptr<Type>> {
    bool operator()(
    const shared_ptr<Type>& left,
    const shared_ptr<Type>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Type>& right);
};

template <class Type>
struct owner_less<weak_ptr<Type>>
    bool operator()(
    const weak_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Ty>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);
};
```

### <a name="parameters"></a>Parámetros

*_left*<br/>
Un puntero compartido o no seguro.

*right*<br/>
Un puntero compartido o no seguro.

### <a name="remarks"></a>Comentarios

Las clases de plantilla definen todos sus operadores miembro al devolver `left.owner_before(right)`.

## <a name="return_temporary_buffer"></a> return_temporary_buffer

Desasigna la memoria temporal que se asignó mediante la función de plantilla `get_temporary_buffer`.

```cpp
template <class Type>
void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Parámetros

*_Pbuf*<br/>
Un puntero a la memoria que se va a desasignar.

### <a name="remarks"></a>Comentarios

Esta función solo debe usarse en una memoria que sea temporal.

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300 };
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
   return_temporary_buffer ( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a> static_pointer_cast

Conversión estática a shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo controlado por el puntero compartido devuelto.

*Otros problemas*<br/>
Tipo controlado por el puntero compartido de argumento.

*Otros problemas*<br/>
Puntero compartido de argumento.

### <a name="remarks"></a>Comentarios

La función de plantilla devuelve un objeto shared_ptr vacío si `sp` está vacío `shared_ptr` objeto; en caso contrario, devuelve un [shared_ptr (clase)](../standard-library/shared-ptr-class.md)\<Ty > objeto que posee el recurso al que pertenece a `sp`. La expresión `static_cast<Ty*>(sp.get())` debe ser válida.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="swap"></a> swap (Biblioteca estándar de C++)

Intercambiar dos objetos shared_ptr o weak_ptr.

```cpp
template <class Ty, class Other>
void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo controlado por el puntero compartido/débil izquierdo.

*Otros problemas*<br/>
Tipo controlado por el puntero compartido/débil derecho.

*left*<br/>
Puntero compartido/débil izquierdo.

*right*<br/>
Puntero compartido/débil derecho.

### <a name="remarks"></a>Comentarios

Las funciones de plantilla llaman a `left.swap(right)`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__swap.cpp
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

## <a name="undeclare_no_pointers"></a> undeclare_no_pointers

Informa a un recolector de elementos no utilizados de que los caracteres del bloque de memoria definido por un puntero de dirección base y el tamaño del bloque pueden contener ahora punteros rastreables.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="remarks"></a>Comentarios

La función informa a cualquier recolector de elementos no utilizados que el intervalo de direcciones `[ptr, ptr + _Size)` puede contener ahora punteros rastreables.

## <a name="undeclare_reachable"></a> undeclare_reachable

Revoca una declaración de accesibilidad para una ubicación de memoria especificada.

```cpp
template <class Type>
Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*ptr*|Un puntero a la dirección de memoria que va a declararse como no accesible.|

### <a name="remarks"></a>Comentarios

Si *ptr* no **nullptr**, la función informa a cualquier recolector de elementos no utilizados que *ptr* ya no es accesible. Devuelve un puntero derivados de forma segura que se compara igual a *ptr*.

## <a name="uninitialized_copy"></a> uninitialized_copy

Copia objetos de un intervalo de origen especificado a un intervalo de destino sin inicializar.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Parámetros

*first*<br/>
Iterador de entrada que direcciona el primer elemento del intervalo de origen.

*last*<br/>
Iterador de entrada que direcciona el último elemento del intervalo de origen.

*dest*<br/>
Iterador hacia delante que direcciona el primer elemento del intervalo de destino.

### <a name="return-value"></a>Valor devuelto

Un iterador hacia delante que direcciona la primera posición más allá del intervalo de destino, a menos que el intervalo de origen estaba vacío.

### <a name="remarks"></a>Comentarios

Este algoritmo permite desacoplar la asignación de memoria de la construcción de objetos.

La función de plantilla ejecuta eficazmente:

```cpp
while (first != last) {
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

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
    Integer(int x) : val(x) {}
    int get() { return val; }
private:
    int val;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    int i;
    cout << "The initialized Array contains " << N << " elements: ";
    for (i = 0; i < N; i++)
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

## <a name="uninitialized_copy_n"></a> uninitialized_copy_n

Crea una copia de un número especificado de elementos de un iterador de entrada. Las copias se colocan en un iterador hacia delante.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parámetros

*first*<br/>
Iterador de entrada que hace referencia al objeto que se va a copiar.

*count*<br/>
Tipo entero con signo o sin signo que especifica el número de veces que se va a copiar el objeto.

*dest*<br/>
Iterador hacia delante que hace referencia a dónde van las nuevas copias.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que direcciona la primera posición más allá del destino. Si el intervalo de origen estaba vacío, el iterador direcciona *primera*.

### <a name="remarks"></a>Comentarios

La función de plantilla ejecuta lo siguiente:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

## <a name="uninitialized_fill"></a> uninitialized_fill

Copia objetos de un valor especificado en un intervalo de destino sin inicializar.

```cpp
template <class ForwardIterator, class Type>
void uninitialized_fill(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>Parámetros

*first*<br/>
Un iterador hacia delante que direcciona el primer elemento del intervalo de destino que se va a iniciar.

*last*<br/>
Un iterador hacia delante que direcciona el último elemento del intervalo de destino que se va a iniciar.

*val*<br/>
Valor que se usará para inicializar el intervalo de destino.

### <a name="remarks"></a>Comentarios

Este algoritmo permite desacoplar la asignación de memoria de la construcción de objetos.

La función de plantilla ejecuta eficazmente:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (val);
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

### <a name="example"></a>Ejemplo

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer {         // No default constructor
   public:
      Integer( int x ) : val( x ) {}
      int get( ) { return val; }
   private:
      int val;
};

int main( )
{
   const int N = 10;
   Integer val ( 25 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill( Array, Array + N, val );
   int i;
   cout << "The initialized Array contains: ";
      for ( i = 0 ; i < N; i++ )
      {
         cout << Array [ i ].get( ) << " ";
      }
   cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a> uninitialized_fill_n

Copia objetos de un valor especificado en un número especificado de elementos a un intervalo de destino sin inicializar.

```cpp
template <class FwdIt, class Size, class Type>
void uninitialized_fill_n(ForwardIterator first, Size count, const Type& val);
```

### <a name="parameters"></a>Parámetros

*first*<br/>
Iterador hacia delante que direcciona el primer elemento del intervalo de destino que se va a iniciar.

*count*<br/>
Número de elementos que se van a inicializar.

*val*<br/>
Valor que se usará para inicializar el intervalo de destino.

### <a name="remarks"></a>Comentarios

Este algoritmo permite desacoplar la asignación de memoria de la construcción de objetos.

La función de plantilla ejecuta eficazmente:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(val);
```

a menos que el código produzca una excepción. En ese caso, se destruyen todos los objetos construidos y la vuelve a producir excepción.

### <a name="example"></a>Ejemplo

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer {   // No default constructor
public:
   Integer( int x ) : val( x ) {}
   int get( ) { return val; }
private:
   int val;
};

int main() {
   const int N = 10;
   Integer val ( 60 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill_n( Array, N, val );  // C4996
   int i;
   cout << "The uninitialized Array contains: ";
   for ( i = 0 ; i < N; i++ )
      cout << Array [ i ].get( ) <<  " ";
}
```

## <a name="see-also"></a>Vea también

[\<memory>](../standard-library/memory.md)<br/>
