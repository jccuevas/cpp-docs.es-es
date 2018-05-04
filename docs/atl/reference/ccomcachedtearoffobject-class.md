---
title: Clase CComCachedTearOffObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1072faed01033bec9fec127318334f8a61ac29e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
 Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que su objeto desplazable para admitir.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|El constructor.|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|Incrementa el recuento de referencias para un `CComCachedTearOffObject` objeto.|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Llamadas a la `m_contained::FinalConstruct` (método de clase que desplazable).|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Llamadas a la `m_contained::FinalRelease` (método de clase que desplazable).|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero a la `IUnknown` de la `CComCachedTearOffObject` objeto, o a la interfaz solicitada en la clase desplazable (la clase `contained`).|  
|[CComCachedTearOffObject::Release](#release)|Disminuye el recuento de referencias para un `CComCachedTearOffObject` de objeto y se destruye si el recuento de referencias es 0.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|A `CComContainedObject` objeto derivado de la clase desplazable (la clase `contained`).|  
  
## <a name="remarks"></a>Comentarios  
 `CComCachedTearOffObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para una interfaz desplazable. Esta clase difiere de `CComTearOffObject` en que `CComCachedTearOffObject` tiene su propio **IUnknown**, independiente del objeto propietario de **IUnknown** (el propietario es el objeto para el que está creando el desplazable). `CComCachedTearOffObject` mantiene su propio recuento de referencias en su **IUnknown** y elimina a sí mismo una vez que su recuento de referencias es cero. Sin embargo, si realiza una consulta para cualquiera de su desplazable interfaces, el recuento de referencias del objeto propietario **IUnknown** se incrementará.  
  
 Si el `CComCachedTearOffObject` objeto ya se crean instancias de implementar el desplazable y la interfaz desplazable es consultar de nuevo, en el mismo `CComCachedTearOffObject` se vuelve a usar el objeto. En cambio, si implementa una interfaz desplazable un `CComTearOffObject` nuevo se consulta a través del objeto propietario, otro `CComTearOffObject` se crearán instancias de.  
  
 Debe implementar la clase propietaria `FinalRelease` y llame al método **versión** en las almacenadas en caché **IUnknown** para el `CComCachedTearOffObject`, lo que disminuye su recuento de referencias. Esto hará que `CComCachedTearOffObject`del `FinalRelease` para llamar y eliminar el desplazable.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>  CComCachedTearOffObject::AddRef  
 Incrementa el recuento de referencias de la `CComCachedTearOffObject` objeto en 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico y prueba.  
  
##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject  
 El constructor.  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 [in] Puntero a la **IUnknown** de la `CComCachedTearOffObject`.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained).  
  
##  <a name="dtor"></a>  CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 Destructor.  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados y llamadas [FinalRelease](#finalrelease).  
  
##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct  
 Llamadas **m_contained::FinalConstruct** crear `m_contained`, `CComContainedObject` <  `contained`> objeto que se usa para tener acceso a la interfaz implementada por la clase desplazable.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease  
 Llamadas **m_contained::FinalRelease** para liberar `m_contained`, `CComContainedObject` <  `contained`> objeto.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase desplazable.  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>Parámetros  
 `contained`  
 [in] Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que su objeto desplazable para admitir.  
  
### <a name="remarks"></a>Comentarios  
 Los métodos `m_contained` hereda se utilizan para acceder a la interfaz desplazable de la clase desplazable mediante el objeto almacenado en caché desplazable `QueryInterface`, `FinalConstruct`, y `FinalRelease`.  
  
##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz que se solicita.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`, o **NULL** si no se encuentra la interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si la interfaz solicitada es **IUnknown**, devuelve un puntero a la `CComCachedTearOffObject`del propio **IUnknown** e incrementa el recuento de referencias. De lo contrario, las consultas para la interfaz en su clase desplazable utilizando la [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) método se hereda de `CComObjectRootEx`.  

  
##  <a name="release"></a>  CComCachedTearOffObject::Release  
 Disminuye el recuento de referencias en 1 y, si el recuento de referencias es 0, elimina el `CComCachedTearOffObject` objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración no, siempre devuelve 0. En las compilaciones de depuración, devuelve un valor que puede ser útil para el diagnóstico o pruebas.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
