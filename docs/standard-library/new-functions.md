---
title: Funciones &lt;new&gt;
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425416"
---
# <a name="ltnewgt-functions"></a>Funciones &lt;new&gt;

## <a name="get_new_handler"></a>get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Observaciones

Devuelve el objeto `new_handler` actual.

## <a name="launder"></a>blanqueo

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Dirección de un byte en memoria que contiene un objeto cuyo tipo es similar a *T*.

### <a name="return-value"></a>Valor devuelto

Valor de tipo *T\** que apunta a X.

### <a name="remarks"></a>Observaciones

También se conoce como barrera de optimización de puntero.

Se utiliza como una expresión constante cuando el valor de su argumento se puede usar en una expresión constante. Se puede obtener acceso a un byte de almacenamiento a través de un valor de puntero que apunta a un objeto si se encuentra dentro del almacenamiento ocupado por otro objeto, un objeto con un puntero similar.

### <a name="example"></a>Ejemplo

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a>nothrow

Proporciona un objeto que se va a usar como argumento para las versiones **nothrow** de **New** y **Delete**.

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Observaciones

El objeto se usa como un argumento de función para que coincida con el tipo de parámetro [std::nothrow_t](../standard-library/nothrow-t-structure.md).

### <a name="example"></a>Ejemplo

Vea [operator new](../standard-library/new-operators.md#op_new) y [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) para obtener ejemplos de cómo se usa `std::nothrow_t` como un parámetro de función.

## <a name="set_new_handler"></a>set_new_handler

Instala una función de usuario a la que se llamará cuando se produzca un error en el **operador New** en su intento de asignar memoria.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parámetros

\ *Pnew*
`new_handler` que se va a instalar.

### <a name="return-value"></a>Valor devuelto

0 en la primera llamada y el valor `new_handler` anterior en las llamadas posteriores.

### <a name="remarks"></a>Observaciones

La función almacena *Pnew* en un nuevo puntero de [controlador](../standard-library/new-typedefs.md#new_handler) estático que mantiene y, a continuación, devuelve el valor almacenado previamente en el puntero. El [operador New](../standard-library/new-operators.md#op_new)(**size_t**) utiliza el nuevo controlador.

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
