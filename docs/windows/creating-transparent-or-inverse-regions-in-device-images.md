---
title: Crear zonas transparentes o inversas en las imágenes de dispositivo (Editor de imágenes para iconos)
ms.date: 11/04/2016
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
ms.openlocfilehash: 3c4f5aa0b63259fbe42c353525e52319db1b0667
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626647"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>Crear zonas transparentes o inversas en las imágenes de dispositivo (Editor de imágenes para iconos)

En el [editor de imágenes](../windows/image-editor-for-icons.md), la imagen inicial de icono o cursor tiene el atributo transparente. Aunque las imágenes de icono y cursor son rectangulares, muchos no aparecen, porque las partes de la imagen son transparentes; Muestra la imagen en la pantalla subyacente a través del icono o cursor. Cuando se arrastra un icono, partes de la imagen pueden aparecer en un color invertido. Crear este efecto estableciendo el color de la pantalla y el inverso en el [ventana colores](../windows/colors-window-image-editor-for-icons.md).

Los colores de pantalla e inversos se aplica a los iconos y cursores en forma y color de la imagen derivada o designan regiones inversas. Los colores indican las partes de la imagen que poseen estos atributos. Puede cambiar los colores que representan los atributos de color de la pantalla y color inverso en la edición. Estos cambios no afectan a la apariencia del icono o cursor en la aplicación.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la **Ayuda**, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-transparent-or-inverse-regions"></a>Para crear zonas transparentes o inversas

1. En el **colores** ventana, haga clic en el **Color de pantalla** selector o **Color inverso** selector.

2. Aplique la pantalla o el color inverso a la imagen mediante una herramienta de dibujo. Para obtener más información sobre herramientas de dibujo, consulte [mediante una herramienta de dibujo](using-a-drawing-tool-image-editor-for-icons.md).

### <a name="to-change-the-screen-or-inverse-color"></a>Para cambiar el color de pantalla o inverso

1. Seleccione el **Color de pantalla** selector o **Color inverso** selector.

2. Elija un color en el **colores** paleta en la **colores** ventana.

   El color complementario se designa automáticamente para el selector de otro.

   > [!TIP]
   > Si hace doble clic en el **Color de pantalla** o **Color inverso** selector, el [cuadro de diálogo Selector de colores personalizados](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) aparece.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)