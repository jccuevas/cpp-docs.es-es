---
title: Teclas de aceleraciónC++ (editor de imágenes para iconos)
ms.date: 02/15/2019
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 867c7d2c217b5efb832654a7863e834a4351c126
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167581"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Teclas de aceleraciónC++ (editor de imágenes para iconos)

A continuación se muestran las teclas de aceleración de los comandos del editor de imágenes que están enlazadas a claves de forma predeterminada. Para cambiar las teclas de aceleración, vaya a **herramientas** de menú > **Opciones** y elija **teclado** en la carpeta **entorno** . Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, vaya a **herramientas** de menú > **importar y exportar configuraciones**. Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Get-Help|Claves|Descripción|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl** + **A**|Dibuja con un aerógrafo con el tamaño y el color seleccionados.|
|Image.BrushTool|**Ctrl** + **B**|Dibuja con un pincel con la forma, el tamaño y el color seleccionados.|
|Image.CopyAndOutlineSelection|**Ctrl** + **MAYÚS** + **U**|Crea una copia de la selección actual y la resalta. Si el color de fondo está contenido en la selección actual, se excluirá si se selecciona [transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) .|
|Image.DrawOpaque|**Ctrl** + **J**|Hace que la selección actual sea [opaca o transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**Ctrl** + **P**|Dibuja una elipse con el ancho de línea y el color seleccionados.|
|Image.EraserTool|**Ctrl** + **Mayús** + **I**|Borra una parte de la imagen (con el color de fondo actual).|
|Image.FilledEllipseTool|**Ctrl** + **mayús** + **Alt** + **P**|Dibuja una elipse rellena.|
|Image.FilledRectangleTool|**Ctrl** + **mayús** + **Alt** + **R**|Dibuja un rectángulo relleno.|
|Image.FilledRoundRectangleTool|**Ctrl** + **mayús** + **Alt** + **W**|Dibuja un rectángulo redondeado relleno.|
|Image.FillTool|**Ctrl** + **F**|Rellena un área.|
|Image.FlipHorizontal|**Ctrl** + **H**|Voltea la imagen o la selección en sentido horizontal.|
|Image.FlipVertical|**Mayús**+ **Alt** + **H**|Voltea la imagen o la selección en sentido vertical.|
|Image.LargerBrush|**Ctrl** +  **=**|Aumenta el tamaño del pincel en un píxel en cada dirección. Para disminuir el tamaño del pincel, vea Image.SmallerBrush en esta tabla.|
|Image.LineTool|**Ctrl** + **L**|Dibuja una línea recta con el tamaño, la forma y el color seleccionados.|
|Image.MagnificationTool|**Ctrl** + **M**|Activa la herramienta **lupa** , que permite ampliar secciones específicas de la imagen.|
|Image.Magnify|**Ctrl** + **Mayús** + **M**|Alterna entre el aumento actual y un aumento de 1:1.|
|Image.NewImageType|**Insertar**|Inicia el [cuadro de diálogo nuevo \<dispositivo > tipo de imagen](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) con el que puede crear una imagen para un tipo de imagen diferente.|
|Image.NextColor|**Ctrl** +  **]**<br /><br /> O bien<br /><br /> **Ctrl** + **flecha derecha**|Cambia el color de primer plano de dibujo al siguiente color de la paleta.|
|Image.NextRightColor|**Ctrl** + **Mayús** +  **]**<br /><br /> O bien<br /><br /> **Mayús** + **Ctrl** + **flecha derecha**|Cambia el color de fondo por el siguiente color de la paleta.|
|Image.OutlinedEllipseTool|**Mayús** + **Alt** + **P**|Dibuja una elipse rellena con un contorno.|
|Image.OutlinedRoundRectangleTool|**Shift** + **Alt** + **R**|Dibuja un rectángulo relleno con contorno.|
|Image.OutlinedRoundRectangleTool|**Mayús** + **Alt** + **W**|Dibuja un rectángulo redondeado relleno con un contorno.|
|Image.PencilTool|**Ctrl** + **I**|Dibuja con un lápiz de un solo píxel.|
|Image.PreviousColor|**Ctrl** +  **[**<br /><br /> O bien<br /><br /> **Ctrl** + **flecha izquierda**|Cambia el color de primer plano de dibujo al color de la paleta anterior.|
|Image.PreviousRightColor|**Ctrl** + **Mayús** +  **[**<br /><br /> O bien<br /><br /> **Mayús** + **Ctrl** + **flecha izquierda**|Cambia el color de fondo de dibujo al color de la paleta anterior.|
|Image.RectangleSelectionTool|**Shift** + **Alt** + **S**|Selecciona una parte rectangular de la imagen para moverla, copiarla o editarla.|
|Image.RectangleTool|ATL + R|Dibuja un rectángulo con el ancho de línea y el color seleccionados.|
|Image.Rotate90Degrees|**Ctrl** + **Mayús** + **H**|Gira la imagen o la selección 90 grados.|
|Image.RoundedRectangleTool|**Alt** + **W**|Dibuja un rectángulo redondeado con el ancho de línea y el color seleccionados.|
|Image.ShowGrid|**Ctrl** + **Alt** + **S**|Alterna la cuadrícula de píxeles (activa o desactiva la opción **cuadrícula de píxeles** en el [cuadro de diálogo Configuración](../windows/grid-settings-dialog-box-image-editor-for-icons.md)de la cuadrícula).|
|Image.ShowTileGrid|**Ctrl** + **mayús** + **Alt** + **S**|Alterna la cuadrícula de mosaico (activa o desactiva la opción **cuadrícula de mosaico** en el [cuadro de diálogo Configuración](../windows/grid-settings-dialog-box-image-editor-for-icons.md)de la cuadrícula).|
|Image.SmallBrush|**Ctrl** +  **.** (punto)|Reduce el tamaño del **pincel** a un píxel. Vea también Image.LargerBrush e Image.SmallerBrush en esta tabla.|
|Image.SmallBrush|**Ctrl** +  **-** (menos)|Reduce el tamaño del pincel en un píxel en cada dirección. Para volver a expandir el tamaño del pincel, vea Image.LargerBrush en esta tabla.|
|Image.TextTool|**Ctrl** + **T**|Abre el [cuadro de diálogo herramienta de texto](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**Ctrl** + **U**|Dibuja utilizando como pincel la selección actual.|
|Image.ZoomIn|**Ctrl** + **MAYÚS** +  **.** (punto)<br /><br /> O bien<br /><br /> **Ctrl** + **flecha arriba**|Aumenta la ampliación de la vista actual.|
|Image.ZoomOut|**Ctrl** +  **,** (coma)<br /><br /> O bien<br /><br /> **Ctrl** + **flecha abajo**|Reduce la ampliación de la vista actual.|

## <a name="requirements"></a>Requisitos

None

## <a name="see-also"></a>Consulte también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: crear un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Cómo: editar una imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Cómo: usar una herramienta de dibujo](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Cómo: trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
