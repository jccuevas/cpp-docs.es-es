---
title: Editor de imágenes para iconos
ms.date: 10/17/2018
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: 4f27b4582da340d401c3ecf10b502453d80b6e7d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561518"
---
# <a name="image-editor-for-icons"></a>Editor de imágenes para iconos

Al hacer clic en un archivo de imagen (por ejemplo, .ico, .bmp, .png) en el Explorador de soluciones, la imagen se abre en el Editor de imágenes de la misma manera que los archivos de código abierto en el Editor de código. Cuando está activa una pestaña del Editor de imágenes, vea las barras de herramientas con muchas herramientas para crear y editar imágenes. Además de mapas de bits, iconos y cursores, pueden editarse imágenes en formato GIF o JPEG mediante los comandos del menú **Imagen** y las herramientas de la barra de herramientas del **Editor de imágenes** .

Con el Editor de imágenes, se puede:

- [Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)

- [Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)

- [Trabajar con iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [Usar teclas de aceleración para comandos del Editor de imágenes](../windows/accelerator-keys-image-editor-for-icons.md)

El **Editor de imágenes** ventana muestra dos vistas de una imagen, con una barra que separa los dos paneles de división. Se puede arrastrar dicha barra a uno u otro lado para cambiar el tamaño relativo de los paneles. El panel activo muestra un borde de selección.

El **Editor de imágenes** ventana puede ajustarse para ajustarse a sus necesidades y preferencias. Se puede [cambiar el factor de ampliación](../windows/changing-the-magnification-factor-image-editor-for-icons.md) y [mostrar u ocultar la cuadrícula de píxeles](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).

> [!NOTE]
> Mediante el **Editor de imágenes**, puede ver las imágenes de 32 bits, pero no puede modificarlas.

## <a name="visual-studio-image-library"></a>Biblioteca de imágenes de Visual Studio

Puede descargar de forma gratuita la **biblioteca de imágenes de Visual Studio** que contiene muchas animaciones, mapas de bits e iconos que puede usar en sus aplicaciones. Para obtener más información sobre cómo descargar la biblioteca, vea [La biblioteca de imágenes de Visual Studio](/visualstudio/designers/the-visual-studio-image-library).

## <a name="managed-resources"></a>Recursos administrados

Puede usar el **imagen** editor y la [editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Iconos](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)