---
title: _com_ptr_t::QueryInterface | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21dffde38e58bb7c07a1a92421d3febe10cc1032
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface
**Específicos de Microsoft**  
  
 Llamadas a la `QueryInterface` función miembro de **IUnknown** en el puntero de interfaz encapsulado.  
  
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
 `iid`  
 **IID** de un puntero de interfaz.  
  
 `p`  
 Puntero de interfaz sin formato.  
  
## <a name="remarks"></a>Comentarios  
 Llamadas **IUnknown:: QueryInterface** en el puntero de interfaz encapsulado con los valores especificados **IID** y devuelve el puntero de interfaz sin formato resultante en `p`. Esta rutina devuelve `HRESULT` para indicar si la operación se ha realizado de forma correcta o no.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)