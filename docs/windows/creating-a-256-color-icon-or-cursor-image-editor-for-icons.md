---
title: Utilizar la paleta de 256 colores (Editor de imágenes para iconos)
ms.date: 11/04/2016
helpviewer_keywords:
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
ms.openlocfilehash: 4e2f2c9ce58799756137bb47db42e52c97a43d39
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702900"
---
# <a name="using-the-256-color-palette-image-editor-for-icons"></a>Utilizar la paleta de 256 colores (Editor de imágenes para iconos)

Mediante el **imagen** editor, iconos y cursores pueden ser de tamaño grande (64 x 64) con una paleta de 256 colores para elegir. Después de crear el recurso, se selecciona un estilo de imagen de dispositivo.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-256-color-icon-or-cursor"></a>Para crear un icono de 256 colores o cursor

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, haga clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **Cursor** y elija **New**.

1. En el **imagen** menú, seleccione **nueva imagen de dispositivo**.

1. Seleccione el estilo de imagen de 256 colores que desee.

## <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Para elegir un color de la paleta de 256 colores para iconos grandes

Para dibujar con una selección de la paleta de 256 colores, deberá seleccionar los colores de la **colores** paleta en la [ventana colores](../windows/colors-window-image-editor-for-icons.md).

1. Seleccione el icono o cursor grande o cree un nuevo icono o cursor grande.

1. Elija un color de los 256 colores mostrados en la **colores** paleta en la **colores** ventana.

   El color seleccionado se convertirá en el color actual en el **colores** paleta en la **colores** ventana.

   > [!NOTE]
   > La paleta inicial que se usa para imágenes de 256 colores coincide con la paleta devuelta por la `CreateHalftonePalette` API de Windows. Todos los iconos previstos para el shell de Windows deben usar esta paleta para impedir el parpadeo durante la realización de la paleta.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Iconos y cursores: Recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
