---
title: "Páginas de propiedades COM de ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 08b1c31aeaba25f4eadad5225dd2f5607cf7053c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-com-property-pages"></a>Páginas de propiedades COM de ATL
Páginas de propiedades COM proporcionan una interfaz de usuario para establecer las propiedades (o llamar a los métodos) de uno o más objetos COM. Páginas de propiedades se utilizan ampliamente por los controles de ActiveX para proporcionar interfaces de usuario enriquecida que permite que las propiedades de control que se establecerá en tiempo de diseño.  
  
 Páginas de propiedades son objetos COM que implementan la [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) o [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) interfaz. Estas interfaces proporcionan métodos que permiten a la página asociar a un `site` (un objeto COM que representa el contenedor de la página) y un número de *objetos* (objetos COM cuyos métodos se llamará en respuesta a los cambios realizadas por el usuario de la página de propiedades). El contenedor de la página de propiedades es responsable de llamar a métodos en la interfaz de la página de propiedades para indicar a la página cuando Mostrar u ocultar la interfaz de usuario y cuándo se deben aplicar los cambios realizados por el usuario a los objetos subyacentes.  
  
 Cada página de propiedades se puede compilar completamente independiente de los objetos cuyas propiedades se pueden establecer. Todo lo que una página de propiedades es necesario comprender una interfaz determinada (o conjunto de interfaces) y para proporcionar una interfaz de usuario para llamar a métodos en esa interfaz.  
  
 Para obtener más información, consulte [hojas de propiedades y páginas de propiedades](http://msdn.microsoft.com/library/windows/desktop/ms686577) en el [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Especificar páginas de propiedades](../atl/specifying-property-pages.md)  
 Enumera los pasos necesarios para especificar páginas de propiedades para un control y se muestra una clase de ejemplo.  
  
 [Implementar páginas de propiedades](../atl/implementing-property-pages.md)  
 Se enumeran los pasos para implementar páginas de propiedades, incluidos los métodos de invalidación. Le guía a través de un ejemplo completo basado en el programa de ejemplo ATLPages.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ejemplo ATLPages](../visual-cpp-samples.md)  
 El extracto del ejemplo ATLPages, que implementa una página de propiedad mediante `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)

