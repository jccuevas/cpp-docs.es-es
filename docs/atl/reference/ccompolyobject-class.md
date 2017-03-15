---
title: Clase CComPolyObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATL.CComPolyObject<contained>
- ATL::CComPolyObject
- ATL::CComPolyObject<contained>
- ATL.CComPolyObject
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
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
ms.openlocfilehash: 37be4c985983cb760246a4a2450c27d175d1f440
ms.lasthandoff: 02/24/2017

---
# <a name="ccompolyobject-class"></a>Clase CComPolyObject
Esta clase implementa **IUnknown** para un objeto agregado o no agregado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parámetros  
 `contained`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|El constructor.|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|Incrementa el recuento de referencias del objeto.|  
|[CComPolyObject::CreateInstance](#createinstance)|(Estático) Le permite crear un nuevo **CComPolyObject** `contained` ** > ** objeto sin la sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|Realiza la inicialización final de `m_contained`.|  
|[CComPolyObject::FinalRelease](#finalrelease)|Realiza la destrucción final de `m_contained`.|  
|[CComPolyObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|  
|[CComPolyObject::Release](#release)|Reduce el recuento de referencia del objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|Delegados **IUnknown** llama al desconocido externo si se agrega el objeto o en la **IUnknown** del objeto si el objeto no es agregado.|  
  
## <a name="remarks"></a>Comentarios  
 `CComPolyObject`implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto agregado o no agregado.  
  
 Cuando una instancia de `CComPolyObject` se crea, el valor de externo desconocido está activado. Si es **NULL**, **IUnknown** se implementa para un objeto no agregado. Si el desconocido externo no es **NULL**, **IUnknown** se implementa para un objeto agregado.  
  
 La ventaja de usar `CComPolyObject` es evitar tener ambos [CComAggObject](../../atl/reference/ccomaggobject-class.md) y [CComObject](../../atl/reference/ccomobject-class.md) en su módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto controla ambos casos. Esto significa que existen una única copia de la tabla vtable y una copia de las funciones en el módulo. Si su tabla vtable es grande, puede reducir sustancialmente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.  
  
 Si el `DECLARE_POLY_AGGREGATABLE` macro se especifica en la definición de clase del objeto, `CComPolyObject` se usará para crear el objeto. `DECLARE_POLY_AGGREGATABLE`automáticamente se declarará si usa el Asistente para proyectos ATL para crear un control total o un control de Internet Explorer.  
  
 Si se agregan, el `CComPolyObject` objeto tiene su propio **IUnknown**independiente desde el objeto externo **IUnknown**y mantiene su propio número de referencias. `CComPolyObject`usa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) delegar en el desconocido externo.  
  
 Para obtener más información acerca de la agregación, vea el artículo [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-nameaddrefa--ccompolyobjectaddref"></a><a name="addref"></a>CComPolyObject::AddRef  
 Incrementa el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que puede ser útil para el diagnóstico o de pruebas.  
  
##  <a name="a-nameccompolyobjecta--ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 El constructor.  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pv`  
 [in] Un puntero para el desconocido externo si el objeto que se va a agregarse, o **NULL** si el objeto si el objeto no es agregado.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el `CComContainedObject` miembro de datos, [m_contained](#m_contained)e incrementa el recuento de bloqueos del módulo.  
  
 El disminuye destructor el módulo recuento de bloqueos.  
  
##  <a name="a-namedtora--ccompolyobjectccompolyobject"></a><a name="dtor"></a>CComPolyObject:: ~ CComPolyObject  
 Destructor.  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados, llamadas [FinalRelease](#finalrelease), y disminuye el módulo recuento de bloqueos.  
  
##  <a name="a-namecreateinstancea--ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPolyObject::CreateInstance  
 Le permite crear un nuevo **CComPolyObject** `contained` ** > ** objeto sin la sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `pp`  
 [out] Un puntero a un **CComPolyObject** `contained` ** > ** puntero. Si `CreateInstance` es incorrecta, `pp` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El objeto devuelto tiene un recuento de referencias de cero, llame `AddRef` inmediatamente, a continuación, utilice **versión** para liberar la referencia en el puntero de objeto cuando haya terminado.  
  
 Si no necesita acceso directo al objeto, pero todavía desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, utilice [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.  
  
##  <a name="a-namefinalconstructa--ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 Se llama durante las fases finales de la construcción de objetos, este método realiza cualquier inicialización final en el [m_contained](#m_contained) miembro de datos.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="a-namefinalreleasea--ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPolyObject::FinalRelease  
 Se llama durante la destrucción de objetos, este método libera la [m_contained](#m_contained) miembro de datos.  
  
```
void FinalRelease();
```  
  
##  <a name="a-namemcontaineda--ccompolyobjectmcontained"></a><a name="m_contained"></a>CComPolyObject::m_contained  
 Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Parámetros  
 `contained`  
 [in] La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.  
  
### <a name="remarks"></a>Comentarios  
 **IUnknown** llama a través de `m_contained` se delegan el desconocido externo si se agrega el objeto, o en la **IUnknown** de este objeto si el objeto no es agregado.  
  
##  <a name="a-namequeryinterfacea--ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPolyObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `Q`  
 La interfaz COM.  
  
 `iid`  
 [in] El identificador de la interfaz solicitada.  
  
 `ppvObject`  
 [out] Un puntero al puntero de interfaz identificado por `iid`. Si el objeto no admite esta interfaz, `ppvObject` está establecido en **NULL**.  
  
 `pp`  
 [out] Un puntero a la interfaz identificada por **__uuidof(Q)**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Para un objeto agregado, si la interfaz solicitada es **IUnknown**, `QueryInterface` devuelve un puntero para el objeto agregado propio **IUnknown** e incrementa el recuento de referencias. De lo contrario, este método consulta para la interfaz a través de la `CComContainedObject` miembro de datos, [m_contained](#m_contained).  
  
##  <a name="a-namereleasea--ccompolyobjectrelease"></a><a name="release"></a>CComPolyObject::Release  
 Disminuye el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 En compilaciones de depuración, **versión** devuelve un valor que puede ser útil para el diagnóstico o de pruebas. En las compilaciones nondebug, **versión** siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](http://msdn.microsoft.com/library/7569e738-cfbc-4404-ba1d-78dcefa3bdb3)   
 [Información general de la clase](../../atl/atl-class-overview.md)

