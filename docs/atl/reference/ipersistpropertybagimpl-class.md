---
title: IPersistPropertyBagImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9ec437be7c719c4ba65b31465f9112fa250284d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751726"
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

*T*  
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

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
[Información general de clases](../../atl/atl-class-overview.md)
