---
title: Clase CComObjectNoLock | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComObjectNoLock
- ATL::CComObjectNoLock
- ATL.CComObjectNoLock<Base>
- CComObjectNoLock
- ATL::CComObjectNoLock<Base>
dev_langs:
- C++
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4cf4cad1a3b1a4ac0a21ef76a0eaca35732abf3a
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectnolock-class"></a>Clase CComObjectNoLock
Esta clase implementa **IUnknown** para un objeto no agregado, pero no no incremento el módulo recuento de bloqueos en el constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de cualquier otra interfaz que desea admitir en el objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Constructor.|  
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada.|  
|[CComObjectNoLock::Release](#release)|Disminuye el recuento de referencias en el objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectNoLock`es similar a [CComObject](../../atl/reference/ccomobject-class.md) en que implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto no agregado; sin embargo, `CComObjectNoLock` tiene cuenta no incremento el bloqueo de módulo en el constructor.  
  
 ATL utiliza `CComObjectNoLock` internamente para generadores de clases. En general, no utilizará esta clase directamente.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-nameaddrefa--ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectNoLock::AddRef  
 Incrementa el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o de pruebas.  
  
##  <a name="a-nameccomobjectnolocka--ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock  
 El constructor. A diferencia de [CComObject](../../atl/reference/ccomobject-class.md), no incrementa el recuento de bloqueos del módulo.  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 **void\***  
 [in] No se utiliza este parámetro sin nombre. Existe por simetría con otros **CCom***XXX*`Object`*XXX* constructores.  
  
##  <a name="a-namedtora--ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CComObjectNoLock:: ~ CComObjectNoLock  
 Destructor.  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llamadas [FinalRelease](ccomobjectrootex-class.md#finalrelease).  

  
##  <a name="a-namequeryinterfacea--ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObjectNoLock::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El identificador de la interfaz solicitada.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`. Si el objeto no admite esta interfaz, `ppvObject` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="a-namereleasea--ccomobjectnolockrelease"></a><a name="release"></a>CComObjectNoLock::Release  
 Disminuye el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En compilaciones de depuración, **versión** devuelve un valor que puede ser útil para el diagnóstico o de pruebas. En versiones no depuradas, **versión** siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

