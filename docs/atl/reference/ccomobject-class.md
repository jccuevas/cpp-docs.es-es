---
title: Clase CComObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComObject<Base>
- ATL::CComObject
- ATL::CComObject<Base>
- ATL.CComObject
- CComObject
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
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
ms.openlocfilehash: 5f752b96d4a722fbddfcc9e5be3a82b8b12a86a1
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobject-class"></a>CComObject (clase)
Esta clase implementa **IUnknown** para un objeto no agregado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|El constructor.|  
|[CComObject:: ~ CComObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|  
|[CComObject::CreateInstance](#createinstance)|(Estático) Crea un nuevo `CComObject` objeto.|  
|[CComObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|  
|[CComObject::Release](#release)|Disminuye el recuento de referencias en el objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObject`implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto no agregado. Sin embargo, las llamadas a `QueryInterface`, `AddRef`, y **versión** se delegan a `CComObjectRootEx`.  
  
 Para obtener más información acerca del uso de `CComObject`, vea el artículo [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-nameaddrefa--ccomobjectaddref"></a><a name="addref"></a>CComObject::AddRef  
 Incrementa el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función devuelve el nuevo recuento de referencias incrementado en el objeto. Este valor puede ser útil para el diagnóstico o pruebas.  
  
##  <a name="a-nameccomobjecta--ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject::CComObject  
 El constructor incrementa el recuento de bloqueos del módulo.  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 **void\***  
 [in] No se utiliza este parámetro sin nombre. Existe por simetría con otros **CCom***XXX*`Object`*XXX* constructores.  
  
### <a name="remarks"></a>Comentarios  
 El disminuye destructor.  
  
 Si un `CComObject`-objeto derivado correctamente se construye utilizando el **nuevo** operador, el recuento de referencia inicial es 0. Para establecer el recuento de referencias en el valor apropiado (1), realice una llamada a la [AddRef](#addref) (función).  
  
##  <a name="a-namedtora--ccomobjectccomobject"></a><a name="dtor"></a>CComObject:: ~ CComObject  
 Destructor.  
  
```
CComObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados, llamadas [FinalRelease](ccomobjectrootex-class.md#finalrelease), y disminuye el módulo recuento de bloqueos.  

  
##  <a name="a-namecreateinstancea--ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject::CreateInstance  
 Esta función estática le permite crear un nuevo **CComObject** `Base` ** > ** objeto, sin la sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 `pp`  
 [out] Un puntero a un **CComObject** `Base` ** > ** puntero. Si `CreateInstance` es incorrecta, `pp` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 El objeto devuelto tiene un recuento de referencias de cero, llame `AddRef` inmediatamente, a continuación, utilice **versión** para liberar la referencia en el puntero de objeto cuando haya terminado.  
  
 Si no necesita el acceso directo al objeto, pero todavía desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, utilice [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#38;](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM&#39;](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="a-namequeryinterfacea--ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
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
  
##  <a name="a-namereleasea--ccomobjectrelease"></a><a name="release"></a>CComObject::Release  
 Disminuye el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función devuelve el nuevo recuento de referencias disminuye en el objeto. En compilaciones de depuración, el valor devuelto puede ser útil para el diagnóstico o pruebas. En versiones no depuradas, **versión** siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [Clase CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](http://msdn.microsoft.com/library/e7e568d7-04e0-4226-b5dc-224deed229ab)   
 [DECLARE_NOT_AGGREGATABLE](http://msdn.microsoft.com/library/2a116c7c-bab8-4f2a-a9ad-03d7aba0f762)   
 [Información general de la clase](../../atl/atl-class-overview.md)

