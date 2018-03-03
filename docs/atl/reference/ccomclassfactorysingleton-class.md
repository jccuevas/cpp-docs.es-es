---
title: Clase CComClassFactorySingleton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 165bc85a0b00ac8186e5a145a75c4478335b5e0e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ccomclassfactorysingleton-class"></a>Clase CComClassFactorySingleton
Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class CComClassFactorySingleton : public CComClassFactory
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase.  
  
 `CComClassFactorySingleton`se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único. Cada llamada a la `CreateInstance` método simplemente consulta este objeto para un puntero de interfaz.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Las consultas `m_spObj` para un puntero de interfaz.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComClassFactorySingleton::m_spObj](#m_spobj)|El [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto construido por `CComClassFactorySingleton`.|  
  
## <a name="remarks"></a>Comentarios  
 Objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Usar `CComClassFactorySingleton`, especifique el [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) macro en la definición de clase del objeto. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactorySingleton::CreateInstance  
 Llamadas `QueryInterface` a través de [m_spObj](#m_spobj) para recuperar un puntero de interfaz.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkOuter`  
 [in] Si el objeto se crea como parte de un agregado, a continuación, `pUnkOuter` debe ser el desconocido externo. En caso contrario, `pUnkOuter` debe ser **NULL**.  
  
 `riid`  
 [in] El IID de la interfaz solicitada. Si `pUnkOuter` no es **NULL**, `riid` debe ser **IID_IUnknown**.  
  
 `ppvObj`  
 [out] Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppvObj` está establecido en **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
##  <a name="m_spobj"></a>CComClassFactorySingleton::m_spObj  
 El [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto construido por `CComClassFactorySingleton`.  
  
```
CComPtr<IUnknown> m_spObj;
```  
  
### <a name="remarks"></a>Comentarios  
 Cada llamada a la [CreateInstance](#createinstance) método simplemente consulta este objeto para un puntero de interfaz.  
  
 Tenga en cuenta que el formulario actual de `m_spObj` presenta un cambio importante con respecto a la forma en que `CComClassFactorySingleton` ha trabajado en versiones anteriores de ATL. En versiones anteriores del `CComClassFactorySingleton` se creó el objeto al mismo tiempo que el generador de clases, durante la inicialización del servidor. En Visual C++ .NET 2003, el objeto se crea de forma diferida, en la primera solicitud. Este cambio podría producir errores en los programas que se basan en la inicialización temprana.  
  
## <a name="see-also"></a>Vea también  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [Clase CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)   
 [Clase CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Información general de clases](../../atl/atl-class-overview.md)
