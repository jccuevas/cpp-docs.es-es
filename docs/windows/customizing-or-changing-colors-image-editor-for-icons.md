---
title: Personalizar o cambiar colores (Editor de imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.customcolorselector
helpviewer_keywords:
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
ms.assetid: e58f6b32-f435-4d9a-a570-7569433661ae
ms.openlocfilehash: 7ab353ad0aa22c74eeba58e9310d9bc0f8d5a832
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560288"
---
# <a name="customizing-or-changing-colors-image-editor-for-icons"></a>Personalizar o cambiar colores (Editor de imágenes para iconos)

El **imagen** del editor [paleta de colores](../windows/colors-window-image-editor-for-icons.md) muestra inicialmente los 16 colores estándar. Con los colores mostrados, también puede crear sus propios colores personalizados. A continuación, puede [guardar y cargar una paleta de colores personalizada](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md).

El **Selector de colores personalizados** cuadro de diálogo le permite personalizar los colores utilizados para la imagen. Las siguientes propiedades que se incluyen son:

|Property|Descripción|
|---|---|
|**Presentación de Color degradado**|Cambia los valores de un color seleccionado. Coloque la cruz en el color que desee cambiar. A continuación, mueva el control deslizante hacia arriba o hacia abajo para cambiar la luminosidad o los valores RGB del color.|
|**Barra Luminosidad**|Establece la luminosidad del color seleccionado en el **muestra de Color degradado** cuadro. Seleccione y arrastre la flecha blanca de la barra para aumentar el brillo o hacia abajo para menor. El **Color** cuadro muestra el color que ha seleccionado y el efecto de la luminosidad establece.|
|**Color**|Muestra el matiz (valor de la rueda de colores) del color que se va a definir. El intervalo de valores está comprendido entre 0 y 240, donde 0 es rojo, 60 es amarillo, 120 es verde, 180 es aguamarina, 200 es magenta y 240 es azul.|
|**HUE**|Muestra el matiz (valor de la rueda de colores) del color que se va a definir. El intervalo de valores está comprendido entre 0 y 240, donde 0 es rojo, 60 es amarillo, 120 es verde, 180 es aguamarina, 200 es magenta y 240 es azul.|
|**Sáb**|Especifica el valor de saturación del color que se va a definir. La saturación es la cantidad de color en un matiz especificado. Los valores comprendidos entre 0 y 240.|
|**Lum.**|Enumera la luminosidad (brillo) del color que se va a definir. Los valores comprendidos entre 0 y 240.|
|**Red**|Especifica el valor de color rojo del color que se va a definir. El intervalo de valores está comprendido entre 0 y 255.|
|**Green**|Especifica el valor de color verde del color que se va a definir. El intervalo de valores está comprendido entre 0 y 255.|
|**Blue**|Especifica el valor azul del color que se va a definir. El intervalo de valores está comprendido entre 0 y 255.|

## <a name="to-change-colors-on-the-colors-palette"></a>Para cambiar los colores de la paleta de colores

1. Desde el **imagen** menú, elija **Ajustar colores**.

1. En el **Selector de colores personalizados** diálogo cuadro, defina el color escribiendo los valores RGB o HSL en los cuadros de texto correspondientes o elija un color en el **muestra de Color degradado** cuadro.

1. Establezca la luminosidad moviendo el control deslizante el **luminosidad** barra.

1. Muchos colores personalizados están interpolados. Si desea que el color sólido más próximo al color interpolado, haga doble clic en el **Color** cuadro.

   Si más adelante decide que desea el color interpolado, mueva el control deslizante el **luminosidad** barra o mueva la cruz el **muestra de Color degradado** cuadro de nuevo para restaurar la interpolación.

1. Seleccione **Aceptar** para agregar el nuevo color.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Imagen (menú)](../windows/image-menu-image-editor-for-icons.md)<br/>
[Ventana colores](../windows/colors-window-image-editor-for-icons.md)