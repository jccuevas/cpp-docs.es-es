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
ms.openlocfilehash: 892153e47ac4e9dd45d5dfc01b76f1ce29d23938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497452"
---
# <a name="ccomclassfactory-class"></a>Clase CComClassFactory

Esta clase implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

## <a name="syntax"></a>Sintaxis

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|Crea un objeto del CLSID especificado.|
|[CComClassFactory::LockServer](#lockserver)|Bloquea el generador de clases en la memoria.|

## <a name="remarks"></a>Comentarios

`CComClassFactory`implementa la interfaz [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , que contiene métodos para crear un objeto de un CLSID determinado, así como el bloqueo del generador de clases en la memoria para permitir que se creen nuevos objetos más rápidamente. `IClassFactory`debe implementarse para cada clase que se registre en el registro del sistema y a la que se asigne un CLSID.

Normalmente, los objetos ATL adquieren un generador de clases mediante la derivación de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Esta clase incluye la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), que declara `CComClassFactory` como el generador de clases predeterminado. Para invalidar este valor predeterminado, especifique una `DECLARE_CLASSFACTORY`de las macros *XXX* en la definición de clase. Por ejemplo, la macro [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) utiliza la clase especificada para el generador de clases:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

La definición de clase anterior especifica `CMyClassFactory` que se usará como generador de clases predeterminado del objeto. `CMyClassFactory`debe derivar `CComClassFactory` de e `CreateInstance`invalidar.

ATL proporciona otras tres macros que declaran un generador de clases:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Usa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), que controla la creación a través de una licencia.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Usa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), que crea objetos en varios apartamentos.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Usa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), que construye un solo objeto [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) .

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="createinstance"></a>  CComClassFactory::CreateInstance

Crea un objeto del CLSID especificado y recupera un puntero de interfaz a este objeto.

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

##  <a name="lockserver"></a>  CComClassFactory::LockServer

Incrementa y disminuye el recuento de bloqueos del módulo `_Module::Lock` mediante `_Module::Unlock`una llamada a y, respectivamente.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parámetros

*fLock*<br/>
de Si es TRUE, el recuento de bloqueos se incrementa; de lo contrario, se reduce el recuento de bloqueos.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`_Module`hace referencia a la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o a una clase derivada de ella.

La `LockServer` llamada a permite a un cliente mantener en un generador de clases para que se puedan crear rápidamente varios objetos.

## <a name="see-also"></a>Vea también

[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
