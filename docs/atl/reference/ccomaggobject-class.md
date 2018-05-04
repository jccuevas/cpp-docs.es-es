---
title: CComAggObject (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426a01c1957b276174b8b36884605b69dd501de8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ccomaggobject-class"></a>CComAggObject (clase)
Esta clase implementa la [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfaz para un objeto agregado. Por definición, un objeto agregado está dentro de un objeto externo. El `CComAggObject` clase es similar a la [CComObject (clase)](../../atl/reference/ccomobject-class.md), excepto en que expone una interfaz que son directamente accesible para los clientes externos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parámetros  
 `contained`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de otras interfaces que desea admitir en el objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|El constructor.|  
|[CComAggObject:: ~ CComAggObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto agregado.|  
|[CComAggObject::CreateInstance](#createinstance)|Esta función estática le permite crear un nuevo **CComAggObject <** `contained` **>** objeto sin la sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComAggObject::FinalConstruct](#finalconstruct)|Realiza la inicialización final de `m_contained`.|  
|[CComAggObject::FinalRelease](#finalrelease)|Realiza la destrucción de final de `m_contained`.|  
|[CComAggObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|  
|[CComAggObject::Release](#release)|Disminuye el recuento de referencias en el objeto agregado.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|Delegados `IUnknown` llamadas al desconocido externo.|  
  
## <a name="remarks"></a>Comentarios  
 `CComAggObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto agregado. `CComAggObject` tiene su propio **IUnknown** interfaz, de forma independiente desde el objeto externo **IUnknown** de interfaz y mantiene su propia recuento de referencias.  
  
 Para obtener más información acerca de la agregación, vea el artículo [aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>  CComAggObject::AddRef  
 Incrementa el recuento de referencias en el objeto agregado.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o pruebas.  
  
##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject  
 El constructor.  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 [in] El desconocido externo.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained)e incrementa el recuento de bloqueos del módulo.  
  
 El disminuye destructor el módulo recuento de bloqueos.  
  
##  <a name="dtor"></a>  CComAggObject:: ~ CComAggObject  
 Destructor.  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados, llamadas [FinalRelease](#finalrelease), y reduce el módulo recuento de bloqueos.  
  
##  <a name="createinstance"></a>  CComAggObject::CreateInstance  
 Esta función estática le permite crear un nuevo **CComAggObject <** `contained` **>** objeto sin la sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `pp`  
 [out] Un puntero a un **CComAggObject\<*** contenidos* **>** puntero. Si `CreateInstance` es incorrecta, `pp` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El objeto devuelto tiene un recuento de referencias de cero, por lo que se llame a `AddRef` inmediatamente, a continuación, utilice **versión** para liberar la referencia en el puntero de objeto cuando haya terminado.  
  
 Si no necesita acceso directo a los objetos, pero todavía desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, use [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.  
  
##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct  
 Se llama durante las fases finales de la construcción de objetos, este método realiza las inicializaciones final en el [m_contained](#m_contained) miembro.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="finalrelease"></a>  CComAggObject::FinalRelease  
 Se llama durante la destrucción de objetos, este método libera el [m_contained](#m_contained) miembro.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComAggObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Parámetros  
 `contained`  
 [in] La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de otras interfaces que desea admitir en el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Todos los **IUnknown** llama a través de `m_contained` se delegan en el desconocido externo.  
  
##  <a name="queryinterface"></a>  CComAggObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El identificador de la interfaz que se solicita.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`. Si el objeto no admite esta interfaz, `ppvObject` está establecido en **NULL**.  
  
 `pp`  
 [out] Un puntero al puntero de interfaz identificado por tipo `Q`. Si el objeto no admite esta interfaz, `pp` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Si la interfaz solicitada es **IUnknown**, `QueryInterface` devuelve un puntero para el objeto agregado propio **IUnknown** e incrementa el recuento de referencias. En caso contrario, este método consulta para la interfaz a través de la `CComContainedObject` miembro, [m_contained](#m_contained).  
  
##  <a name="release"></a>  CComAggObject::Release  
 Disminuye el recuento de referencias en el objeto agregado.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En las compilaciones de depuración, **versión** devuelve un valor que puede ser útil para el diagnóstico o pruebas. En las compilaciones de depuración no, **versión** siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [CComObject (clase)](../../atl/reference/ccomobject-class.md)   
 [Clase CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Información general de clases](../../atl/atl-class-overview.md)
