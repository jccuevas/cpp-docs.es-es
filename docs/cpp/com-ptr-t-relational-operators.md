---
title: Operadores relacionales _com_ptr_t | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operator>
- _com_ptr_t::operator>=
- _com_ptr_t::operator<=
- _com_ptr_t::operator==
- _com_ptr_t::operator!=
- _com_ptr_t::operator<
dev_langs:
- C++
helpviewer_keywords:
- '>= operator [C++], comparing specific objects'
- '!= operator'
- operator > [C++], pointers
- operator>= [C++], pointers
- operator < [C++], pointers
- operator!= [C++], relational operators
- < operator [C++], comparing specific objects
- operator== [C++], pointers
- operator == [C++], pointers
- <= operator [C++], with specific objects
- relational operators [C++], _com_ptr_t class
- operator >= [C++], pointers
- operator != [C++], relational operators
- operator <= [C++], pointers
- '> operator [C++], comparing specific objects'
- operator<= [C++], pointers
- operator< [C++], pointers
- == operator [C++], with specific Visual C++ objects
ms.assetid: 5ae4028c-33ee-485d-bbda-88d2604d6d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4502f4752d094805ac9e31bbd4fdcbd1b0fdbdab
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403266"
---
# <a name="comptrt-relational-operators"></a>_com_ptr_t (Operadores relacionales)
**Específicos de Microsoft**  
  
 Comparar el objeto de puntero inteligente a otro puntero inteligente, puntero de interfaz sin formato, o NULL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename _OtherIID>   
bool operator==( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>    
bool operator==( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator==( _InterfaceType* p );  
  
template<>   
bool operator==( Interface* p );  
  
template<>   
bool operator==( const _com_ptr_t& p ) throw();  
  
template<>   
bool operator==( _com_ptr_t& p ) throw();  
  
bool operator==( Int null );  
  
template<typename _OtherIID>   
bool operator!=( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator!=( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator!=( _InterfaceType* p );  
  
bool operator!=( Int null );  

template<typename _OtherIID>   
bool operator<( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator<( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator<( _InterfaceType* p );  

template<typename _OtherIID>   
bool operator>( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator>(_com_ptr_t< _OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator>( _InterfaceType* p );  
  
template<typename _OtherIID>   
bool operator<=( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator<=( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator<=( _InterfaceType* p );  
  
template<typename _OtherIID>  
bool operator>=( const _com_ptr_t<_OtherIID>& p );  
  
template<typename _OtherIID>   
bool operator>=( _com_ptr_t<_OtherIID>& p );  
  
template<typename _InterfaceType>   
bool operator>=( _InterfaceType* p );  
```  
  
## <a name="remarks"></a>Comentarios  
 Compara un puntero inteligente de objeto a otro inteligente de puntero, un puntero de interfaz sin formato, o NULL. Excepto para las pruebas de puntero NULL, estos operadores consultan primero ambos punteros para `IUnknown`y comparar los resultados.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)