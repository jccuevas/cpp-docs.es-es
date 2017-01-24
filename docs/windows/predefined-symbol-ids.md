---
title: "Predefined Symbol IDs | Microsoft Docs"
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
  - "symbols, predefined IDs"
  - "predefined symbol IDs"
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Predefined Symbol IDs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se inicia un proyecto nuevo, dependiendo del tipo de proyecto, es posible que se hayan predefinido algunos identificadores de símbolo.  Estos identificadores son compatibles con los distintos tipos de proyectos y bibliotecas \(por ejemplo, MFC\).  Representan tareas comunes que se suelen incluir en todas las aplicaciones, o acciones de elementos de hardware, como un mouse o una impresora.  
  
 Estos identificadores de símbolo son importantes al trabajar con recursos.  Se encuentran disponibles al editar tablas de aceleradores y algunos de ellos ya están asociados con teclas virtuales.  También puede encontrarlos en la [ventana Propiedades](../Topic/Properties%20Window.md).  Puede asignar cualquiera de los identificadores de símbolo predefinidos a los nuevos recursos, o también puede asignar a estos identificadores teclas de aceleración. En este caso, la funcionalidad asociada con el identificador de símbolo se asociará a su vez de forma automática con la combinación de teclas en cuestión.  
  
 Estas bibliotecas cuentan con símbolos predefinidos que aparecerán como parte del proyecto:  
  
-   [Símbolos predefinidos de MFC](../windows/mfc-predefined-symbols.md)  
  
-   [Símbolos predefinidos de ATL](../windows/atl-predefined-symbols.md)  
  
-   [Símbolos predefinidos de Win32](../windows/win32-predefined-symbols.md)  
  
    > [!NOTE]
    >  Los símbolos predefinidos son siempre de solo lectura.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, consulte [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32, MFC o ATL  
  
## Vea también  
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)