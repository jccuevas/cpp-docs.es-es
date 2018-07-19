---
title: Especificar páginas de propiedades (ATL) | Documentos de Microsoft
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
ms.openlocfilehash: e8d4cbeaa8ea9a57f9287f2d2fe78c61884ba4a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358930"
---
# <a name="specifying-property-pages"></a>Especificar páginas de propiedades
Cuando se crea un control ActiveX, a menudo deseará asociarlo a páginas de propiedades que pueden usarse para establecer las propiedades del control. Controla el uso de contenedores el **ISpecifyPropertyPages** interfaz para averiguar qué páginas de propiedades pueden usarse para establecer las propiedades del control. Debe implementar esta interfaz en el control.  
  
 Para implementar **ISpecifyPropertyPages** con ATL, siga estos pasos:  
  
1.  Derive la clase de [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).  
  
2.  Agregue una entrada para **ISpecifyPropertyPages** al mapa de COM de la clase.  
  
3.  Agregar un [PROP_PAGE](reference/property-map-macros.md#prop_page) entrada para la asignación de propiedad para cada página asociada con el control.  
  
> [!NOTE]
>  Al generar un control estándar mediante el [Asistente para controles ATL](../atl/reference/atl-control-wizard.md), solo tendrá que agregar el `PROP_PAGE` entradas para la asignación de propiedad. El asistente genera el código necesario para el resto de pasos.  
  
 Los contenedores mostrará las páginas de propiedades especificado en el mismo orden que el `PROP_PAGE` entradas en la asignación de propiedad. Por lo general, debe colocar las entradas de página de propiedades estándar después de las entradas de las páginas personalizadas en la asignación de propiedad, por lo que los usuarios vean las páginas específicas de su control en primer lugar.  
  
## <a name="example"></a>Ejemplo  
 La clase siguiente para un calendario de control utiliza la **ISpecifyPropertyPages** interfaz para indicar a los contenedores que se pueden establecer sus propiedades mediante una página de fechas personalizado y la página de color estándar.  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../atl/atl-com-property-pages.md)   
 [Ejemplo ATLPages](../visual-cpp-samples.md)

