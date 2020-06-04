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
ms.openlocfilehash: 31ac39104c041d1d119f6cd06de5f9c4a620dac0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190032"
---
# <a name="_com_ptr_t-extractors"></a>_com_ptr_t (Extractores)

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

## <a name="remarks"></a>Observaciones

- **Operator interface** <strong>\*</strong> devuelve el puntero de interfaz encapsulado, que puede ser null.

- **interfaz de operador &** Devuelve una referencia al puntero de interfaz encapsulado y genera un error si el puntero es NULL.

- **operator** <strong>\*</strong> permite que un objeto de puntero inteligente actúe como si fuera la interfaz encapsulada real al desreferenciarse.

- **operador->** Permite que un objeto de puntero inteligente actúe como si fuera la interfaz encapsulada real al desreferenciarse.

- **operador &** Libera cualquier puntero de interfaz encapsulado, reemplazándolo por NULL y devuelve la dirección del puntero encapsulado. Esto permite pasar el puntero inteligente por dirección a una función que tiene un parámetro *out* a través del cual devuelve un puntero de interfaz.

- **operador bool** Permite usar un objeto de puntero inteligente en una expresión condicional. Este operador devuelve TRUE si el puntero no es NULL.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
