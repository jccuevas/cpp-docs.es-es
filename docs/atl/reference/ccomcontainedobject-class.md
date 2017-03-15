---
title: Clase CComContainedObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComContainedObject
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
caps.latest.revision: 20
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
ms.openlocfilehash: 60958f328d78205c3432f35ed4e3e3c4b652ebfe
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcontainedobject-class"></a>Clase CComContainedObject
Esta clase implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) delegando en el objeto propietario **IUnknown**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class Base>  
class CComContainedObject : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|El constructor. Inicializa el puntero de miembro para el objeto propietario `IUnknown`.|  
|[CComContainedObject:: ~ CComContainedObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComContainedObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto propietario.|  
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Recupera el objeto propietario `IUnknown`.|  
|[CComContainedObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada en el objeto propietario.|  
|[CComContainedObject::Release](#release)|Disminuye el recuento de referencias en el objeto propietario.|  
  
## <a name="remarks"></a>Comentarios  
 ATL utiliza `CComContainedObject` en clases [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), y [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) delegando en el objeto propietario **IUnknown**. (El propietario es el objeto externo de una agregación o el objeto para el que se está creando una interfaz desplazable). `CComContainedObject` llamadas `CComObjectRootEx`de `OuterQueryInterface`, `OuterAddRef`, y `OuterRelease`, todo heredado a través de `Base`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComContainedObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-nameaddrefa--ccomcontainedobjectaddref"></a><a name="addref"></a>CComContainedObject::AddRef  
 Incrementa el recuento de referencias en el objeto propietario.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o de pruebas.  
  
##  <a name="a-nameccomcontainedobjecta--ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject  
 El constructor.  
  
```
CComContainedObject(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 [in] El objeto propietario **IUnknown**.  
  
### <a name="remarks"></a>Comentarios  
 Conjuntos de la `m_pOuterUnknown` puntero miembro (heredan a través de la `Base` clase) a `pv`.  
  
##  <a name="a-namedtora--ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CComContainedObject:: ~ CComContainedObject  
 Destructor.  
  
```
~CComContainedObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="a-namegetcontrollingunknowna--ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown  
 Devuelve el `m_pOuterUnknown` puntero miembro (heredan a través de la *Base* clase) que contiene el objeto propietario **IUnknown**.  
  
```
IUnknown* GetControllingUnknown();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto propietario **IUnknown**.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede ser virtual si `Base` ha declarado el [DECLARE_GET_CONTROLLING_UNKNOWN](http://msdn.microsoft.com/library/82b0199a-a9d5-4f95-a711-fa1ae18e1f77) (macro).  
  
##  <a name="a-namequeryinterfacea--ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CComContainedObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada en el objeto propietario.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El identificador de la interfaz solicitada.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`. Si el objeto no admite esta interfaz, `ppvObject` está establecido en **NULL**.  
  
 `pp`  
 [out] Un puntero al puntero de interfaz identificado por tipo `Q`. Si el objeto no admite esta interfaz, `pp` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="a-namereleasea--ccomcontainedobjectrelease"></a><a name="release"></a>CComContainedObject::Release  
 Disminuye el recuento de referencias en el objeto propietario.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En compilaciones de depuración, **versión** devuelve un valor que puede ser útil para el diagnóstico o de pruebas. En versiones no depuradas, **versión** siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

