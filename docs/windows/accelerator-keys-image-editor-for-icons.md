---
title: Teclas de aceleración (Editor de C++ imágenes para iconos)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 45afdf4b3b557b560d7597b1bb4330c36a1fc84d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204815"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Teclas de aceleración (Editor de C++ imágenes para iconos)

A continuación se muestran las teclas de aceleración de los comandos del editor de imágenes que están enlazados a las claves de forma predeterminada. Para cambiar las teclas de aceleración, vaya al menú **herramientas** > **opciones** y elija **teclado** bajo el **entorno** carpeta. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, vaya al menú **herramientas** > **importar y exportar configuraciones**. Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Comando|Teclas|Descripción|
|-------------|----------|-----------------|
|Image.AirBrushTool|**Ctrl** + **A**|Dibuja con un aerógrafo con el tamaño y color seleccionados.|
|Image.BrushTool|**Ctrl** + **B**|Dibuja con un pincel con la forma seleccionada, tamaño y color.|
|Image.CopyAndOutlineSelection|**CTRL** + **MAYÚS** + **U**|Crea una copia de la selección actual y la resalta. Si la selección actual contiene el color de fondo, se excluirá si tienes [transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) seleccionado.|
|Image.DrawOpaque|**Ctrl** + **J**|Convierte la selección actual o bien [opaca o transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**Ctrl** + **P**|Dibuja una elipse con el ancho de línea seleccionado y el color.|
|Image.EraserTool|**Ctrl** + **Mayús** + **I**|Borra una parte de la imagen (con el color de fondo actual).|
|Image.FilledEllipseTool|**CTRL** + **MAYÚS** + **Alt** + **P**|Dibuja una elipse rellena.|
|Image.FilledRectangleTool|**CTRL** + **MAYÚS** + **Alt** + **R**|Dibuja un rectángulo relleno.|
|Image.FilledRoundRectangleTool|**CTRL** + **MAYÚS** + **Alt** + **W**|Dibuja un rectángulo redondeado relleno.|
|Image.FillTool|**Ctrl** + **F**|Rellena un área.|
|Image.FlipHorizontal|**Ctrl** + **H**|Voltea la imagen o la selección en sentido horizontal.|
|Image.FlipVertical|**MAYÚS**+ **Alt** + **H**|Voltea la imagen o la selección en sentido vertical.|
|Image.LargerBrush|**Ctrl** + **=**|Aumenta el tamaño del pincel en un píxel en cada dirección. Para disminuir el tamaño del pincel, vea Image.SmallerBrush en esta tabla.|
|Image.LineTool|**Ctrl** + **L**|Dibuja una línea recta con el tamaño, la forma y el color seleccionados.|
|Image.MagnificationTool|**CTRL** + **M**|Activa el **Magnify** herramienta, que permite ampliar secciones específicas de la imagen.|
|Image.Magnify|**Ctrl** + **Mayús** + **M**|Alterna entre el aumento actual y un aumento de 1:1.|
|Image.NewImageType|**Insertar**|Inicia el [New \<dispositivo > cuadro de diálogo de tipo de imagen](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) con que se puede crear una imagen para un tipo de imagen diferente.|
|Image.NextColor|**Ctrl** + **]**<br /><br /> o bien<br /><br /> **CTRL** + **flecha derecha**|Cambia el color de primer plano de dibujo al siguiente color de la paleta.|
|Image.NextRightColor|**Ctrl** + **Mayús** + **]**<br /><br /> o bien<br /><br /> **MAYÚS** + **Ctrl** + **flecha derecha**|Cambia el color de fondo por el siguiente color de la paleta.|
|Image.OutlinedEllipseTool|**MAYÚS** + **Alt** + **P**|Dibuja una elipse rellena con un contorno.|
|Image.OutlinedRoundRectangleTool|**MAYÚS** + **Alt** + **R**|Dibuja un rectángulo relleno con contorno.|
|Image.OutlinedRoundRectangleTool|**MAYÚS** + **Alt** + **W**|Dibuja un rectángulo redondeado relleno con un contorno.|
|Image.PencilTool|**Ctrl** + **I**|Dibuja con un lápiz de un solo píxel.|
|Image.PreviousColor|**Ctrl** + **[**<br /><br /> o bien<br /><br /> **CTRL** + **flecha izquierda**|Cambia el color de primer plano de dibujo al color de la paleta anterior.|
|Image.PreviousRightColor|**Ctrl** + **Mayús** + **[**<br /><br /> o bien<br /><br /> **MAYÚS** + **Ctrl** + **flecha izquierda**|Cambia el color de fondo de dibujo al color de la paleta anterior.|
|Image.RectangleSelectionTool|**MAYÚS** + **Alt** + **S**|Selecciona una parte rectangular de la imagen para mover, copiar o modificar.|
|Image.RectangleTool|ATL + R|Dibuja un rectángulo con el ancho de línea seleccionado y el color.|
|Image.Rotate90Degrees|**Ctrl** + **Mayús** + **H**|Gira la imagen o la selección 90 grados.|
|Image.RoundedRectangleTool|**ALT** + **W**|Dibuja un rectángulo redondeado con el ancho de línea seleccionado y el color.|
|Image.ShowGrid|**Ctrl** + **Alt** + **S**|Muestra u oculta la cuadrícula de píxeles (activa o desactiva el **cuadrícula de píxeles** opción el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.ShowTileGrid|**CTRL** + **MAYÚS** + **Alt** + **S**|Muestra u oculta la cuadrícula de mosaico (activa o desactiva el **cuadrícula de mosaico** opción el [cuadro de diálogo de configuración de la cuadrícula](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.SmallBrush|**Ctrl** + **.** (punto)|Reduce la **pincel** tamaño a un píxel. Vea también Image.LargerBrush e Image.SmallerBrush en esta tabla.|
|Image.SmallBrush|**CTRL**  +  **-** (signo menos)|Reduce el tamaño del pincel en un píxel en cada dirección. Para volver a expandir el tamaño del pincel, vea Image.LargerBrush en esta tabla.|
|Image.TextTool|**Ctrl** + **T**|Se abre el [cuadro de diálogo Herramienta de texto](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**Ctrl** + **U**|Dibuja utilizando como pincel la selección actual.|
|Image.ZoomIn|**CTRL** + **MAYÚS** + **.** (punto)<br /><br /> o bien<br /><br /> **CTRL** + **flecha arriba**|Aumenta la ampliación de la vista actual.|
|Image.ZoomOut|**CTRL** + **,** (coma)<br /><br /> o bien<br /><br /> **CTRL** + **flecha abajo**|Reduce la ampliación de la vista actual.|

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: Creación de un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Cómo: Edición de una imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Cómo: Uso de una herramienta de dibujo](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Cómo: Trabajo con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>