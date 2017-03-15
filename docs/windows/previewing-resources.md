---
title: "Previewing Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.resource.previewing"
  - "vs.resvw.resource.previewing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "resource previews"
  - "code, viewing"
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Previewing Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La vista previa de los recursos permite ver recursos gráficos sin tener que abrirlos.  Como los identificadores de recursos cambian a números, la vista previa también resulta muy útil para archivos ejecutables ya compilados.  Estos identificadores numéricos no suelen suministrar suficiente información, por lo que la vista previa de los recursos ayuda a identificarlos con rapidez.  
  
 Es posible obtener una vista previa del diseño visual de los siguientes tipos de recursos:  
  
-   Mapa de bits  
  
-   Cuadro de diálogo  
  
-   Icono  
  
-   Menu  
  
-   Cursor  
  
-   Barra de herramientas  
  
 La función de vista previa no es aplicable a los recursos de aceleradores, del manifiesto, de tabla de cadenas y de información de versión.  
  
### Para obtener una vista previa de recursos  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md) o en una ventana de documento, seleccione el recurso en cuestión \(por ejemplo, IDD\_ABOUTBOX\).  
  
     **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En la [ventana Propiedades](../Topic/Properties%20Window.md), haga clic en el botón **Páginas de propiedades**.  
  
     \-O bien\-  
  
3.  En el menú **Ver**, haga clic en **Páginas de propiedades**.  
  
     Se abrirá entonces la página de propiedades del recurso mostrando una vista previa de él.  Utilice las teclas de dirección  arriba y abajo para navegar por el control de árbol de la vista de recursos o de la ventana de documento.  La Página de propiedades permanecerá abierta y mostrará todos los recursos que tengan el foco y puedan mostrarse en vista preliminar.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [How to: Open a Resource Script File Outside of a Project \(Standalone\)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Resource Editors](../mfc/resource-editors.md)