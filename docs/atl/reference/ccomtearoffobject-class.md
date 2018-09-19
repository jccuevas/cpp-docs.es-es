---
title: CComTearOffObject (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
dev_langs:
- C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecbf2b415b93526fe856e21411431eb1f20b4c42
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089585"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject (clase)

Esta clase implementa una interfaz desplazable.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parámetros

*base*<br/>
Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que el objeto desplazable para admitir.

ATL implementa sus interfaces divisibles en dos fases: la `CComTearOffObjectBase` métodos controlan el recuento de referencias y `QueryInterface`, mientras que `CComTearOffObject` implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|El constructor.|
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|Incrementa el recuento de referencias para un `CComTearOffObject` objeto.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada en la clase desplazable o la clase propietaria.|
|[CComTearOffObject::Release](#release)|Disminuye el recuento de referencias para un `CComTearOffObject` de objeto y lo destruye.|

### <a name="ccomtearoffobjectbase-methods"></a>Métodos CComTearOffObjectBase

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Constructor.|

### <a name="ccomtearoffobjectbase-data-members"></a>Miembros de datos CComTearOffObjectBase

|||
|-|-|
|[m_pOwner](#m_powner)|Un puntero a un `CComObject` derivado de la clase propietaria.|

## <a name="remarks"></a>Comentarios

`CComTearOffObject` implementa una interfaz divisible como un objeto independiente que se crean instancias sólo cuando se consulta esa interfaz. Las tiras se eliminan cuando su recuento de referencias se convierte en cero. Por lo general, cree una interfaz desplazable para una interfaz que se usa con poca frecuencia, dado que uso un desplazable guarda un puntero de vtable en todas las instancias de su objeto principal.

Debe derivar la clase que implementa el desplazable de `CComTearOffObjectBase` y desde cualquier interfaces desea que el objeto desplazable para admitir. `CComTearOffObjectBase` se hace plantilla en la clase propietaria y el modelo de subprocesos. La clase propietaria es la clase del objeto para el que está implementando un desplazable. Si no especifica un modelo de subprocesos, se usa el modelo de subprocesos de forma predeterminada.

Debe crear un mapa COM para la clase desplazable. Cuando se crea una instancia de ATL la desplazable, creará `CComTearOffObject<CYourTearOffClass>` o `CComCachedTearOffObject<CYourTearOffClass>`.

Por ejemplo, en el ejemplo de BUSCAPERSONAS, el `CBeeper2` es la clase desplazable y `CBeeper` es la clase de propietario:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="addref"></a>  CComTearOffObject::AddRef

Incrementa el recuento de referencias de la `CComTearOffObject` objeto por uno.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para el diagnóstico y prueba.

##  <a name="ccomtearoffobject"></a>  CComTearOffObject::CComTearOffObject

El constructor.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
[in] Puntero que se convertirá en un puntero a un `CComObject<Owner>` objeto.

### <a name="remarks"></a>Comentarios

Recuento de referencias del propietario se incrementa en uno.

##  <a name="dtor"></a>  CComTearOffObject:: ~ CComTearOffObject

Destructor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados, las llamadas FinalRelease y reduce el módulo de recuento de bloqueo.

##  <a name="ccomtearoffobjectbase"></a>  CComTearOffObject::CComTearOffObjectBase

El constructor.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Comentarios

Inicializa el [m_pOwner](#m_powner) miembro en NULL.

##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner

Un puntero a un [CComObject](../../atl/reference/ccomobject-class.md) objeto derivado de *propietario*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parámetros

*Propietario*<br/>
[in] La clase para el que está implementando un desplazable.

### <a name="remarks"></a>Comentarios

El puntero se inicializa en NULL durante la construcción.

##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*IID*<br/>
[in] IID de la interfaz que se solicita.

*ppvObject*<br/>
[out] Un puntero al puntero de interfaz identificado por *iid*, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Consultas en primer lugar para las interfaces de la clase desplazable. Si la interfaz no está allí, las consultas para la interfaz en el objeto propietario. Si la interfaz solicitada es `IUnknown`, devuelve el `IUnknown` del propietario.

##  <a name="release"></a>  CComTearOffObject::Release

Disminuye el recuento de referencias en uno y, si el recuento de referencias es cero, se elimina el `CComTearOffObject`.

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Valor devuelto

En versiones no depuradas, siempre devuelve cero. En las compilaciones de depuración, devuelve un valor que puede ser útil para el diagnóstico o de pruebas.

## <a name="see-also"></a>Vea también

[CComCachedTearOffObject (clase)](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
