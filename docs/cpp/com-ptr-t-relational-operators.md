---
title: Operadores relacionales _com_ptr_t | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
- '>= operator, comparing specific objects'
- '!= operator'
- operator >, pointers
- operator>=, pointers
- operator <, pointers
- operator!=, relational operators
- < operator, comparing specific objects
- operator==, pointers
- operator ==, pointers
- <= operator, with specific objects
- relational operators, _com_ptr_t class
- operator >=, pointers
- operator !=, relational operators
- operator <=, pointers
- '> operator, comparing specific objects'
- operator<=, pointers
- operator<, pointers
- == operator, with specific Visual C++ objects
ms.assetid: 5ae4028c-33ee-485d-bbda-88d2604d6d4b
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 25ec5c27afcc6374f4f450a3fc290aad2cf6bfac
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="comptrt-relational-operators"></a>_com_ptr_t (Operadores relacionales)
**Específicos de Microsoft**  
  
 Compara el objeto de puntero inteligente con otro puntero inteligente, puntero de interfaz sin formato, o **NULL**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      template<typename _OtherIID>   
bool operator==(   
   const _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _OtherIID>    
bool operator==(   
   _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _InterfaceType>   
bool operator==(   
   _InterfaceType* p   
);  
  
template<>   
bool operator==(   
   Interface* p   
);  
  
template<>   
bool operator==(   
   const _com_ptr_t& p   
) throw();  
  
template<>   
bool operator==(   
   _com_ptr_t& p   
) throw();  
  
bool operator==(   
   int null   
);  
```  
  
```  
  
      template<typename _OtherIID>   
bool operator!=(   
   const _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _OtherIID>   
bool operator!=(   
   _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _InterfaceType>   
bool operator!=(   
   _InterfaceType* p   
);  
  
bool operator!=(   
   int null   
);  
```  
  
```  
  
      template<typename _OtherIID>   
bool operator<(   
   const _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _OtherIID>   
bool operator<(   
   _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _InterfaceType>   
bool operator<(   
   _InterfaceType* p   
);  
```  
  
```  
  
      template<typename _OtherIID>   
bool operator>(   
   const _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _OtherIID>   
bool operator>(_com_ptr_t<   
   _OtherIID>& p   
);  
  
template<typename _InterfaceType>   
bool operator>(   
   _InterfaceType* p   
);  
```  
  
```  
  
      template<typename _OtherIID>   
bool operator<=(   
   const _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _OtherIID>   
bool operator<=(   
   _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _InterfaceType>   
bool operator<=(   
   _InterfaceType* p   
);  
```  
  
```  
  
      template<typename _OtherIID>   
bool operator>=(   
   const _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _OtherIID>   
bool operator>=(   
   _com_ptr_t<_OtherIID>& p   
);  
  
template<typename _InterfaceType>   
bool operator>=(   
   _InterfaceType* p   
);  
```  
  
## <a name="remarks"></a>Comentarios  
 Compara un objeto de puntero inteligente con otro puntero inteligente, puntero de interfaz sin formato, o **NULL**. Excepto para la **NULL** comprobaciones de puntero, estos operadores consultan primero ambos punteros para **IUnknown**y comparar los resultados.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
