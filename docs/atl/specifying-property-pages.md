---
title: Especificar páginas de propiedades (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- ISpecifyPropertyPages
dev_langs:
- C++
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db0445e83bbcae6baa45d4a482489e6761fa945a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069435"
---
# <a name="specifying-property-pages"></a>Especificar páginas de propiedades

Cuando se crea un control ActiveX, que a menudo desea asociarla a páginas de propiedades que pueden usarse para establecer las propiedades del control. Controlar el uso de contenedores el `ISpecifyPropertyPages` interfaz para averiguar qué páginas de propiedades pueden usarse para establecer las propiedades del control. Deberá implementar esta interfaz en un control.

Para implementar `ISpecifyPropertyPages` mediante ATL, realice los pasos siguientes:

1. Derive la clase de [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).

2. Agregue una entrada para `ISpecifyPropertyPages` al mapa COM de la clase.

3. Agregar un [PROP_PAGE](reference/property-map-macros.md#prop_page) entrada al mapa de propiedades para cada página asociada al control.

> [!NOTE]
>  Al generar un control estándar mediante el [Asistente para controles ATL](../atl/reference/atl-control-wizard.md), sólo tendrá que agregar las entradas PROP_PAGE al mapa de propiedades. El asistente genera el código necesario para los demás pasos.

Los contenedores mostrarán las páginas de propiedades especificada en el mismo orden que las entradas PROP_PAGE en la asignación de propiedad. Por lo general, debería colocar entradas de la página de propiedades estándar después de las entradas para las páginas personalizadas en el mapa de propiedades, para que los usuarios ven las páginas específicas de su control primero.

## <a name="example"></a>Ejemplo

La siguiente clase de un calendario de control usa el `ISpecifyPropertyPages` interfaz para indicar a los contenedores que se pueden establecer sus propiedades mediante una página personalizada de fecha y la página de cotizaciones de color.

[!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../atl/atl-com-property-pages.md)<br/>
[Ejemplo ATLPages](../visual-cpp-samples.md)

