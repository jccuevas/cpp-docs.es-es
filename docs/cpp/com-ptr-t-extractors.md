---
title: _com_ptr_t (Extractores)
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: 494507592222a7cd6334f2272c3a306e61e5d47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545982"
---
# <a name="comptrt-extractors"></a>_com_ptr_t (Extractores)

**Específicos de Microsoft**

Extrae el puntero de interfaz COM encapsulado.

## <a name="syntax"></a>Sintaxis

```
operator Interface*( ) const throw( ); 
operator Interface&( ) const; 
Interface& operator*( ) const; 
Interface* operator->( ) const; 
Interface** operator&( ) throw( ); 
operator bool( ) const throw( );
```

## <a name="remarks"></a>Comentarios

- **operador Interface** <strong>\*</strong> devuelve el puntero de interfaz encapsulado, que puede ser NULL.

- **operador Interface &** devuelve una referencia al puntero de interfaz encapsulado y emite un error si el puntero es NULL.

- **operador** <strong>\*</strong> permite a un objeto de puntero inteligente para que actúe como si fuese la interfaz encapsulada real cuando se desreferencia.

- **operador ->** permite a un objeto de puntero inteligente para que actúe como si fuese la interfaz encapsulada real cuando se desreferencia.

- **operador &** libera cualquier puntero de interfaz encapsulado, lo reemplaza con el valor NULL y devuelve la dirección del puntero encapsulado. Esto permite que el puntero inteligente que se pasará por dirección a una función que tiene un *out* parámetro a través del cual devuelve un puntero de interfaz.

- **operador booleano** permite a un objeto de puntero inteligente que se usará en una expresión condicional. Este operador devuelve TRUE si el puntero no es NULL.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)