---
title: "Accelerator Keys (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator keys"
  - "Image editor [C++], accelerator keys"
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Accelerator Keys (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A continuación se muestran las teclas de aceleración predeterminadas de los comandos del Editor de imágenes que están enlazadas con teclas de manera predeterminada.  Para cambiar las teclas de aceleración, haga clic en **Opciones** en el menú **Herramientas** y elija **Teclado** en la carpeta **Entorno**.  Para obtener más información, consulte [Identificar y personalizar métodos abreviados de teclado](../Topic/Identifying%20and%20Customizing%20Keyboard%20Shortcuts%20in%20Visual%20Studio.md).  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
|Command|Claves|Descripción|  
|-------------|------------|-----------------|  
|Image.AirBrushTool|CTRL \+ A|Dibuja, con un aerógrafo, en el tamaño y el color seleccionados.|  
|Image.BrushTool|CTRL \+ B|Dibuja, con un pincel, en el tamaño, la forma y el color seleccionados.|  
|Image.CopyAndOutlineSelection|CTRL \+ MAYÚS \+ U|Crea una copia de la selección actual y la resalta.  Si la selección actual contiene el color de fondo, se excluirá si ha seleccionado [transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|  
|Image.DrawOpaque|CTRL \+ J|Convierte la selección actual en [opaca o transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|  
|Image.EllipseTool|CTRL \+ P|Dibuja una elipse con el ancho de línea y el color seleccionados.|  
|Image.EraserTool|CTRL \+ MAYÚS \+ I|Borra una parte de la imagen \(con el color de fondo actual\).|  
|Image.FilledEllipseTool|CTRL \+ MAYÚS \+ ALT \+ P|Dibuja una elipse rellena.|  
|Image.FilledRectangleTool|CTRL \+ MAYÚS \+ ALT \+ R|Dibuja un rectángulo relleno.|  
|Image.FilledRoundRectangleTool|CTRL \+ MAYÚS \+ ALT \+ W|Dibuja un rectángulo redondeado relleno.|  
|Image.FillTool|CTRL \+ F|Rellena un área.|  
|Image.FlipHorizontal|CTRL \+ H|Voltea la imagen o la selección en sentido horizontal.|  
|Image.FlipVertical|MAYÚS \+ ALT \+ H|Voltea la imagen o la selección en sentido vertical.|  
|Image.LargerBrush|CTRL \+ \=|Aumenta el tamaño del pincel en un píxel en cada dirección.  Para disminuir el tamaño del pincel, vea Image.SmallerBrush en esta tabla.|  
|Image.LineTool|CTRL \+ L|Dibuja una línea recta con el tamaño, la forma y el color seleccionados.|  
|Image.MagnificationTool|CTRL \+ M|Activa la herramienta **Aumentar**, que permite ampliar secciones específicas de una imagen.|  
|Image.Magnify|CTRL \+ MAYÚS \+ M|Alterna entre el aumento actual y un aumento de 1:1.|  
|Image.NewImageType|INSERT|Inicia el [cuadro de diálogo Nueva imagen de \<dispositivo\>](../mfc/new-device-image-type-dialog-box-image-editor-for-icons.md), que permite crear una imagen para un tipo de imagen diferente.|  
|Image.NextColor|CTRL \+ \]<br /><br /> \-O bien\-<br /><br /> CTRL \+ FLECHA DERECHA|Cambia el color de primer plano de dibujo al siguiente color de la paleta.|  
|Image.NextRightColor|CTRL \+ MAYÚS \+ \]<br /><br /> \-O bien\-<br /><br /> MAYÚS \+ CTRL \+ FLECHA DERECHA|Cambia el color de fondo por el siguiente color de la paleta.|  
|Image.OutlinedEllipseTool|MAYÚS \+ ALT \+ P|Dibuja una elipse rellena con un contorno.|  
|Image.OutlinedRoundRectangleTool|MAYÚS \+ ATL \+ R|Dibuja un rectángulo relleno con contorno.|  
|Image.OutlinedRoundRectangleTool|MAYÚS \+ ALT \+ W|Dibuja un rectángulo redondeado relleno con un contorno.|  
|Image.PencilTool|CTRL \+ I|Dibuja con un lápiz de un solo píxel.|  
|Image.PreviousColor|CTRL \+ \[<br /><br /> \-O bien\-<br /><br /> CTRL \+ FLECHA IZQUIERDA|Cambia el color de primer plano de dibujo al color de la paleta anterior.|  
|Image.PreviousRightColor|CTRL \+ MAYÚS \+ \[<br /><br /> \-O bien\-<br /><br /> MAYÚS \+ CTRL \+ FLECHA IZQUIERDA|Cambia el color de fondo de dibujo al color de la paleta anterior.|  
|Image.RectangleSelectionTool|MAYÚS \+ ALT \+ S|Selecciona una parte rectangular de la imagen para moverla, copiarla o editarla.|  
|Image.RectangleTool|ATL \+ R|Dibuja un rectángulo con el ancho de línea y el color seleccionados.|  
|Image.Rotate90Degrees|CTRL \+ MAYÚS \+ H|Gira la imagen o la selección 90 grados.|  
|Image.RoundedRectangleTool|ALT \+ W|Dibuja un rectángulo redondeado con el ancho de línea y el color seleccionados.|  
|Image.ShowGrid|CTRL \+ ALT \+ S|Muestra u oculta la cuadrícula de píxeles \(activa o desactiva la opción **Cuadrícula de píxeles**en la [cuadro de diálogo Configuración de cuadrícula](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)\).|  
|Image.ShowTileGrid|CTRL \+ MAYÚS \+ ALT \+ S|Muestra u oculta la cuadrícula de mosaico \(activa o desactiva la opción **Cuadrícula de mosaico** en el [cuadro de diálogo Configuración de cuadrícula](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)\).|  
|Image.SmallBrush|CTRL \+ .  \(punto\)|Reduce el tamaño del pincel a un píxel.  Vea también Image.LargerBrush e Image.SmallerBrush en esta tabla.|  
|Image.SmallBrush|CTRL \+ \- \(menos\)|Reduce el tamaño del pincel en un píxel en cada dirección.  Para volver a ampliar el tamaño del pincel, vea Image.LargerBrush en esta tabla.|  
|Image.TextTool|CTRL \+ T|Abre el [cuadro de diálogo Herramienta de texto](../mfc/text-tool-dialog-box-image-editor-for-icons.md).|  
|Image.UseSelectionAsBrush|CTRL \+ U|Dibuja utilizando como pincel la selección actual.|  
|Image.ZoomIn|CTRL \+ MAYÚS \+ .  \(punto\)<br /><br /> \-O bien\-<br /><br /> CTRL \+ FLECHA ARRIBA|Aumenta la ampliación de la vista actual.|  
|Image.ZoomOut|CTRL \+ , \(coma\)<br /><br /> \-O bien\-<br /><br /> CTRL \+ FLECHA ABAJO|Reduce la ampliación de la vista actual.|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 None  
  
## Vea también  
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)