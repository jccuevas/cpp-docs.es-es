---
title: auto_ptr (Clase)
ms.date: 11/04/2016
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
ms.openlocfilehash: 14841662235f075d74120673208dd54531763c09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456710"
---
# <a name="autoptr-class"></a>auto_ptr (Clase)

Encapsula un puntero inteligente en torno a un recurso que garantiza que el recurso se destruye automáticamente cuando el control abandona un bloque.

La clase `unique_ptr` de mayor capacidad reemplaza a `auto_ptr`. Para más información, vea [unique_ptr (Clase)](../standard-library/unique-ptr-class.md).

Para más información sobre `throw()` y el control de excepciones, vea [Especificaciones de excepciones (throw)](../cpp/exception-specifications-throw-cpp.md).

## <a name="syntax"></a>Sintaxis

```cpp
class auto_ptr {
    typedef Type element_type;
    explicit auto_ptr(Type* ptr = 0) throw();
    auto_ptr(auto_ptr<Type>& right) throw()
        ;
    template <class Other>
    operator auto_ptr<Other>() throw();
    template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
    template <class Other>
    auto_ptr(auto_ptr<Other>& right);
    auto_ptr<Type>& operator=(auto_ptr<Type>& right);
    ~auto_ptr();
    Type& operator*() const throw();
    Type * operator->()const throw();
    Type *get() const throw();
    Type *release()throw();
    void reset(Type* ptr = 0);
};
```

### <a name="parameters"></a>Parámetros

*correcta*\
`auto_ptr` desde el que se va a obtener un recurso existente.

*anota*\
Puntero especificado para reemplazar el puntero almacenado.

## <a name="remarks"></a>Comentarios

La clase de plantilla describe un puntero inteligente, denominado `auto_ptr`, a un objeto asignado. El puntero debe ser nulo o designar un objeto asignado por **New**. `auto_ptr` transfiere la propiedad si su valor almacenado se asigna a otro objeto. (Reemplaza el valor almacenado después de una transferencia con un puntero nulo). El destructor de `auto_ptr<Type>` elimina el objeto asignado. `auto_ptr<Type>` garantiza que un objeto asignado se elimina automáticamente cuando el control abandona un bloque, incluso a través de una excepción producida. No debe construir dos objetos `auto_ptr<Type>` que posean el mismo objeto.

