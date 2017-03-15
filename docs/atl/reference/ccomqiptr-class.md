---
title: Clase CComQIPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComQIPtr
- ATL::CComQIPtr
- CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e2060a0be3f9780191c316c2df41115e66033d4d
ms.lasthandoff: 02/24/2017

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
 Una interfaz COM que especifica el tipo de puntero que se almacenará.  
  
 `piid`  
 Un puntero para el IID de `T`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Constructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|Asigna un puntero al puntero de miembro.|  
  
## <a name="remarks"></a>Comentarios  
 ATL utiliza `CComQIPtr` y [CComPtr](../../atl/reference/ccomptr-class.md) para administrar los punteros de interfaz COM, que derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Ambas clases realizan a través de llamadas a de recuento de referencias automático `AddRef` y **versión**. Operadores sobrecargados controlen las operaciones de puntero.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcomcli.h  
  
##  <a name="a-nameccomqiptra--ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr::CComQIPtr  
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
 Un puntero para el IID de `T`.  
  
##  <a name="a-nameoperatoreqa--ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr::operator =  
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
 Un puntero para el IID de `T`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la actualización `CComQIPtr` objeto.  
  
## <a name="see-also"></a>Vea también  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [Clase CComPtrBase](../../atl/reference/ccomptrbase-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clase CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)

