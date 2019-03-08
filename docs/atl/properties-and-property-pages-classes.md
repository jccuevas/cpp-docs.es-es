---
title: Las propiedades y las clases de páginas de propiedades (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.properties
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: f5d318cecc527d0c41124ccf14326ea308007b1d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290474"
---
# <a name="properties-and-property-pages-classes"></a>Las propiedades y las clases de páginas de propiedades

Las clases siguientes admiten propiedades y páginas de propiedades:

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver) recupera o establece las propiedades de un objeto a través de un `IDispatch` puntero.

- [CStockPropImpl](../atl/reference/cstockpropimpl-class.md) implementa las propiedades estándar compatibles con ATL.

- [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md) tiene acceso a la información de las páginas de propiedades de un objeto.

- [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md) almacena propiedades de un objeto en un contenedor de propiedades proporcionados por el cliente.

- [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md) administra una determinada página de propiedades dentro de una hoja de propiedades.

- [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md) Similar a `IPropertyPageImpl`, pero también permite que un cliente seleccionar una propiedad específica en una página de propiedades.

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) obtiene los CLSID para las páginas de propiedades admitidos por un objeto.

## <a name="related-articles"></a>Artículos relacionados

[Tutorial de ATL](../atl/active-template-library-atl-tutorial.md)

[Páginas de propiedades COM de ATL](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)<br/>
[Macros de mapa de propiedades](../atl/reference/property-map-macros.md)
