---
title: Clase CComPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ae7bb5e85f23492bdbef4af86d9f68fa83c991e2
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomptr-class"></a>Clase CComPtr
Una clase de puntero inteligente para administrar los punteros de interfaz COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class CComPtr
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una interfaz COM que especifica el tipo de puntero que se almacenará.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|El constructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|Asigna un puntero al puntero de miembro.|  
  
## <a name="remarks"></a>Comentarios  
 ATL utiliza `CComPtr` y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) para administrar los punteros de interfaz COM. Ambos derivan [CComPtrBase](../../atl/reference/ccomptrbase-class.md), y ambos realizan el recuento de referencias automático.  
  
 El **CComPtr** y [CComQIPtr](../../atl/reference/ccomqiptr-class.md) clases pueden ayudar a eliminar pérdidas de memoria mediante la realización de recuento de referencias automático.  Las funciones siguientes realizan las mismas operaciones lógicas; Sin embargo, tenga en cuenta cómo la segunda versión puede ser menos propensas a errores mediante el uso de la **CComPtr** clase:  
  
 [!code-cpp[NVC_ATL_Utilities&#130;](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities&#131;](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 En compilaciones de depuración, vincular quitado atlsd.lib para el seguimiento del código.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="ccomptr"></a>CComPtr::CComPtr  
 El constructor.  
  
```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```  
  
### <a name="parameters"></a>Parámetros  
 `lp`  
 Se utiliza para inicializar el puntero de interfaz.  
  
 `T`  
 Una interfaz COM.  
  
##  <a name="operator_eq"></a>CComPtr::operator =  
 Operador de asignación.  
  
```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la actualización `CComPtr` objeto  
  
### <a name="remarks"></a>Comentarios  
 Esta operación AddRefs el nuevo objeto y versiones el objeto existente, si existe.  
  
## <a name="see-also"></a>Vea también  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [Información general de la clase](../../atl/atl-class-overview.md)

