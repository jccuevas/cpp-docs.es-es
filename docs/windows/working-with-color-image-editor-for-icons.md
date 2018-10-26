---
title: Trabajar con colores (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c829d086198233f0149782f1cb4cb1780aec7ad
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054183"
---
# <a name="working-with-color-image-editor-for-icons"></a>Trabajar con colores (Editor de imágenes para iconos)

El **Editor de imágenes** contiene muchas características que controlan específicamente y personalización los colores. Puede establecer el color de primer plano o en segundo plano, rellenar áreas delimitadas con color o seleccione un color en una imagen que se usará como el color de primer plano o actual. Puede usar herramientas en el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) junto con la paleta de colores en el [ventana colores](../windows/colors-window-image-editor-for-icons.md) para crear imágenes.

Se muestran todos los colores para monocromo e imágenes de 16 colores en el **colores** paleta en la **colores** ventana. Además de los 16 colores estándares, puede crear sus propios colores personalizados. Si se cambia cualquiera de los colores de la paleta cambiará inmediatamente el color correspondiente en la imagen.

Cuando se trabaja con el icono de 256 colores e imágenes de cursor, la **colores** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window) se utiliza. Para obtener más información, consulte [crear un icono de 256 colores o cursor](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).

> [!NOTE]
> Mediante el **Editor de imágenes**, puede ver las imágenes de 32 bits, pero no puede modificarlas.

También se pueden crear imágenes de color verdadero. Sin embargo, las muestras de color verdadero no aparecen en la paleta completa de la **colores** ventana; aparecen sólo en el área de indicador de color de primer plano o en segundo plano. Verdadero se crea mediante el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Para obtener más información, consulte [personalizar o cambiar colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md).

Puede guardar las paletas de colores personalizada en el disco y volver a cargarlos según sea necesario. La paleta de colores usados más recientemente se guarda en el registro y se cargan automáticamente la próxima vez que inicie Visual Studio.

- [Selección de primer plano o los colores de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)

- [Llenar un área delimitada de una imagen con un Color](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)

- [Seleccionar un Color de una imagen para utilizarlo en otro sitio](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)

- [Elegir un fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)

- [Invertir los colores de una selección](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)

- [Personalizar o cambiar colores](../windows/customizing-or-changing-colors-image-editor-for-icons.md)

- [Guardar y cargar diferentes paletas de colores](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)

- [Ventana colores](../windows/colors-window-image-editor-for-icons.md)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)
