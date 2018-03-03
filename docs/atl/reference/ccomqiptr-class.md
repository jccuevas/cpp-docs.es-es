---
title: Clase CComQIPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b63e584b7c4620be0e77da034a2a419b80cf741
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomqiptr-class"></a>Clase CComQIPtr
Una clase de puntero inteligente para administrar los punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una interfaz COM que especifican el tipo de puntero que se almacenará.  
  
 `piid`  
 Un puntero a lo IID de `T`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Constructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|Asigna un puntero al puntero de miembro.|  
  
## <a name="remarks"></a>Comentarios  
 ATL usa `CComQIPtr` y [CComPtr](../../atl/reference/ccomptr-class.md) para administrar los punteros de interfaz COM, que derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Ambas clases realizan a través de llamadas a de recuento de referencias automático `AddRef` y **versión**. Operadores sobrecargados controlen las operaciones de puntero.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcomcli.h  
  
##  <a name="ccomqiptr"></a>CComQIPtr::CComQIPtr  
 El constructor.  
  
```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lp`  
 Se utiliza para inicializar el puntero de interfaz.  
  
 `T`  
 Una interfaz COM.  
  
 `piid`  
 Un puntero a lo IID de `T`.  
  
##  <a name="operator_eq"></a>CComQIPtr::operator =  
 El operador de asignación.  
  
```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lp`  
 Se utiliza para inicializar el puntero de interfaz.  
  
 `T`  
 Una interfaz COM.  
  
 `piid`  
 Un puntero a lo IID de `T`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la actualización `CComQIPtr` objeto.  
  
## <a name="see-also"></a>Vea también  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [Clase CComPtrBase](../../atl/reference/ccomptrbase-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits (clase)](../../atl/reference/ccomqiptrelementtraits-class.md)
