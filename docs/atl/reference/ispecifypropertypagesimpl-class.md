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
ms.openlocfilehash: c201cf6d9d89ab1a6a8e888deee1be79e5770490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495411"
---
# <a name="ispecifypropertypagesimpl-class"></a>Clase ISpecifyPropertyPagesImpl

Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la interfaz [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `ISpecifyPropertyPagesImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Rellena una matriz contada de valores UUID. Cada UUID corresponde al CLSID para una de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.|

## <a name="remarks"></a>Comentarios

La interfaz [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) permite a un cliente obtener una lista de CLSID para las páginas de propiedades admitidas por un objeto. La `ISpecifyPropertyPagesImpl` clase proporciona una implementación predeterminada de esta interfaz e `IUnknown` implementa enviando información al dispositivo de volcado en las compilaciones de depuración.

> [!NOTE]
>  No exponga la `ISpecifyPropertyPages` interfaz si el objeto no admite páginas de propiedades.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

Rellena la matriz de la estructura [CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid) con los CLSID de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Comentarios

ATL usa el mapa de propiedades del objeto para recuperar cada CLSID.

Vea [ISpecifyPropertyPages:: GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) en el Windows SDK.

## <a name="see-also"></a>Vea también

[IPropertyPageImpl (clase)](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl (clase)](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
