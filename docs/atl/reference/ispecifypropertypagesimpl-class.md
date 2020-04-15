---
title: Clase ISpecifyPropertyPagesImpl
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: 06b6b60227a659bd35e042952c7464971fc40bdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326413"
---
# <a name="ispecifypropertypagesimpl-class"></a>Clase ISpecifyPropertyPagesImpl

Esta clase `IUnknown` implementa y proporciona una implementación predeterminada de la [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) interfaz.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `ISpecifyPropertyPagesImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Rellena una matriz contada de valores UUID. Cada UUID corresponde al CLSID de una de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.|

## <a name="remarks"></a>Observaciones

El [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) interfaz permite a un cliente para obtener una lista de CLSID para las páginas de propiedades admitidas por un objeto. Clase `ISpecifyPropertyPagesImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

> [!NOTE]
> No exponga `ISpecifyPropertyPages` la interfaz si el objeto no admite páginas de propiedades.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages

Rellena la matriz de la estructura [CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid) con los CLSID de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Observaciones

ATL utiliza el mapa de propiedades del objeto para recuperar cada CLSID.

Consulte [ISpecifyPropertyPages::GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[Clase IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
