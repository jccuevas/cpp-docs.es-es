---
title: _com_ptr_t (extractores) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3465b75d39d62c2118c53533f46627a68a1f286d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101675"
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