---
title: IPersistPropertyBagImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: 800c38c15e4ec8028fba9188d75e49be7ca51146
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274898"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl (clase)

Esta clase implementa `IUnknown` y permite que un objeto guardar sus propiedades en una bolsa de propiedades proporcionados por el cliente.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IPersistPropertyBagImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializa un objeto recién creado. La implementación de ATL devuelve S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Carga las propiedades del objeto de un contenedor de propiedades proporcionados por el cliente.|
|[IPersistPropertyBagImpl::Save](#save)|Guarda las propiedades del objeto en un contenedor de propiedades proporcionados por el cliente.|

## <a name="remarks"></a>Comentarios

El [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx) interfaz permite que un objeto guardar sus propiedades en una bolsa de propiedades proporcionados por el cliente. Clase `IPersistPropertyBagImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

`IPersistPropertyBag` funciona junto con [IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx) y [IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx). Estas dos interfaces de este últimas deben implementarse mediante el cliente. A través de `IPropertyBag`, el cliente guarda y carga las propiedades del objeto individuales. A través de `IErrorLog`, el objeto y el cliente pueden notificar los errores detectados.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Comentarios

Consulte [IPersist:: GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) en el SDK de Windows.

##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew

Inicializa un objeto recién creado.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) en el SDK de Windows.

##  <a name="load"></a>  IPersistPropertyBagImpl::Load

Carga las propiedades del objeto de un contenedor de propiedades proporcionados por el cliente.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Comentarios

ATL utiliza la asignación de propiedad del objeto para recuperar esta información.

Consulte [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768206.aspx) en el SDK de Windows.

##  <a name="save"></a>  IPersistPropertyBagImpl::Save

Guarda las propiedades del objeto en un contenedor de propiedades proporcionados por el cliente.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Comentarios

ATL utiliza la asignación de propiedad del objeto para almacenar esta información. De forma predeterminada, este método guarda todas las propiedades, independientemente del valor de *fSaveAllProperties*.

Consulte [IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
