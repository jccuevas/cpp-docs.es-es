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
ms.openlocfilehash: 73879a73a48290e19d2a27307884953129826df7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497487"
---
# <a name="ccomclassfactoryautothread-class"></a>Clase CComClassFactoryAutoThread

Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) y permite crear objetos en varios apartamentos.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|

## <a name="remarks"></a>Comentarios

`CComClassFactoryAutoThread`es similar a [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), pero permite crear objetos en varios apartamentos. Para aprovechar esta compatibilidad, derive el módulo EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) como el generador de clases predeterminado. Para usar `CComClassFactoryAutoThread`, especifique la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) en la definición de clase del objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="createinstance"></a>  CComClassFactoryAutoThread::CreateInstance

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>Comentarios

Si el módulo se deriva de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` primero selecciona un subproceso para crear el objeto en el contenedor asociado.

##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer

Incrementa y disminuye el recuento de bloqueos del módulo `_Module::Lock` mediante `_Module::Unlock`una llamada a y, respectivamente.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*fLock*<br/>
de Si es TRUE, el recuento de bloqueos se incrementa; de lo contrario, se reduce el recuento de bloqueos.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Cuando se `CComClassFactoryAutoThread`usa `_Module` , normalmente hace referencia a la instancia global de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

La `LockServer` llamada a permite a un cliente mantener en un generador de clases para que se puedan crear rápidamente varios objetos.

## <a name="see-also"></a>Vea también

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2 (clase)](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton (clase)](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
