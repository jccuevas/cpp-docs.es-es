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
ms.openlocfilehash: 5ec6cb2f4fc6931a1bec429068b558bf7ac1906e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495605"
---
# <a name="ipropertypage2impl-class"></a>Clase IPropertyPage2Impl

Esta clase implementa `IUnknown` y hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPropertyPage2Impl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Especifica qué control de propiedad recibirá el foco cuando se active la página de propiedades. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

La interfaz [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) extiende [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) agregando el `EditProperty` método. Este método permite a un cliente seleccionar una propiedad específica en un objeto de página de propiedades.

La `IPropertyPage2Impl` clase simplemente devuelve E_NOTIMPL `IPropertyPage2::EditProperty`para. Sin embargo, hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) e implementa `IUnknown` enviando información al dispositivo de volcado en las compilaciones de depuración.

Cuando se crea una página de propiedades, la clase se deriva normalmente `IPropertyPageImpl`de. Para proporcionar la compatibilidad adicional de `IPropertyPage2`, modifique la definición de clase e invalide el `EditProperty` método.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

Especifica qué control de propiedad recibirá el foco cuando se active la página de propiedades.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IPropertyPage2:: EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) en el Windows SDK.

## <a name="see-also"></a>Vea también

[IPerPropertyBrowsingImpl (clase)](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl (clase)](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
