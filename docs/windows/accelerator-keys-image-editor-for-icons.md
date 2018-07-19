---
title: Teclas de aceleración (Editor de imágenes para iconos) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2b19fb16410f7d720d11e8b8560cde4cadf10b1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861537"
---
# <a name="accelerator-keys-image-editor-for-icons"></a>Teclas de aceleración (Editor de imágenes para iconos)
A continuación se muestran las teclas de aceleración de los comandos del editor de imágenes que están enlazados a las claves de forma predeterminada. Para cambiar las teclas de aceleración, haga clic en **opciones** en el **herramientas** menú y, a continuación, elija **teclado** en el **entorno** carpeta. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
|Comando|Teclas|Descripción|  
|-------------|----------|-----------------|  
|Image.AirBrushTool|CTRL + A|Dibuja utilizando un aerógrafo con el tamaño y color seleccionados.|  
|Image.BrushTool|CTRL + B|Dibuja utilizando un pincel con la forma seleccionada, tamaño y color.|  
|Image.CopyAndOutlineSelection|CTRL + MAYÚS + U|Crea una copia de la selección actual y la resalta. Si el color de fondo está incluido en la selección actual, se excluirá si tienes [transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) seleccionado.|  
|Image.DrawOpaque|CTRL + J|Convierte la selección actual o [opaco o transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|  
|Image.EllipseTool|CTRL + P|Dibuja una elipse con el ancho de línea seleccionado y el color.|  
|Image.EraserTool|CTRL + MAYÚS + I|Borra una parte de la imagen (con el color de fondo actual).|  
|Image.FilledEllipseTool|CTRL + MAYÚS + ALT + P|Dibuja una elipse rellena.|  
|Image.FilledRectangleTool|CTRL + MAYÚS + ALT + R|Dibuja un rectángulo relleno.|  
|Image.FilledRoundRectangleTool|CTRL + MAYÚS + ALT + W|Dibuja un rectángulo redondeado relleno.|  
|Image.FillTool|CTRL + F|Rellena un área.|  
|Image.FlipHorizontal|CTRL + H|Voltea la imagen o la selección en sentido horizontal.|  
|Image.FlipVertical|MAYÚS + ALT + H|Voltea la imagen o la selección en sentido vertical.|  
|Image.LargerBrush|CTRL + =|Aumenta el tamaño del pincel en un píxel en cada dirección. Para disminuir el tamaño del pincel, vea Image.SmallerBrush en esta tabla.|  
|Image.LineTool|CTRL + L|Dibuja una línea recta con el tamaño, la forma y el color seleccionados.|  
|Image.MagnificationTool|CTRL + M|Activa el **Magnify** herramienta, que permite ampliar secciones específicas de la imagen.|  
|Image.Magnify|CTRL + MAYÚS + M|Alterna entre el aumento actual y un aumento de 1:1.|  
|Image.NewImageType|INSERT|Inicia la [New \<dispositivo > cuadro de diálogo tipo de imagen](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) con que se puede crear una imagen para un tipo de imagen diferente.|  
|Image.NextColor|CTRL +]<br /><br /> O bien<br /><br /> CTRL + FLECHA DERECHA|Cambia el color de primer plano de dibujo al siguiente color de la paleta.|  
|Image.NextRightColor|CTRL + MAYÚS +]<br /><br /> O bien<br /><br /> MAYÚS + CTRL + FLECHA DERECHA|Cambia el color de fondo por el siguiente color de la paleta.|  
|Image.OutlinedEllipseTool|MAYÚS + ALT + P|Dibuja una elipse rellena con un contorno.|  
|Image.OutlinedRoundRectangleTool|MAYÚS + ALT + R|Dibuja un rectángulo relleno con contorno.|  
|Image.OutlinedRoundRectangleTool|MAYÚS + ALT + W|Dibuja un rectángulo redondeado relleno con un contorno.|  
|Image.PencilTool|CTRL + I|Dibuja con un lápiz de un solo píxel.|  
|Image.PreviousColor|CTRL + [<br /><br /> O bien<br /><br /> CTRL + FLECHA IZQUIERDA|Cambia el color de primer plano de dibujo al color de la paleta anterior.|  
|Image.PreviousRightColor|CTRL + MAYÚS + [<br /><br /> O bien<br /><br /> MAYÚS + CTRL + FLECHA IZQUIERDA|Cambia el color de fondo de dibujo al color de la paleta anterior.|  
|Image.RectangleSelectionTool|MAYÚS + ALT + S|Selecciona una parte rectangular de la imagen para mover, copiar o editar.|  
|Image.RectangleTool|ATL + R|Dibuja un rectángulo con el ancho de línea seleccionado y el color.|  
|Image.Rotate90Degrees|CTRL + MAYÚS + H|Gira la imagen o la selección 90 grados.|  
|Image.RoundedRectangleTool|ALT + W|Dibuja un rectángulo redondeado con el ancho de línea seleccionado y el color.|  
|Image.ShowGrid|CTRL + ALT + S|Muestra u oculta la cuadrícula de píxeles (activa o desactiva el **cuadrícula de píxeles** opción en el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|  
|Image.ShowTileGrid|CTRL + MAYÚS + ALT + S|Muestra u oculta la cuadrícula de mosaico (activa o desactiva el **icono cuadrícula** opción en el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|  
|Image.SmallBrush|CTRL +. (punto)|Reduce la **pincel** tamaño a un píxel. Vea también Image.LargerBrush e Image.SmallerBrush en esta tabla.|  
|Image.SmallBrush|CTRL + - (signo menos)|Reduce el tamaño del pincel en un píxel en cada dirección. Para volver a ampliar el tamaño del pincel, vea Image.LargerBrush en esta tabla.|  
|Image.TextTool|CTRL + T|Se abre la [cuadro de diálogo Herramienta de texto](../windows/text-tool-dialog-box-image-editor-for-icons.md).|  
|Image.UseSelectionAsBrush|CTRL + U|Dibuja utilizando como pincel la selección actual.|  
|Image.ZoomIn|CTRL + MAYÚS +. (punto)<br /><br /> O bien<br /><br /> CTRL + FLECHA ARRIBA|Aumenta la ampliación de la vista actual.|  
|Image.ZoomOut|CTRL +, (coma)<br /><br /> O bien<br /><br /> CTRL + FLECHA ABAJO|Reduce la ampliación de la vista actual.|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Editor de imágenes para iconos](../windows/image-editor-for-icons.md)

