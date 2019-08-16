---
title: Páginas de propiedades COM de ATL
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
ms.openlocfilehash: f6f549388e69e9549c64645de758d92822205fd5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491859"
---
# <a name="atl-com-property-pages"></a>Páginas de propiedades COM de ATL

Las páginas de propiedades COM proporcionan una interfaz de usuario para establecer las propiedades (o llamar a los métodos) de uno o más objetos COM. Los controles ActiveX usan extensamente páginas de propiedades para proporcionar interfaces de usuario enriquecidas que permiten establecer las propiedades de los controles en tiempo de diseño.

Las páginas de propiedades son objetos COM que implementan la interfaz [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) o [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) . Estas interfaces proporcionan métodos que permiten asociar la página con un `site` (un objeto com que representa el contenedor de la página) y varios *objetos* (objetos com cuyos métodos se llamarán en respuesta a los cambios realizados por el usuario del Página de propiedades). El contenedor de la página de propiedades es responsable de llamar a los métodos de la interfaz de página de propiedades para indicar a la página Cuándo Mostrar u ocultar su interfaz de usuario y cuándo aplicar los cambios realizados por el usuario a los objetos subyacentes.

Cada página de propiedades se puede compilar completamente de forma independiente de los objetos cuyas propiedades se pueden establecer. Todo lo que necesita una página de propiedades es comprender una interfaz determinada (o un conjunto de interfaces) y proporcionar una interfaz de usuario para llamar a los métodos de esa interfaz.

Para obtener más información, vea [hojas de propiedades y páginas de propiedades](/windows/win32/com/property-sheets-and-property-pages) en el Windows SDK.

## <a name="in-this-section"></a>En esta sección

[Especificar páginas de propiedades](../atl/specifying-property-pages.md)<br/>
Enumera los pasos para especificar las páginas de propiedades para controlar y mostrar una clase de ejemplo.

[Implementar páginas de propiedades](../atl/implementing-property-pages.md)<br/>
Enumera los pasos para implementar páginas de propiedades, incluidos los métodos que se van a invalidar. Le guía a través de un ejemplo completo basado en el programa de ejemplo ATLPages.

## <a name="related-sections"></a>Secciones relacionadas

[Ejemplos de Visual C++](../overview/visual-cpp-samples.md)<br/>
El ejemplo abstracto para el ejemplo ATLPages, que implementa una página de propiedades `IPropertyPageImpl`mediante.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)
