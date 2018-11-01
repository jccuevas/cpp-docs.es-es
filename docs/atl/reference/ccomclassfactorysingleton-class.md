---
title: CComClassFactorySingleton (clase)
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: 760bf47ff818e301ddfbdeb8c44d318ab105b760
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517317"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton (clase)

Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase.

`CComClassFactorySingleton` se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un objeto único. Cada llamada a la `CreateInstance` método simplemente consulta este objeto para un puntero de interfaz.

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

Objetos ATL adquieren normalmente un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara `CComClassFactory` como el generador de clases de forma predeterminada. Para usar `CComClassFactorySingleton`, especifique el [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) macro en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance

Las llamadas `QueryInterface` a través de [m_spObj](#m_spobj) para recuperar un puntero de interfaz.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
[in] Si el objeto se crea como parte de un agregado y, a continuación, *pUnkOuter* debe ser el desconocido externo. En caso contrario, *pUnkOuter* debe ser NULL.

*riid*<br/>
[in] IID de la interfaz solicitada. Si *pUnkOuter* es distinto de NULL, *riid* debe ser `IID_IUnknown`.

*ppvObj*<br/>
[out] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj

El [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto construido por `CComClassFactorySingleton`.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Comentarios

Cada llamada a la [CreateInstance](#createinstance) método simplemente consulta este objeto para un puntero de interfaz.

Tenga en cuenta que el formulario actual de `m_spObj` presenta un cambio importante de la forma en que `CComClassFactorySingleton` funcionó en versiones anteriores de ATL. En versiones anteriores el `CComClassFactorySingleton` se creó el objeto al mismo tiempo como el generador de clases, durante la inicialización del servidor. En Visual C++ .NET 2003, el objeto se crea de forma diferida, en la primera solicitud. Este cambio podría producir errores en programas que se basan en la inicialización temprana.

## <a name="see-also"></a>Vea también

[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 (clase)](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread (clase)](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
