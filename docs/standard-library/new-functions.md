---
title: Funciones &lt;new&gt;
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243660"
---
# <a name="ltnewgt-functions"></a>Funciones &lt;new&gt;

## <a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Comentarios

Devuelve el valor actual `new_handler`.

## <a name="launder"></a> Lave

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Parámetros

*PTR*\
La dirección de un byte en la memoria que contiene un objeto cuyo tipo es similar a *T*.

### <a name="return-value"></a>Valor devuelto

Un valor de tipo *T\**  que apunta a X.

### <a name="remarks"></a>Comentarios

Se conoce también como una barrera de optimización del puntero.

Se utiliza como una expresión constante cuando el valor de su argumento se puede utilizar en una expresión constante. Un byte de almacenamiento es accesible a través de un valor de puntero que señala a un objeto si el almacenamiento ocupado por otro objeto, un objeto con un puntero similar.

### <a name="example"></a>Ejemplo

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a> nothrow

Proporciona un objeto que se usará como un argumento para el **nothrow** versiones de **nueva** y **eliminar**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Comentarios

El objeto se usa como un argumento de función para que coincida con el tipo de parámetro [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Ejemplo

Vea [operator new](../standard-library/new-operators.md#op_new) y [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) para obtener ejemplos de cómo se usa `std::nothrow_t` como un parámetro de función.

## <a name="set_new_handler"></a> set_new_handler

Una función de usuario que se va a llamar cuando se instala **operador new** se produce un error en su intento de asignar memoria.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parámetros

*Pnew*\
El `new_handler` para instalarse.

### <a name="return-value"></a>Valor devuelto

0 en la primera llamada y el valor `new_handler` anterior en las llamadas posteriores.

### <a name="remarks"></a>Comentarios

La función almacena *Pnew* en estático [nuevo controlador](../standard-library/new-typedefs.md#new_handler) puntero que mantiene y, a continuación, devuelve el valor almacenado previamente en el puntero. Está usando el nuevo controlador [new (operador)](../standard-library/new-operators.md#op_new)(**size_t**).

### <a name="example"></a>Ejemplo

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```
