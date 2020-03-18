---
title: Operadores &lt;memory&gt;
ms.date: 11/04/2016
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
ms.openlocfilehash: 661f1bb4c0f5734d88dd23f73c69b362f59a76c2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425494"
---
# <a name="ltmemorygt-operators"></a>Operadores &lt;memory&gt;

## <a name="op_neq"></a>operador! =

Comprueba la desigualdad entre objetos.

```cpp
template <class Type, class Other>
bool operator!=(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>
bool operator!=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator!=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Uno de los objetos cuya desigualdad se va a comprobar.

\ *derecha*
Uno de los objetos cuya desigualdad se va a comprobar.

\ *Ty1*
Tipo controlado por el puntero compartido izquierdo.

\ *Ty2*
Tipo controlado por el puntero compartido derecho.

### <a name="return-value"></a>Valor devuelto

**true** si los objetos no son iguales y **false** si son iguales.

### <a name="remarks"></a>Observaciones

El primer operador de la plantilla devuelve false. (Todos los asignadores predeterminados son iguales).

El segundo y el tercer operador de la plantilla devuelven `!(left == right)`.

### <a name="example"></a>Ejemplo

```cpp
// memory_op_me.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<double> Alloc;
   vector <char>:: allocator_type v1Alloc;

   if ( Alloc != v1Alloc )
      cout << "The allocator objects Alloc & v1Alloc not are equal."
           << endl;
   else
      cout << "The allocator objects Alloc & v1Alloc are equal."
           << endl;
}
```

```Output
The allocator objects Alloc & v1Alloc are equal.
```

### <a name="example"></a>Ejemplo

```cpp
// std__memory__operator_ne.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 != sp0 == " << std::boolalpha
        << (sp0 != sp0) << std::endl;
    std::cout << "sp0 != sp1 == " << std::boolalpha
        << (sp0 != sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 != sp0 == false
sp0 != sp1 == true
```

## <a name="op_eq_eq"></a>operador = =

Comprueba la igualdad entre objetos.

```cpp
template <class Type, class Other>
bool operator==(
    const allocator<Type>& left,
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>
bool operator==(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>
bool operator==(
    const shared_ptr<Ty1>& left;,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Uno de los objetos cuya igualdad se va a comprobar.

\ *derecha*
Uno de los objetos cuya igualdad se va a comprobar.

\ *Ty1*
Tipo controlado por el puntero compartido izquierdo.

\ *Ty2*
Tipo controlado por el puntero compartido derecho.

### <a name="return-value"></a>Valor devuelto

**true** si los objetos son iguales, **false** si los objetos no son iguales.

### <a name="remarks"></a>Observaciones

El primer operador de la plantilla devuelve true. (Todos los asignadores predeterminados son iguales).

El segundo y el tercer operador de la plantilla devuelven `left.get() ==  right.get()`.

### <a name="example"></a>Ejemplo

```cpp
// memory_op_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<char> Alloc;
   vector <int>:: allocator_type v1Alloc;

   allocator<char> cAlloc(Alloc);
   allocator<int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="example"></a>Ejemplo

```cpp
// std__memory__operator_eq.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(0));
    std::shared_ptr<int> sp1(new int(0));

    std::cout << "sp0 == sp0 == " << std::boolalpha
        << (sp0 == sp0) << std::endl;
    std::cout << "sp0 == sp1 == " << std::boolalpha
        << (sp0 == sp1) << std::endl;

    return (0);
    }
```

```Output
sp0 == sp0 == true
sp0 == sp1 == false
```

## <a name="op_gt_eq"></a>operador&gt;=

Comprueba si un objeto es mayor o igual que un segundo objeto.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator>=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>
bool operator>=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Uno de los objetos que se va a comparar.

\ *derecha*
Uno de los objetos que se va a comparar.

\ *Ty1*
Tipo controlado por el puntero compartido izquierdo.

\ *Ty2*
Tipo controlado por el puntero compartido derecho.

### <a name="remarks"></a>Observaciones

Los operadores de plantilla devuelven `left.get() >= right.get()`.

## <a name="op_lt"></a> operator&lt;

Comprueba si un objeto es menor que un segundo objeto.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Uno de los objetos que se va a comparar.

\ *derecha*
Uno de los objetos que se va a comparar.

\ *Ty1*
Tipo controlado por el puntero izquierdo.

\ *Ty2*
Tipo controlado por el puntero derecho.

## <a name="op_lt_eq"></a>operador&lt;=

Comprueba si un objeto es menor o igual que un segundo objeto.

```cpp
template <class T, class Del1, class U, class Del2>
bool operator<=(
    const unique_ptr<T, Del1>& left,
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>
bool operator<=(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Uno de los objetos que se va a comparar.

\ *derecha*
Uno de los objetos que se va a comparar.

\ *Ty1*
Tipo controlado por el puntero compartido izquierdo.

\ *Ty2*
Tipo controlado por el puntero compartido derecho.

### <a name="remarks"></a>Observaciones

Los operadores de plantilla devuelven `left.get() <= right.get()`

## <a name="op_gt"></a> operator&gt;

Comprueba si un objeto es mayor que un segundo objeto.

```cpp
template <class Ty1, class Del1, class Ty2, class Del2>
bool operator>(
    const unique_ptr<Ty1, Del1>& left,
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>
bool operator>(
    const shared_ptr<Ty1>& left,
    const shared_ptr<Ty2>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Uno de los objetos que se va a comparar.

\ *derecha*
Uno de los objetos que se va a comparar.

\ *Ty1*
Tipo controlado por el puntero compartido izquierdo.

\ *Ty2*
Tipo controlado por el puntero compartido derecho.

## <a name="op_lt_lt"></a>operador&lt;&lt;

Escribe el puntero compartido en la secuencia.

```cpp
template <class Elem, class Tr, class Ty>
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,
    shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parámetros

\ *Elem*
El tipo del elemento de secuencia.

*Tr*\
El tipo de rasgos del elemento de secuencia.

\ *Ty*
Tipo controlado por el puntero compartido.

*out*\
Secuencia de salida.

\ *SP*
El puntero compartido.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve `out << sp.get()`.

### <a name="example"></a>Ejemplo

```cpp
// std__memory__operator_sl.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;

    return (0);
    }
```

```Output
sp0 == 3f3040 (varies)
```
