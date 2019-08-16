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
ms.openlocfilehash: 71705d02140f0392a9ce023c64e7b4125c14443f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497402"
---
# <a name="ccomclassfactorysingleton-class"></a>Clase CComClassFactorySingleton

Esta clase se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un solo objeto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase.

`CComClassFactorySingleton`se deriva de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) y usa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) para construir un solo objeto. Cada llamada al `CreateInstance` método simplemente consulta este objeto para obtener un puntero de interfaz.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Consulta `m_spObj` un puntero de interfaz.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Objeto [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) construido por `CComClassFactorySingleton`.|

## <a name="remarks"></a>Comentarios

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara `CComClassFactory` como el generador de clases predeterminado. Para usar `CComClassFactorySingleton`, especifique la macro [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance

Llama `QueryInterface` a través de [m_spObj](#m_spobj) para recuperar un puntero de interfaz.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
de Si el objeto se crea como parte de un agregado, *pUnkOuter* debe ser el desconocido externo. De lo contrario, *pUnkOuter* debe ser null.

*riid*<br/>
de IID de la interfaz solicitada. Si *pUnkOuter* no es null, *riid* debe ser `IID_IUnknown`.

*ppvObj*<br/>
enuncia Puntero al puntero de interfaz identificado por *riid*. Si el objeto no admite esta interfaz, *ppvObj* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj

Objeto [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) construido por `CComClassFactorySingleton`.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Comentarios

Cada llamada al método [CreateInstance](#createinstance) simplemente consulta este objeto para obtener un puntero de interfaz.

Tenga en cuenta que el formulario `m_spObj` actual de presenta un cambio importante de la `CComClassFactorySingleton` forma en que funcionó en versiones anteriores de ATL. En versiones anteriores, `CComClassFactorySingleton` el objeto se creó al mismo tiempo que el generador de clases durante la inicialización del servidor. En Visual C++.NET 2003 y versiones posteriores, el objeto se crea de forma diferida en la primera solicitud. Este cambio puede provocar errores en los programas que se basan en la inicialización temprana.

## <a name="see-also"></a>Vea también

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 (clase)](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread (clase)](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
