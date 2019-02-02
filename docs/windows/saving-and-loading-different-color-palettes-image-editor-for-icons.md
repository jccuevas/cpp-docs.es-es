---
title: Guardar y cargar diferentes paletas de colores (Editor de imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.color
- vc.editors.loadcolorpalette
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
ms.openlocfilehash: fd2664407d33d8e3ed594921501b7f80e6c8850b
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560275"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Guardar y cargar diferentes paletas de colores (Editor de imágenes para iconos)

Puede guardar y cargar un **colores** paleta que contiene [personalizar los colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (De forma predeterminada, el **colores** paleta usado más recientemente se carga automáticamente al iniciar Visual Studio.)

> [!TIP]
> Puesto que la **imagen** editor no tiene ningún medio para restaurar el valor predeterminado **colores** paleta, debe guardar el valor predeterminado **colores** paleta en un nombre, como  *estándar.PAL* o *predeterminada.PAL* por lo que puede restaurar fácilmente la configuración predeterminada.

Utilice la **Cargar paleta de colores** cuadro de diálogo para cargar las paletas de colores para usar en el proyecto de C++. Las siguientes propiedades que se incluyen son:

|Property|Descripción|
|---|---|
|**Buscar en**|Especifica la ubicación donde desea ubicar un archivo o carpeta. Seleccione la flecha para elegir otra ubicación, o seleccione el icono de carpeta en la barra de herramientas para mover los niveles.|
|**Nombre de archivo**|Proporciona un espacio para que escriba el nombre del archivo que desea abrir. Para buscar rápidamente un archivo que ha abierto anteriormente, seleccione el nombre de archivo en la lista desplegable, si está disponible.<br/><br/>Si está buscando un archivo, puede utilizar asteriscos (*) como caracteres comodín. Por ejemplo, puede escribir \*.\* para ver una lista de todos los archivos. También puede escribir la ruta de acceso completa de un archivo, por ejemplo, C:\My Documentos\MiPaletaDeColores. PAL o \\\NetworkServer\MyFolder\MyColorPalette.pal.|
|**Tipo de archivo**|Enumera los tipos de archivos que se va a mostrar. Paleta (*. PAL) es el tipo de archivo predeterminado para las paletas de colores.|

## <a name="to-save-a-custom-colors-palette"></a>Para guardar una paleta de colores personalizada

1. Desde el **imagen** menú, elija **Guardar paleta**.

1. Desplácese al directorio donde quiera guardar la paleta y escriba un nombre para la misma.

1. Seleccione **Guardar**.

## <a name="to-load-a-custom-colors-palette"></a>Para cargar una paleta de colores personalizada

1. Desde el **imagen** menú, elija **Cargar paleta**.

1. En el **Cargar paleta de colores** diálogo cuadro, vaya al directorio correcto y seleccione la paleta que desea cargar. **Color** paletas se guardan con una extensión de archivo. PAL.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)