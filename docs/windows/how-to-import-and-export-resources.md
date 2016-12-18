---
title: "How to: Import and Export Resources | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.resvw.resource.importing"
  - "vc.resvw.resource.importing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], exporting"
  - "graphics [C++], exporting"
  - "graphics [C++], importing"
  - "resources [Visual Studio], importing"
  - "bitmaps [C++], importing and exporting"
  - "toolbars [C++], importing"
  - "images [C++], importing"
  - "toolbars [C++], exporting"
  - "cursors [C++], importing and exporting"
  - "images [C++], exporting"
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Import and Export Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede importar recursos gráficos \(mapas de bits, iconos, cursores y barras de herramientas\), archivos HTML y recursos personalizados para usarlos en Visual C\+\+.  Puede exportar los mismos tipos de archivos desde un proyecto de Visual C\+\+ para separar archivos que se pueden usar fuera del entorno de desarrollo.  
  
> [!NOTE]
>  Los tipos de recursos como los aceleradores, los cuadros de diálogo y las tablas de cadenas no se pueden importar o exportar, porque no son tipos de archivos independientes.  
  
### Para importar un recurso individual al archivo de recursos actual  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), haga clic con el botón derecho en el nodo del archivo de script de recursos \(\*.rc\) al que quiera agregar un recurso.  
  
2.  Haga clic en **Importar** en el menú contextual.  
  
3.  Busque y seleccione el nombre de archivo del mapa de bits \(.bmp\), icono \(.ico\), cursor \(.cur\), archivo Html \(.htm\) o cualquier otro archivo que quiera importar.  
  
4.  Haga clic en **Aceptar** para agregar el recurso al archivo seleccionado en la **Vista de recursos**.  
  
    > [!NOTE]
    >  El proceso de importación es el mismo, independientemente del tipo de recurso seleccionado.  El recurso importado se agrega automáticamente al nodo correspondiente a ese tipo de recurso.  
  
### Para exportar un mapa de bits, un icono o un cursor como un archivo independiente \(para usarlo fuera de Visual C\+\+\)  
  
1.  En la **Vista de recursos**, haga clic con el botón derecho en el recurso que quiera exportar.  
  
2.  Haga clic en **Exportar** en el menú contextual.  
  
3.  En el cuadro de diálogo **Exportar recurso**, acepte el nombre de archivo actual o escriba uno nuevo.  
  
4.  Vaya a la carpeta donde quiera guardar el archivo y haga clic en **Exportar**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Vea el [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md) para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo tener acceso a los recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades.  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)