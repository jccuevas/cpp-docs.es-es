---
title: ISpecifyPropertyPagesImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d231f493fd2b2f2c492eec224a0ae041f175f53d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767355"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl (clase)

Esta clase implementa `IUnknown` y proporciona una implementación predeterminada de la [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interfaz.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parámetros

*T*  
La clase derivada de `ISpecifyPropertyPagesImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Rellena los valores de recuento de matriz de UUID. Cada UUID se corresponde con el CLSID de uno de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.|

## <a name="remarks"></a>Comentarios

El [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interfaz permite que un cliente obtener una lista de CLSID para las páginas de propiedades admitidos por un objeto. Clase `ISpecifyPropertyPagesImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

> [!NOTE]
>  No exponga el `ISpecifyPropertyPages` si el objeto no es compatible con páginas de propiedades de la interfaz.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

Rellena la matriz la [cauuid a](/windows/desktop/api/ocidl/ns-ocidl-tagcauuid) estructura con el CLSID para las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Comentarios

ATL usa asignación de propiedad del objeto para recuperar cada CLSID.

Consulte [ISpecifyPropertyPages::GetPages](/windows/desktop/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[IPropertyPageImpl (clase)](../../atl/reference/ipropertypageimpl-class.md)   
[IPerPropertyBrowsingImpl (clase)](../../atl/reference/iperpropertybrowsingimpl-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)
