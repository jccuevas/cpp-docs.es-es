---
title: _com_ptr_t::QueryInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c455ce81a869d64b3a9019088028e384c6a06217
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944166"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface
**Específicos de Microsoft**  
  
 Las llamadas del `QueryInterface` función miembro de `IUnknown` en el puntero de interfaz encapsulado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType*& p   
) throw ( );  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType** p  
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 *IID*  
 `IID` de un puntero de interfaz.  
  
 *p*  
 Puntero de interfaz sin formato.  
  
## <a name="remarks"></a>Comentarios  
 Las llamadas `IUnknown::QueryInterface` en el puntero de interfaz encapsulado con los valores especificados `IID` y devuelve el puntero de interfaz sin formato resultante en *p*. Esta rutina devuelve el valor HRESULT para indicar éxito o error.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)