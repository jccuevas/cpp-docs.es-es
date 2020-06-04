---
title: Clase IPropertyPage2Impl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: d112a2411a9debbf2eb77e6b851f4500e8d32ab8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329592"
---
# <a name="ipropertypage2impl-class"></a>Clase IPropertyPage2Impl

Esta clase `IUnknown` implementa y hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPropertyPage2Impl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Especifica qué control de propiedades recibirá el foco cuando se active la página de propiedades. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Observaciones

El [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) interfaz extiende [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) agregando el `EditProperty` método. Este método permite a un cliente seleccionar una propiedad específica en un objeto de página de propiedades.

La `IPropertyPage2Impl` clase simplemente `IPropertyPage2::EditProperty`devuelve E_NOTIMPL para . Sin embargo, hereda la implementación predeterminada de `IUnknown` [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

Al crear una página de propiedades, la `IPropertyPageImpl`clase se deriva normalmente de . Para proporcionar la `IPropertyPage2`compatibilidad adicional de , `EditProperty` modifique la definición de clase e invalide el método.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a>IPropertyPage2Impl::EditProperty

Especifica qué control de propiedades recibirá el foco cuando se active la página de propiedades.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Vea [IPropertyPage2::EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Clase ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
