---
title: Clase CComClassFactory
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 041575339906b83488697f1db5a7f8b08b53070e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321021"
---
# <a name="ccomclassfactory-class"></a>Clase CComClassFactory

Esta clase implementa el [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) interfaz.

## <a name="syntax"></a>Sintaxis

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|
|[CComClassFactory::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|

## <a name="remarks"></a>Observaciones

`CComClassFactory`implementa la interfaz [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) que contiene métodos para crear un objeto de un CLSID determinado, así como bloquear el generador de clases en la memoria para permitir que se creen nuevos objetos más rápidamente. `IClassFactory`debe implementarse para cada clase que registre en el registro del sistema y a la que asigne un CLSID.

Los objetos ATL normalmente adquieren un generador de clases derivando de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)la macro `CComClassFactory` DECLARE_CLASSFACTORY , que declara como generador de clases predeterminado. Para invalidar este valor predeterminado, especifique una de las macros `DECLARE_CLASSFACTORY` *XXX* en la definición de clase. Por ejemplo, la macro [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) utiliza la clase especificada para el generador de clases:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

La definición de `CMyClassFactory` clase anterior especifica que se usará como generador de clases predeterminado del objeto. `CMyClassFactory`debe derivar `CComClassFactory` de `CreateInstance`y anular .

ATL proporciona otras tres macros que declaran un generador de clases:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Utiliza [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Utiliza [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios apartamentos.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Utiliza [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye un único [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClassFactory::CreateInstance

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

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

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClassFactory::LockServer

Incrementa y disminuye el recuento de `_Module::Lock` bloqueos del módulo llamando y `_Module::Unlock`, respectivamente.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*Rebaño*<br/>
[en] Si es TRUE, el recuento de bloqueos se incrementa; de lo contrario, el recuento de bloqueos se reduce.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

`_Module`hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o a una clase derivada de ella.

La `LockServer` llamada permite a un cliente aferrarse a un generador de clases para que se puedan crear varios objetos rápidamente.

## <a name="see-also"></a>Consulte también

[Clase CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
