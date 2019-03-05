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
ms.openlocfilehash: bf76182242f7b76e3a2c18f85b72674e88afa737
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287510"
---
# <a name="ipropertypage2impl-class"></a>Clase IPropertyPage2Impl

Esta clase implementa `IUnknown` y hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IPropertyPage2Impl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Especifica qué control propiedad recibirá el foco cuando se activa la página de propiedades. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

El [IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) interfaz extiende [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) agregando el `EditProperty` método. Este método permite que un cliente seleccionar una propiedad específica en un objeto de la página de propiedad.

Clase `IPropertyPage2Impl` simplemente devuelve E_NOTIMPL para `IPropertyPage2::EditProperty`. Sin embargo, hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

Cuando se crea una página de propiedades, la clase se deriva normalmente de `IPropertyPageImpl`. Para proporcionar la compatibilidad adicional de `IPropertyPage2`, modifique la definición de clase e invalide el `EditProperty` método.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

Especifica qué control propiedad recibirá el foco cuando se activa la página de propiedades.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IPropertyPage2::EditProperty](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage2-editproperty) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[IPerPropertyBrowsingImpl (clase)](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl (clase)](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
