---
title: Clase CComTearOffObject
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: de7528d3972991c233ee4b9037f609b89d0f7434
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327321"
---
# <a name="ccomtearoffobject-class"></a>Clase CComTearOffObject

Esta clase implementa una interfaz de desmontaje.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
Su clase de desmontaje, derivada de `CComTearOffObjectBase` y las interfaces que desea que su objeto de desmontaje para admitir.

ATL implementa sus interfaces de desmontaje `CComTearOffObjectBase` en dos fases: los métodos controlan el recuento de referencias y `QueryInterface`, mientras `CComTearOffObject` implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|El constructor.|
|[CComTearOffObject::-CComTearOffObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|Incrementa el recuento `CComTearOffObject` de referencias de un objeto.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada en la clase de desmontaje o en la clase de propietario.|
|[CComTearOffObject::Release](#release)|Disminuye el recuento de referencias `CComTearOffObject` de un objeto y lo destruye.|

### <a name="ccomtearoffobjectbase-methods"></a>Métodos CComTearOffObjectBase

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Constructor.|

### <a name="ccomtearoffobjectbase-data-members"></a>Miembros de datos CComTearOffObjectBase

|||
|-|-|
|[m_pOwner](#m_powner)|Puntero a `CComObject` un derivado de la clase de propietario.|

## <a name="remarks"></a>Observaciones

`CComTearOffObject`implementa una interfaz de desmontaje como un objeto independiente que se crea una instancia solo cuando se consulta esa interfaz. El desmontaje se elimina cuando su recuento de referencias se convierte en cero. Normalmente, se crea una interfaz de desmontaje para una interfaz que rara vez se utiliza, ya que el uso de un desgarro guarda un puntero vtable en todas las instancias del objeto principal.

Debe derivar la clase que implementa `CComTearOffObjectBase` el desmontaje de y de las interfaces que desee que admita el objeto de desmontaje. `CComTearOffObjectBase`se templatiza en la clase propietaria y el modelo de subprocesos. La clase owner es la clase del objeto para el que se está implementando un desgarro. Si no especifica un modelo de subprocesos, se utiliza el modelo de subprocesos predeterminado.

Debe crear un mapa COM para la clase de desmontaje. Cuando ATL crea una instancia del `CComTearOffObject<CYourTearOffClass>` desmontaje, creará o `CComCachedTearOffObject<CYourTearOffClass>`.

Por ejemplo, en el ejemplo `CBeeper2` BEEPER, la clase `CBeeper` es la clase de desmontaje y la clase es la clase propietaria:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a>CComTearOffObject::AddRef

Incrementa el recuento `CComTearOffObject` de referencias del objeto en uno.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos y pruebas.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject

El constructor.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
[en] Puntero que se convertirá en `CComObject<Owner>` un puntero a un objeto.

### <a name="remarks"></a>Observaciones

Incrementa el recuento de referencias del propietario en uno.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a>CComTearOffObject::-CComTearOffObject

Destructor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados, llama a FinalRelease y disminuye el recuento de bloqueos del módulo.

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase

El constructor.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Observaciones

Inicializa el miembro [m_pOwner](#m_powner) en NULL.

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a>CComTearOffObject::m_pOwner

Un puntero a un [CComObject](../../atl/reference/ccomobject-class.md) objeto derivado de *Owner*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parámetros

*Propietario*<br/>
[en] La clase para la que se está implementando un desgarro.

### <a name="remarks"></a>Observaciones

El puntero se inicializa en NULL durante la construcción.

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComTearOffObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] El IID de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *iid*, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Consulta primero las interfaces de la clase de desmontaje. Si la interfaz no está allí, consulta la interfaz en el objeto propietario. Si la interfaz solicitada es `IUnknown`, devuelve el `IUnknown` propietario.

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a>CComTearOffObject::Release

Disminuye el recuento de referencias en uno y, si el `CComTearOffObject`recuento de referencias es cero, elimina el archivo .

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones que no son de depuración, siempre devuelve cero. En compilaciones de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas.

## <a name="see-also"></a>Consulte también

[Clase CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
