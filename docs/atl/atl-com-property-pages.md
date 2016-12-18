---
title: "P&#225;ginas de propiedades COM de ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos ATL COM"
  - "páginas de propiedades ATL"
  - "objetos COM, ATL"
  - "páginas de propiedades COM"
  - "páginas de propiedades, ATL"
  - "páginas de propiedades, COM"
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# P&#225;ginas de propiedades COM de ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las páginas de propiedades COM proporcionan una interfaz de usuario para establecer las propiedades \(o llamar a los métodos\) de uno o más objetos COM.  Las páginas de propiedades son utilizadas ampliamente por los controles ActiveX para proporcionar interfaces de usuario complejas que permiten que las propiedades del control establece en tiempo de diseño.  
  
 Las páginas de propiedades son objetos COM que implementan la interfaz de [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) o de [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) .  Estas interfaces proporcionan métodos que permiten que la página se asociado a `site` \(un objeto COM que representa el contenedor de la página\) y varios *objetos* \(objetos COM cuyos métodos se llamará en respuesta a los cambios realizados por el usuario de la página de propiedades\).  El contenedor de la página de propiedades es responsable de llamar a métodos en la interfaz de la página de propiedades para indicar la página cuándo mostrar u ocultar la interfaz de usuario, y cuándo aplicar los cambios realizados por el usuario a los objetos subyacentes.  
  
 Cada página de la propiedad se puede compilar completamente independientemente de los objetos cuyas propiedades se pueden establecer.  Todo lo que una página de propiedades necesita es comprender una interfaz determinada \(o conjunto de interfaces\) y proporcionar una interfaz de usuario para llamar a métodos de la interfaz.  
  
 Para obtener más información, vea [hojas de propiedades y páginas de propiedades](http://msdn.microsoft.com/library/windows/desktop/ms686577) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## En esta sección  
 [especificar las páginas de propiedades](../atl/specifying-property-pages.md)  
 Muestra los pasos para especificar páginas de propiedades para el control y se muestra una clase de ejemplo.  
  
 [Implementar páginas de propiedades](../atl/implementing-property-pages.md)  
 Muestra los pasos para implementar páginas de propiedades, incluidos los métodos para reemplazar.  Explica un ejemplo completo basado en el programa de ejemplo ATLPages.  
  
## Secciones relacionadas  
 [Ejemplo ATLPages](../top/visual-cpp-samples.md)  
 El resumen de ejemplo para el ejemplo ATLPages, que implementa una página de propiedades mediante `IPropertyPageImpl`.  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas conceptuales sobre cómo programar utilizando Active Template Library.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)