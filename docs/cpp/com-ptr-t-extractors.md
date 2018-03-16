---
title: _com_ptr_t Extractors | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c006c18b9e00e5c79ff686dfb31fa9ccf56fd4e
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
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
  
-   **operador Interface\***  devuelve el puntero de interfaz encapsulado, que puede ser **NULL**.  
  
-   **operador Interface &** devuelve una referencia al puntero de interfaz encapsulado y emite un error si el puntero es **NULL**.  
  
-   **operador\***  permite que un objeto de puntero inteligente actúe como si fuera la interfaz encapsulada real cuando se desreferencia.  
  
-   **operador ->** permite que un objeto de puntero inteligente actúe como si fuera la interfaz encapsulada real cuando se desreferencia.  
  
-   **operador &** libera cualquier puntero de interfaz encapsulado, lo reemplaza con **NULL**y devuelve la dirección del puntero encapsulado. Esto permite que el puntero inteligente que se pasan por dirección a una función que tiene un **out** parámetro a través del cual devuelve un puntero de interfaz.  
  
-   **operador bool** permite que un objeto de puntero inteligente para su uso en una expresión condicional. Este operador devuelve **true** si el puntero no es **NULL**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)