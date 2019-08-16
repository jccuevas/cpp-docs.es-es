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
ms.openlocfilehash: 0d27a6fa3c0070cd32c78971a7544327c51d4393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496919"
---
# <a name="ccomtearoffobject-class"></a>Clase CComTearOffObject

Esta clase implementa una interfaz de recorte.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parámetros

*Básica*<br/>
La clase de recorte, derivada de `CComTearOffObjectBase` y las interfaces que desea que admita el objeto de recorte.

ATL implementa sus interfaces de recorte en dos fases: los métodos `CComTearOffObjectBase` controlan el recuento de `QueryInterface`referencias y `CComTearOffObject` , mientras que implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|El constructor.|
|[CComTearOffObject::~CComTearOffObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|Incrementa el recuento de referencias de `CComTearOffObject` un objeto.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada en la clase de recorte o la clase propietaria.|
|[CComTearOffObject::Release](#release)|Disminuye el recuento de referencias para `CComTearOffObject` un objeto y lo destruye.|

### <a name="ccomtearoffobjectbase-methods"></a>Métodos CComTearOffObjectBase

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Constructor.|

### <a name="ccomtearoffobjectbase-data-members"></a>Miembros de datos de CComTearOffObjectBase

|||
|-|-|
|[m_pOwner](#m_powner)|Un puntero a un `CComObject` derivado de la clase propietaria.|

## <a name="remarks"></a>Comentarios

`CComTearOffObject`implementa una interfaz de recorte como un objeto independiente del que se crean instancias solo cuando se consulta la interfaz. El recorte se elimina cuando su recuento de referencias se convierte en cero. Normalmente, se genera una interfaz de recorte para una interfaz que se usa con poca frecuencia, ya que el uso de una desactivación guarda un puntero vtable en todas las instancias del objeto principal.

Debe derivar la clase que implementa el recorte desde `CComTearOffObjectBase` y desde cualquier interfaz que desee que admita el objeto de recorte. `CComTearOffObjectBase`es hace plantilla en la clase propietaria y en el modelo de subproceso. La clase propietaria es la clase del objeto para el que se está implementando una interrupción. Si no se especifica un modelo de subproceso, se utiliza el modelo de subproceso predeterminado.

Debe crear un mapa COM para la clase de recorte. Cuando ATL crea instancias de la recorte, creará `CComTearOffObject<CYourTearOffClass>` o. `CComCachedTearOffObject<CYourTearOffClass>`

Por ejemplo, en el ejemplo beeper, la `CBeeper2` clase es la clase Tear y la `CBeeper` clase es la clase propietaria:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="addref"></a>  CComTearOffObject::AddRef

Incrementa en uno el recuento de `CComTearOffObject` referencias del objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para los diagnósticos y las pruebas.

##  <a name="ccomtearoffobject"></a>  CComTearOffObject::CComTearOffObject

El constructor.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*pv*<br/>
de Puntero que se convertirá en un puntero a un `CComObject<Owner>` objeto.

### <a name="remarks"></a>Comentarios

Incrementa el recuento de referencias del propietario en uno.

##  <a name="dtor"></a>  CComTearOffObject::~CComTearOffObject

Destructor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados, llama a FinalRelease y disminuye el recuento de bloqueos del módulo.

##  <a name="ccomtearoffobjectbase"></a>  CComTearOffObject::CComTearOffObjectBase

El constructor.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Comentarios

Inicializa el miembro [m_pOwner](#m_powner) en NULL.

##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner

Un puntero a un objeto [CComObject](../../atl/reference/ccomobject-class.md) derivado de *Owner*.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parámetros

*Propietario*<br/>
de Clase para la que se está implementando un recorte.

### <a name="remarks"></a>Comentarios

El puntero se inicializa en NULL durante la construcción.

##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
de IID de la interfaz que se solicita.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz identificado por *IID*, o null si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Primero realiza consultas para las interfaces de la clase que se ha interrumpido. Si la interfaz no está allí, consulta la interfaz en el objeto propietario. Si la interfaz solicitada `IUnknown`es, devuelve `IUnknown` el del propietario.

##  <a name="release"></a>  CComTearOffObject::Release

Disminuye el recuento de referencias en uno y, si el recuento de referencias es cero, `CComTearOffObject`elimina.

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones que no son de depuración, siempre devuelve cero. En compilaciones de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas.

## <a name="see-also"></a>Vea también

[CComCachedTearOffObject (clase)](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
