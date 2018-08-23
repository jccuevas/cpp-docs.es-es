---
title: CComObject (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4be126af9228312fa5fd4430e4f477f037d31df8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572497"
---
# <a name="ccomobject-class"></a>CComObject (clase)
Esta clase implementa `IUnknown` para un objeto no agregado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>Parámetros  
 *base*  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|El constructor.|  
|[CComObject:: ~ CComObject](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|  
|[CComObject::CreateInstance](#createinstance)|(Estático) Crea un nuevo `CComObject` objeto.|  
|[CComObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|  
|[CComObject::Release](#release)|Disminuye el recuento de referencias en el objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CComObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto no agregado. Sin embargo, las llamadas a `QueryInterface`, `AddRef`, y `Release` se delegan a `CComObjectRootEx`.  
  
 Para obtener más información sobre el uso de `CComObject`, consulte el artículo [aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="addref"></a>  CComObject::AddRef  
 Incrementa el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función devuelve el nuevo recuento de referencias incrementado en el objeto. Este valor puede ser útil para diagnósticos o pruebas.  
  
##  <a name="ccomobject"></a>  CComObject::CComObject  
 El constructor incrementa el recuento de bloqueos del módulo.  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 **void\***  
 [in] No se utiliza este parámetro sin nombre. Existe para lograr una simetría Sí **CCom *** XXX*`Object`*XXX* constructores.  
  
### <a name="remarks"></a>Comentarios  
 El destructor disminuye lo.  
  
 Si un `CComObject`-objeto derivado correctamente se construye utilizando el **nuevo** operador, el recuento de referencias inicial es 0. Para establecer el recuento de referencias en el valor apropiado (1), realice una llamada a la [AddRef](#addref) función.  
  
##  <a name="dtor"></a>  CComObject:: ~ CComObject  
 Destructor.  
  
```
CComObject();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados, llamadas [FinalRelease](ccomobjectrootex-class.md#finalrelease), y reduce el módulo recuento de bloqueos.  

  
##  <a name="createinstance"></a>  CComObject::CreateInstance  
 Esta función estática le permite crear un nuevo **CComObject <** `Base` **>** objeto, sin la sobrecarga de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 *perfil de puerto*  
 [out] Un puntero a un **CComObject <** `Base` **>** puntero. Si `CreateInstance` es incorrecta, *pp* se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El objeto devuelto tiene un recuento de referencias de cero, puede llamarlo `AddRef` inmediatamente, use `Release` para liberar la referencia en el puntero de objeto cuando haya terminado.  
  
 Si no necesita acceso directo a los objetos, pero todavía desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, utilice [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>  CComObject::QueryInterface  
 Recupera un puntero a la interfaz solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parámetros  
 *IID*  
 [in] El identificador de la interfaz que se solicita.  
  
 *ppvObject*  
 [out] Un puntero al puntero de interfaz identificado por *iid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.  
  
 *perfil de puerto*  
 [out] Un puntero al puntero de interfaz identificado por tipo `Q`. Si el objeto no admite esta interfaz, *pp* se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
##  <a name="release"></a>  CComObject::Release  
 Disminuye el recuento de referencias en el objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función devuelve el nuevo recuento de referencias disminuye en el objeto. En las compilaciones de depuración, el valor devuelto puede ser útil para el diagnóstico o pruebas. En versiones no depuradas, `Release` siempre devuelve 0.  
  
## <a name="see-also"></a>Vea también  
 [CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject (clase)](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Información general de clases](../../atl/atl-class-overview.md)
