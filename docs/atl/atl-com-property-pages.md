---
title: Páginas de propiedades COM de ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ec1fb89817da663dd088dadc9b667a3ff0aef46
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200983"
---
# <a name="atl-com-property-pages"></a>Páginas de propiedades COM de ATL
Páginas de propiedades COM proporcionan una interfaz de usuario para establecer las propiedades (o llamar a los métodos) de uno o más objetos COM. Páginas de propiedades se utilizan ampliamente por los controles de ActiveX para proporcionar interfaces de usuario enriquecida que permite que las propiedades de control debe establecerse en tiempo de diseño.  
  
 Páginas de propiedades son objetos COM que implementan la [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) o [IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) interfaz. Estas interfaces proporcionan métodos que permiten a la página se asocie a un `site` (un objeto COM que representa el contenedor de la página) y un número de *objetos* (objetos COM cuyos métodos se llamará en respuesta a cambios realizada por el usuario de la página de propiedades). El contenedor de la página de propiedades es responsable de llamar a métodos en la interfaz de la página de propiedad para indicar a la página cuando Mostrar u ocultar su interfaz de usuario y cuándo se deben aplicar los cambios realizados por el usuario a los objetos subyacentes.  
  
 Cada página de propiedades se puede compilar completamente independiente de los objetos cuyas propiedades se pueden establecer. Todo lo que una página de propiedades es necesita para comprender una interfaz determinada (o conjunto de interfaces) y proporcionar una interfaz de usuario para llamar a métodos de esa interfaz.  
  
 Para obtener más información, consulte [hojas de propiedades y páginas de propiedades](/windows/desktop/com/property-sheets-and-property-pages) en el SDK de Windows.  
  
## <a name="in-this-section"></a>En esta sección  
 [Especificar páginas de propiedades](../atl/specifying-property-pages.md)  
 Se enumeran los pasos para especificar las páginas de propiedades para un control y se muestra una clase de ejemplo.  
  
 [Implementar páginas de propiedades](../atl/implementing-property-pages.md)  
 Se enumeran los pasos para implementar páginas de propiedades, incluidos los métodos de invalidación. Le guía a través de un ejemplo completo basado en el programa de ejemplo ATLPages.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ejemplo ATLPages](../visual-cpp-samples.md)  
 El extracto del ejemplo ATLPages, que implementa una página de propiedad mediante `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)

