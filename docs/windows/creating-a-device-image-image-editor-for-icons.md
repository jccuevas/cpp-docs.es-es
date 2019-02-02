---
title: Crear una imagen de dispositivo (Editor de imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: ce1069f6f410d7a60d631461086ca8870ef679c0
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560301"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Crear una imagen de dispositivo (Editor de imágenes para iconos)

Al crear un nuevo icono o cursor, la **imagen** editor crea primero una imagen en un estilo específico (32 x 32, 16 colores para iconos y 32 x 32, monocromático para cursores). A continuación, puede agregar imágenes de diferentes tamaños y estilos para el icono o cursor inicial y edite cada imagen adicional, según sea necesario, para los dispositivos de pantalla diferentes. También puede editar una imagen mediante una operación de cortar y pegar desde un tipo de imagen existente o desde un mapa de bits creados en un programa de gráficos.

Al abrir el recurso de icono o cursor en el [editor de imágenes](../windows/image-editor-for-icons.md), la imagen de la mayoría coincidiendo casi con el dispositivo de pantalla actual se abre de forma predeterminada.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="new-ltdevicegt-image-type-dialog-box"></a>Nuevo &lt;dispositivo&gt; cuadro de diálogo de tipo de imagen

El **New &lt;dispositivo&gt; tipo de imagen** cuadro de diálogo le permite crear una nueva imagen de dispositivo de un tipo especificado. Para abrir el **New \<dispositivo > imagen** cuadro de diálogo, seleccione **nuevo tipo de imagen** en el **imagen** menú. Son las siguientes propiedades incluidas **tipo de imagen de destino** y **personalizado**.

### <a name="target-image-type"></a>Tipo de imagen de destino

Enumera los tipos de imagen disponible. Seleccione el tipo de imagen que desea abrir:

||||
|-|-|-|
|-16 x 16, 16 colores|-48 x 48, 16 colores|-96 x 96, 16 colores|
|-16 x 16, 256 colores|-48 x 48, 256 colores|-96 x 96, 256 colores|
|-16 x 16, monocromático|-48 x 48, monocromático|-96 x 96, monocromático|
|-32 x 32, 16 colores|-64 x 64, 16 colores||
|-32 x 32, 256 colores|-64 x 64, 256 colores||
|-32 x 32, monocromático|-64 x 64, monocromático||

> [!NOTE]
> Las imágenes ya existentes no se mostrará en esta lista.

### <a name="custom"></a>Personalizados

Se abre el **imagen personalizada** cuadro de diálogo en el que puede crear una nueva imagen con un tamaño personalizado y el número de colores.

El **imagen personalizada** cuadro de diálogo le permite crear una nueva imagen con un tamaño personalizado y el número de colores. Las siguientes propiedades que se incluyen son:

|Property|Descripción|
|---|---|
|**Width**|Proporciona un espacio para que escriba el ancho de la imagen personalizada en píxeles (1-512, límite de 2048).|
|**Height**|Proporciona un espacio para escribir el alto de la imagen personalizada en píxeles (1-512, límite de 2048).|
|**Colores**|Proporciona un espacio para elegir el número de colores para la imagen personalizada: 2, 16 o 256.|

## <a name="open-ltdevicegt-image-dialog-box"></a>Abra &lt;dispositivo&gt; cuadro de diálogo imagen

Use la **abrir &lt;dispositivo&gt; imagen** cuadro de diálogo para abrir las imágenes de dispositivo en los proyectos de C++. Enumera las imágenes de dispositivo existentes en el recurso actual (imágenes que forman parte del recurso actual). Es la siguiente propiedad incluida:

|Property|Descripción|
|---|---|
|**Imágenes actuales**|Enumera las imágenes incluidas en el recurso. Seleccione el tipo de imagen que desea abrir.|

## <a name="to-create-a-new-icon-or-cursor"></a>Para crear un nuevo icono o cursor

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, haga clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione **icono** o **Cursor** y elija **New**. Para los iconos, esta acción crea un recurso de icono con un 32 x 32, icono de 16 colores. Para los cursores, 32 x 32, se crea la imagen monocromática (2 colores).

   Si un signo más (**+**) aparece junto al tipo de recurso de imagen en el **Insertar recurso** cuadro de diálogo, significa que están disponibles plantillas de barra de herramientas. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **New**.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Iconos y cursores: Recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Iconos y cursores: Recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Imagen (menú)](../windows/image-menu-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
