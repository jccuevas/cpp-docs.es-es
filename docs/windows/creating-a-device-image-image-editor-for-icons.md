---
title: Crear una imagen de dispositivo (Editor de imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: 322205e22edf2624784ddb8f294bcf5e73af06f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447767"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Crear una imagen de dispositivo (Editor de imágenes para iconos)

Al crear un nuevo icono o cursor, la **imagen** editor crea primero una imagen en un estilo específico (32 x 32, 16 colores para iconos y 32 x 32, monocromático para cursores). A continuación, puede agregar imágenes de diferentes tamaños y estilos para el icono o cursor inicial y edite cada imagen adicional, según sea necesario, para los dispositivos de pantalla diferentes. También puede editar una imagen mediante la realización de una operación de cortar y pegar desde un tipo de imagen existente o desde un mapa de bits creados en un programa de gráficos.

Al abrir el recurso de icono o cursor en el [editor de imágenes](../windows/image-editor-for-icons.md), la imagen de la mayoría coincidiendo casi con el dispositivo de pantalla actual se abre de forma predeterminada.

### <a name="to-create-a-new-icon-or-cursor"></a>Para crear un nuevo icono o cursor

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, puede hacer simplemente clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **Cursor** y haga clic en **New**. Para los iconos, esto crea un recurso de icono con un 32 x 32, icono de 16 colores. Para los cursores, 32 x 32, se crea la imagen monocromática (2 colores).

   Si un signo más (**+**) aparece junto al tipo de recurso de imagen en el **Insertar recurso** cuadro de diálogo, significa que están disponibles plantillas de barra de herramientas. Haga clic en el signo más para expandir la lista de plantillas, seleccione una plantilla y haga clic en **New**.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)