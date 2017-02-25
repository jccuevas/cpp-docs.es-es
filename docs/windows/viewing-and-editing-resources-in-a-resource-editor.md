---
title: "Viewing and Editing Resources in a Resource Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.resourceview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "rc files, viewing resources"
  - "Resource View pane"
  - "layouts, previewing resource"
  - "code, viewing resources"
  - "resource editors, viewing resources"
  - ".rc files, viewing resources"
  - "resources [Visual Studio], editing"
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Viewing and Editing Resources in a Resource Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada tipo de recurso tiene asociado un editor de recursos específico.  Por medio del editor asociado, puede reorganizar, cambiar el tamaño, agregar controles y características o modificar otros aspectos de un recurso.  También puede editar recursos en [formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md) y [formato binario](../mfc/opening-a-resource-for-binary-editing.md).  
  
 Algunos tipos de recursos son archivos individuales que pueden importarse y utilizarse de varias maneras, como mapas de bits, iconos, cursores, barras de herramientas, archivos html, etc.  Estos recursos tienen nombres de archivo e [identificaciones de recursos](../mfc/symbols-resource-identifiers.md).  Otros, como los cuadros de diálogo, los menús y las tablas de cadenas de proyectos de Win32, sólo existen como parte de archivos de script de recursos \(.rc\) o de plantillas de recursos \(.rct\).  
  
> [!NOTE]
>  Las propiedades de un recurso [se pueden modificar utilizando la ventana Propiedades](../windows/changing-the-properties-of-a-resource.md).  
  
## Recursos de Win32  
 Puede tener acceso a los recursos de Win32 en el panel [Vista de recursos](../windows/resource-view-window.md).  
  
#### Para ver un recurso de Win32 en un editor de recursos  
  
1.  Seleccione **Vista de recursos** en el menú **Ver**.  
  
2.  Si la ventana Vista de recursos no es la de nivel superior, puede ponerla encima de las demás haciendo clic en la ficha **Vista de recursos**.  
  
3.  En el panel **Vista de recursos**, expanda la carpeta del proyecto que contenga los recursos que desee ver.  Por ejemplo, si desea ver un recurso de cuadro de diálogo, expanda la carpeta Cuadro de diálogo.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
4.  Haga doble clic en el recurso en cuestión \(por ejemplo, IDD\_ABOUTBOX\).  
  
     El recurso se abrirá en el editor correspondiente.  Por ejemplo, los recursos de cuadro de diálogo se abrirán en el Editor de cuadros de diálogo.  
  
     También puede [ver los recursos de un archivo .rc \(de script de recursos\) sin tener un proyecto abierto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
#### Para eliminar un recurso de Win32 existente  
  
1.  En la **Vista de recursos**, expanda el nodo de un tipo de recurso.  
  
2.  Haga clic con el botón secundario del mouse en el recurso que desee eliminar y elija **Eliminar** en el menú contextual.  
  
    > [!NOTE]
    >  Podrá utilizar este mismo comando del menú contextual para eliminar un recurso cuando tenga el archivo .rc abierto en una ventana de documento fuera de un proyecto.  
  
## Recursos de proyectos administrados  
 Dado que los proyectos administrados no utilizan los archivos de script de recursos, debe abrir los recursos en el **Explorador de soluciones**.  Puede utilizar el [Editor de imágenes](../mfc/image-editor-for-icons.md) y el [Editor binario](../mfc/binary-editor.md) para trabajar con archivos de recursos en proyectos administrados.  Todos los recursos administrados que vaya a editar deberán estar vinculados.  Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
#### Para ver un recurso administrado en un editor de recursos  
  
1.  En el Explorador de soluciones, haga doble clic en el recurso; por ejemplo, Bitmap1.bmp.  
  
     El recurso se abrirá en el editor correspondiente.  
  
#### Para eliminar un recurso administrado existente  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el recurso que desee eliminar y elija **Eliminar** en el menú contextual.  
  
### Requisitos  
 None  
  
## Vea también  
 [Resource Editors](../mfc/resource-editors.md)