Puede pasar un objeto `auto_ptr<Type>` por valor como argumento a una llamada de función. `auto_ptr` no puede ser un elemento de ningún contenedor de la biblioteca estándar. No puede administrar de manera fiable una secuencia de objetos `auto_ptr<Type>` con un contenedor de la biblioteca estándar de C++.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[auto_ptr](#auto_ptr)|Constructor para los objetos de tipo `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|El tipo es un sinónimo del parámetro de plantilla `Type`.|

### <a name="functions"></a>Funciones

|||
|-|-|
|[get](#get)|La función miembro devuelve el puntero `myptr` almacenado.|
|[release](#release)|El miembro reemplaza el puntero `myptr` almacenado con un puntero nulo y devuelve el puntero almacenado previamente.|
|[reset](#reset)|La función miembro evalúa la expresión `delete myptr`, pero solo si el valor de puntero `myptr` almacenado cambia como consecuencia de la llamada de función. Luego sustituye el puntero almacenado por *ptr*.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator=](#op_eq)|Operador de asignación que transfiere la propiedad de un objeto `auto_ptr` a otro.|
|[operator*](#op_star)|Operador de desreferenciación para objetos de tipo `auto_ptr`.|
|[operator->](#op_arrow)|Operador para permitir el acceso a miembros.|
|[operator auto_ptr\<Other>](#op_auto_ptr_lt_other_gt)|Convierte de un tipo de `auto_ptr` a otro tipo de `auto_ptr`.|
|[operator auto_ptr_ref\<Other>](#op_auto_ptr_ref_lt_other_gt)|Convierte de `auto_ptr` a `auto_ptr_ref`.|

### <a name="auto_ptr"></a>auto_ptr

Constructor para los objetos de tipo `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

#### <a name="parameters"></a>Parámetros

*anota*\
Puntero al objeto que `auto_ptr` encapsula.

*correcta*\
Objeto `auto_ptr` que el constructor va a copiar.

#### <a name="remarks"></a>Comentarios

El primer constructor almacena *ptr* en `myptr`, el puntero almacenado al objeto asignado. El segundo constructor transfiere la propiedad del puntero almacenado a la *derecha*, almacenando *right*. [liberar](#release) en `myptr`.

El tercer constructor se comporta igual que el segundo, salvo que almacena `right`. `ref`. `release`en `myptr`, donde `ref` es la referencia almacenada `right`en.

El constructor de plantilla se comporta igual que el segundo constructor, siempre que un puntero a `Other` se pueda convertir implícitamente en un puntero a. `Type`

#### <a name="example"></a>Ejemplo

```cpp
// auto_ptr_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

void function ( auto_ptr<Int> &pi )
{
   ++( *pi );
   auto_ptr<Int> pi2( pi );
   ++( *pi2 );
   pi = pi2;
}

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   cout << pi->x << endl;
   function( pi );
   cout << pi->x << endl;
}
```

```Output
Constructing 00311AF8
5
7
Destructing 00311AF8
```

### <a name="element_type"></a>element_type

El tipo es un sinónimo del parámetro de plantilla `Type`.

```cpp
typedef Type element  _type;
```

### <a name="get"></a>Obtener

La función miembro devuelve el puntero `myptr` almacenado.

```cpp
Type *get() const throw();
```

#### <a name="return-value"></a>Valor devuelto

Puntero `myptr`almacenado.

#### <a name="example"></a>Ejemplo

```cpp
// auto_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      x = i;
      cout << "Constructing " << ( void* )this  << " Value: " << x << endl;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << " Value: " << x << endl;
   };

   int x;

};

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   pi.reset( new Int( 6 ) );
   Int* pi2 = pi.get ( );
   Int* pi3 = pi.release ( );
   if (pi2 == pi3)
      cout << "pi2 == pi3" << endl;
   delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="op_eq"></a> operator=

Operador de asignación que transfiere la propiedad de un objeto `auto_ptr` a otro.

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>Parámetros

*correcta*\
Objeto de tipo `auto_ptr`.

#### <a name="return-value"></a>Valor devuelto

Referencia a un objeto de tipo `auto_ptr<Type>`.

#### <a name="remarks"></a>Comentarios

La asignación evalúa la expresión `delete myptr`, pero solo si el puntero `myptr` almacenado cambia como resultado de la asignación. A continuación, transfiere la propiedad del puntero almacenado a la *derecha*, mediante *el almacenamiento correcto*. [liberar](#release) en `myptr`. La función devuelve __\*this__.

#### <a name="example"></a>Ejemplo

Para obtener un ejemplo del uso del operador miembro, vea [auto_ptr](#auto_ptr).

### <a name="op_star"></a>Operator

Operador de desreferenciación para objetos de tipo `auto_ptr`.

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>Valor devuelto

Referencia a un objeto de tipo `Type` que posee el puntero.

#### <a name="remarks"></a>Comentarios

El operador de direccionamiento indirecto devuelve `*`[get](#get). Por tanto, el puntero almacenado no debe ser nulo.

#### <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar la función miembro, vea [auto_ptr](#auto_ptr).

### <a name="op_arrow"></a>Operator&gt;

Operador para permitir el acceso a miembros.

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>Valor devuelto

Miembro del objeto que `auto_ptr` posee.

#### <a name="remarks"></a>Comentarios

El operador de selección devuelve [get](#get)`( )`, de modo que la expresión *ap*-> **member** se comporta igual que (*ap*. **get**( ) )-> **member**, donde *ap* es un objeto de clase `auto_ptr`\< **Type**>. Por lo tanto, el puntero almacenado no debe ser null `Type` y debe ser una clase, estructura o tipo de unión con `member` un miembro.

#### <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar la función miembro, vea [auto_ptr](#auto_ptr).

### <a name="op_auto_ptr_lt_other_gt"></a>operador auto_ptr&lt;otro&gt;

Convierte de un tipo de `auto_ptr` a otro tipo de `auto_ptr`.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>Valor devuelto

El operador de conversión de tipo devuelve `auto_ptr` \< **Other**>( **\*this**).

#### <a name="example"></a>Ejemplo

```cpp
// auto_ptr_op_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;
int main()
{
   auto_ptr<int> pi ( new int( 5 ) );
   auto_ptr<const int> pc = ( auto_ptr<const int> )pi;
}
```

### <a name="op_auto_ptr_ref_lt_other_gt"></a>operador auto_ptr_ref&lt;otro&gt;

Convierte de `auto_ptr` a `auto_ptr_ref`.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>Valor devuelto

El operador de conversión de tipo devuelve **auto_ptr_ref**\< **Other**>( **\*this**).

#### <a name="example"></a>Ejemplo

```cpp
// auto_ptr_op_auto_ptr_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class C {
public:
    C(int _i) : m_i(_i) {
    }
    ~C() {
        cout << "~C:  " << m_i << "\n";
    }
    C &operator =(const int &x) {
        m_i = x;
        return *this;
    }
    int m_i;
};
void f(auto_ptr<C> arg) {
};
int main()
{
    const auto_ptr<C> ciap(new C(1));
    auto_ptr<C> iap(new C(2));

    // Error: this implies transfer of ownership of iap's pointer
    // f(ciap);
    f(iap); // compiles, but gives up ownership of pointer

            // here, iap owns a destroyed pointer so the following is bad:
            // *iap = 5; // BOOM

    cout << "main exiting\n";
}
```

```Output
~C:  2
main exiting
~C:  1
```

### <a name="release"></a>emisión

El miembro reemplaza el puntero `myptr` almacenado con un puntero nulo y devuelve el puntero almacenado previamente.

```cpp
Type *release() throw();
```

#### <a name="return-value"></a>Valor devuelto

Puntero almacenado previamente.

#### <a name="remarks"></a>Comentarios

El miembro reemplaza el puntero `myptr` almacenado con un puntero nulo y devuelve el puntero almacenado previamente.

#### <a name="example"></a>Ejemplo

```cpp
// auto_ptr_release.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int() {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;

};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

### <a name="reset"></a>determinado

La función miembro evalúa la expresión `delete myptr`, pero solo si el valor `myptr` de puntero almacenado cambia como resultado de una llamada de función. A continuación, reemplaza el puntero almacenado con `ptr`.

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>Parámetros

*anota*\
Puntero especificado para reemplazar el puntero `myptr`almacenado.

#### <a name="example"></a>Ejemplo

```cpp
// auto_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int()
    {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;
};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="see-also"></a>Vea también

[unique_ptr (Clase)](../standard-library/unique-ptr-class.md)
