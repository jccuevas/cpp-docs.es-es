---
title: Clase CComCachedTearOffObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 96f040c732c5545a9b8febb32fcb1636f0fe4a40
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcachedtearoffobject-class"></a>Clase CComCachedTearOffObject
Esta clase implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para una interfaz desplazable.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template
 <class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
 ::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parámetros  
 `contained`  
 Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que el objeto desplazable para admitir.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|El constructor.|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|Incrementa el recuento de referencias para un `CComCachedTearOffObject` objeto.|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Llamadas del `m_contained::FinalConstruct` (método de clase que desplazable).|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Llamadas del `m_contained::FinalRelease` (método de clase que desplazable).|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero a la `IUnknown` de la `CComCachedTearOffObject` objeto, o a la interfaz solicitada en la clase desplazable (la clase `contained`).|  
|[CComCachedTearOffObject::Release](#release)|Disminuye el recuento de referencias para un `CComCachedTearOffObject` de objetos y se destruye si el recuento de referencias es 0.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|Un `CComContainedObject` objeto derivado de la clase desplazable (la clase `contained`).|  
  
## <a name="remarks"></a>Comentarios  
 `CComCachedTearOffObject`implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para una interfaz desplazable. Esta clase difiere de `CComTearOffObject` en que `CComCachedTearOffObject` tiene su propio **IUnknown**, independiente del objeto propietario de **IUnknown** (el propietario es el objeto para el que está creando el desplazable). `CComCachedTearOffObject`mantiene su propio número de referencias en su **IUnknown** y se elimina cuando su recuento de referencias es cero. Sin embargo, si cualquiera de su desplazable Consulta interfaces, el recuento de referencias del objeto propietario **IUnknown** se incrementará.  
  
 Si el `CComCachedTearOffObject` objeto ya se crean instancias de implementar el desplazable y la interfaz desplazable es consultar de nuevo, en el mismo `CComCachedTearOffObject` se vuelve a utilizar el objeto. En cambio, si implementa una interfaz divisible por un `CComTearOffObject` nuevo se consulta a través del objeto propietario, otro `CComTearOffObject` creará una instancia.  
  
 Debe implementar la clase propietaria `FinalRelease` y llame a **versión** en la caché **IUnknown** para el `CComCachedTearOffObject`, lo que disminuye su recuento de referencia. Esto hará que `CComCachedTearOffObject`de `FinalRelease` para llamar y eliminar el desplazable.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>CComCachedTearOffObject::AddRef  
 Incrementa el recuento de referencias de la `CComCachedTearOffObject` objeto en 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para los diagnósticos y pruebas.  
  
##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject  
 El constructor.  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 [in] Puntero a la **IUnknown** de la `CComCachedTearOffObject`.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained).  
  
##  <a name="dtor"></a>CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 Destructor.  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llamadas [FinalRelease](#finalrelease).  
  
##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct  
 Llamadas **m_contained::FinalConstruct** crear `m_contained`, `CComContainedObject` <  `contained`> objeto usado para tener acceso a la interfaz implementada por la clase desplazable.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease  
 Llamadas **m_contained::FinalRelease** para liberar `m_contained`, `CComContainedObject` <  `contained`> objeto.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained  
 Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase desplazable.  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>Parámetros  
 `contained`  
 [in] Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que el objeto desplazable para admitir.  
  
### <a name="remarks"></a>Comentarios  
 Los métodos `m_contained` hereda se utilizan para tener acceso a la interfaz desplazable en su clase desplazable a través del objeto en caché desplazable `QueryInterface`, `FinalConstruct`, y `FinalRelease`.  
  
##  <a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz solicitada.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`, o **NULL** si no se encuentra la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si la interfaz solicitada es **IUnknown**, devuelve un puntero a la `CComCachedTearOffObject`del propio **IUnknown** e incrementa el recuento de referencias. De lo contrario, las consultas de la interfaz en la clase desplazable con el [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) método hereda de `CComObjectRootEx`.  

  
##  <a name="release"></a>CComCachedTearOffObject::Release  
 Disminuye el recuento de referencias en 1 y, si el recuento de referencias es 0, se elimina la `CComCachedTearOffObject` objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En versiones no depuradas, siempre devuelve 0. En compilaciones de depuración, devuelve un valor que puede ser útil para el diagnóstico o de pruebas.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

