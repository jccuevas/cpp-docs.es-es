---
title: "Opening a Resource for Binary Editing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.binary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary data, editing"
  - "resources [Visual Studio], opening for binary editing"
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Opening a Resource for Binary Editing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para abrir un recurso de escritorio de Windows para editarlo en modo binario  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), seleccione el archivo de recursos específico que quiera editar.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Haga clic con el botón secundario en el recurso y haga clic en **Abrir datos binarios** en el menú contextual.  
  
    > [!NOTE]
    >  Si usa la ventana [Vista de recursos](../windows/resource-view-window.md) para abrir un recurso con un formato que Visual Studio no reconozca \(como RCDATA o un recurso personalizado\), el recurso se abrirá automáticamente en el editor binario.  
  
### Para abrir un recurso para editarlo para la edición binaria  
  
1.  En el Explorador de soluciones, seleccione el archivo de recursos específico que quiera editar.  
  
2.  Haga clic con el botón secundario en el recurso y elija **Abrir con** en el menú contextual.  
  
3.  En el cuadro de diálogo **Abrir con**, seleccione **Editor binario**.  
  
    > [!NOTE]
    >  Se puede usar el [Editor de imágenes](../mfc/image-editor-for-icons.md) y el [Editor binario](../mfc/binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
    > [!NOTE]
    >  Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 ![Editor binario](../mfc/media/vcbinaryeditor2.png "vcBinaryEditor2")  
Datos binarios de un cuadro de diálogo que aparece en el editor binario  
  
 Solo determinados valores ASCII se representan en el editor binario \(de 0x20 a 0x7E\). Los caracteres extendidos se muestran como puntos en la sección de valor ASCII del editor binario \(el panel derecho\). Los caracteres "imprimibles" son valores ASCII de 32 a 126.  
  
> [!NOTE]
>  Si quiere usar el editor binario en un recurso que ya se está editando en otra ventana del editor, cierre primero la otra ventana del editor.  
  
 **Requisitos**  
  
 Ninguno  
  
## Vea también  
 [Binary Editor](../mfc/binary-editor.md)