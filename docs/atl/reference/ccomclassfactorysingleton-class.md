---
title: Clase CComClassFactorySingleton
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: ec860f7ef59b7d3289bf2e18fea0f0e064a7c8f9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320824"
---
# <a name="ccomclassfactorysingleton-class"></a>Clase CComClassFactorySingleton

Esta clase deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un único objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Tu clase.

`CComClassFactorySingleton`deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y utiliza [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un único objeto. Cada llamada `CreateInstance` al método simplemente consulta este objeto para un puntero de interfaz.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Consulta `m_spObj` un puntero de interfaz.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|El [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto `CComClassFactorySingleton`construido por .|

## <a name="remarks"></a>Observaciones

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)la macro `CComClassFactory` DECLARE_CLASSFACTORY , que declara como generador de clases predeterminado. Para `CComClassFactorySingleton`utilizar , especifique la [macro DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClassFactorySingleton::CreateInstance

Llamadas `QueryInterface` a través [de m_spObj](#m_spobj) para recuperar un puntero de interfaz.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
[en] Si el objeto se crea como parte de un agregado, *pUnkOuter* debe ser el desconocido externo. De lo contrario, *pUnkOuter* debe ser NULL.

*riid*<br/>
[en] El IID de la interfaz solicitada. Si *pUnkOuter* no es NULL, `IID_IUnknown` *riid* debe ser .

*ppvObj*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

El [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto `CComClassFactorySingleton`construido por .

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Observaciones

Cada llamada al método [CreateInstance](#createinstance) simplemente consulta este objeto para un puntero de interfaz.

Tenga en cuenta `m_spObj` que la forma actual `CComClassFactorySingleton` de presentar un cambio importante de la forma en que funcionaba en versiones anteriores de ATL. En versiones `CComClassFactorySingleton` anteriores, el objeto se creaba al mismo tiempo que el generador de clases, durante la inicialización del servidor. En Visual C++.NET 2003 y versiones posteriores, el objeto se crea perezosamente, en la primera solicitud. Este cambio podría provocar errores en los programas que se basan en la inicialización temprana.

## <a name="see-also"></a>Consulte también

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Clase CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Clase CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Clase CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
