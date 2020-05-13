---
title: Clase CComClassFactoryAutoThread
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: e997d92adfa9df46c82dacbd297db495b037c6e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320903"
---
# <a name="ccomclassfactoryautothread-class"></a>Clase CComClassFactoryAutoThread

Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) y permite crear objetos en varios apartamentos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|

## <a name="remarks"></a>Observaciones

`CComClassFactoryAutoThread`es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite crear objetos en varios apartamentos. Para aprovechar esta compatibilidad, derive el módulo EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la [macro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para `CComClassFactoryAutoThread`utilizar , especifique la [macro DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClassFactoryAutoThread::CreateInstance

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>Observaciones

Si el módulo deriva de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` primero selecciona un subproceso para crear el objeto en el apartamento asociado.

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComClassFactoryAutoThread::LockServer

Incrementa y disminuye el recuento de `_Module::Lock` bloqueos del módulo llamando y `_Module::Unlock`, respectivamente.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*Rebaño*<br/>
[en] Si es TRUE, el recuento de bloqueos se incrementa; de lo contrario, el recuento de bloqueos se reduce.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Cuando `CComClassFactoryAutoThread`se `_Module` usa , normalmente hace referencia a la instancia global de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

La `LockServer` llamada permite a un cliente aferrarse a un generador de clases para que se puedan crear rápidamente varios objetos.

## <a name="see-also"></a>Consulte también

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Clase CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Clase CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Clase CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
