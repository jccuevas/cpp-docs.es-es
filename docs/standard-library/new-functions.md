---
title: Funciones &lt;new&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: 6192805f0f427f86267a646b11d9f1d3365a1d57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716045"
---
# <a name="ltnewgt-functions"></a>Funciones &lt;new&gt;

|||
|-|-|
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|

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

*Pnew*<br/>
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

## <a name="see-also"></a>Vea también

[\<new>](../standard-library/new.md)<br/>
