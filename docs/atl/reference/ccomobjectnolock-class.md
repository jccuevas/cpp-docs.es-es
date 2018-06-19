---
title: Clase CComObjectNoLock | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd7f9fa0ac67592c5fca805eaa4bb4ec4b0ca153
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361484"
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Constructor.|  
|[CComObjectNoLock:: ~ CComObjectNoLock](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada.|  
|[CComObjectNoLock::Release](#release)|Disminuye el recuento de referencias en el objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObjectNoLock` es similar a [CComObject](../../atl/reference/ccomobject-class.md) en que implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto; sin embargo, `CComObjectNoLock` tiene cuenta no incremento el bloqueo de módulo en el constructor.  
  
 ATL usa `CComObjectNoLock` internamente para los generadores de clases. En general, no utilizará esta clase directamente.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>  CComObjectNoLock::AddRef  
 Incrementa el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o pruebas.  
  
##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock  
 El constructor. A diferencia de [CComObject](../../atl/reference/ccomobject-class.md), no incrementa el recuento de bloqueos del módulo.  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 **void\***  
 [in] No se utiliza este parámetro sin nombre. Existe por simetría con otros **CCom *** XXX*`Object`*XXX* constructores.  
  
##  <a name="dtor"></a>  CComObjectNoLock:: ~ CComObjectNoLock  
 Destructor.  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llamadas [FinalRelease](ccomobjectrootex-class.md#finalrelease).  

  
##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El identificador de la interfaz que se solicita.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`. Si el objeto no admite esta interfaz, `ppvObject` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="release"></a>  CComObjectNoLock::Release  
 Disminuye el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración, **versión** devuelve un valor que puede ser útil para el diagnóstico o pruebas. En las compilaciones de depuración no, **versión** siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
