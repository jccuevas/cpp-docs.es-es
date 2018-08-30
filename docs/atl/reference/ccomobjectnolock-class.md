---
title: CComObjectNoLock (clase) | Microsoft Docs
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
ms.openlocfilehash: 85332341e1a229ce5110153c0ad6195ef0ad42c4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208180"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock (clase)
Esta clase implementa `IUnknown` para un objeto no agregado, pero no no incremento el módulo recuento de bloqueos en el constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 *base*  
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
 `CComObjectNoLock` es similar a [CComObject](../../atl/reference/ccomobject-class.md) en que implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) para un objeto agregado; sin embargo, `CComObjectNoLock` tiene en cuenta no incremento el bloqueo de módulo en el constructor.  
  
 ATL utiliza `CComObjectNoLock` internamente para generadores de clases. En general, no utilizará esta clase directamente.  
  
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
 Un valor que puede ser útil para el diagnóstico o de pruebas.  
  
##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock  
 El constructor. A diferencia de [CComObject](../../atl/reference/ccomobject-class.md), no incrementa el recuento de bloqueos del módulo.  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 <em>void\*</em>  
 [in] No se utiliza este parámetro sin nombre. Existe para lograr una simetría con otros `CComXXXObjectXXX` constructores.  
  
##  <a name="dtor"></a>  CComObjectNoLock:: ~ CComObjectNoLock  
 Destructor.  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease).  

  
##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 *IID*  
 [in] El identificador de la interfaz que se solicita.  
  
 *ppvObject*  
 [out] Un puntero al puntero de interfaz identificado por *iid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="release"></a>  CComObjectNoLock::Release  
 Disminuye el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración, `Release` devuelve un valor que puede ser útil para el diagnóstico o de pruebas. En versiones no depuradas, `Release` siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
