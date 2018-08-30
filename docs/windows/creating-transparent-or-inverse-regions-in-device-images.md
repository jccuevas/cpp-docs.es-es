---
title: Crear zonas transparentes o inversas en las imágenes de dispositivo (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors, device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices, transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects, transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5bc95e75cc9a58dd6f01b8a4ca537709941f6bf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215945"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>Crear zonas transparentes o inversas en las imágenes de dispositivo (Editor de imágenes para iconos)

En el [editor de imágenes](../windows/image-editor-for-icons.md), la imagen inicial de icono o cursor tiene el atributo transparente. Aunque las imágenes de icono y cursor son rectangulares, muchos no aparecen, porque las partes de la imagen son transparentes; Muestra la imagen en la pantalla subyacente a través del icono o cursor. Cuando se arrastra un icono, partes de la imagen pueden aparecer en un color invertido. Crear este efecto estableciendo el color de la pantalla y el inverso en el [ventana colores](../windows/colors-window-image-editor-for-icons.md).

Los colores de pantalla e inversos se aplica a los iconos y cursores en forma y color de la imagen derivada o designan regiones inversas. Los colores indican las partes de la imagen que poseen estos atributos. Puede cambiar los colores que representan los atributos de color de la pantalla y color inverso en la edición. Estos cambios no afectan a la apariencia del icono o cursor en la aplicación.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la **Ayuda**, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

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

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)  
[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)