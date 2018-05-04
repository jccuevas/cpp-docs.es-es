---
title: _com_ptr_t::QueryInterface | Documentos de Microsoft
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
ms.openlocfilehash: 7c046f1b1d14b7e7dbd44ca9f5f012e632efef6e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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