---
title: "How to: Search for Symbols in Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbols, finding"
  - "resources [Visual Studio], searching for symbols"
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Search for Symbols in Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para buscar símbolos en recursos:  
  
1.  En el menú **Edición**, elija **Buscar símbolo**.  
  
2.  En el [cuadro de diálogo Buscar símbolo](http://msdn.microsoft.com/es-es/63e93d9c-784f-418d-a76a-723da5ff5d96), vaya al cuadro **Buscar** y seleccione una cadena de búsqueda anterior en la lista desplegable, o escriba la tecla de aceleración que desea buscar \(por ejemplo, ID\_ACCEL1\).  
  
    > [!TIP]
    >  Si desea usar [expresiones regulares](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md) en la búsqueda, use el [comando Buscar en archivos](../Topic/Find%20Command.md) del menú **Edición**, en lugar del comando **Buscar símbolo**.  Para habilitar las expresiones regulares, active la casilla **Usar expresiones regulares** en el [cuadro de diálogo Buscar](http://msdn.microsoft.com/es-es/dad03582-4931-4893-83ba-84b37f5b1600).  A continuación, haga clic en el botón de flecha derecha situado a la derecha del cuadro **Buscar**, para mostrar una lista de expresiones regulares de búsqueda.  Cuando seleccione una expresión de esta lista, se usará como texto de búsqueda en el cuadro **Buscar**.  
  
3.  Seleccione cualquiera de las opciones de **Buscar**.  
  
4.  Haga clic en **Buscar siguiente**.  
  
    > [!NOTE]
    >  No se pueden buscar símbolos en los recursos binarios, de acelerador o de cadena.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, consulte [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)