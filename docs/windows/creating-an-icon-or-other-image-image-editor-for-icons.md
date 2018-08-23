---
title: Crear un icono u otra imagen (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resource toolbars
- resources [Visual Studio], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bab69a9f7e62161d95ebcf788a05f776af88f10f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607239"
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>Crear un icono u otra imagen (Editor de imágenes para iconos)

Puede crear una nueva imagen (mapa de bits, icono, cursor o barra de herramientas) y luego usar el editor de imágenes para personalizar su apariencia. También puede crear un nuevo mapa de bits crearse un [plantilla](../windows/how-to-use-resource-templates.md).

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Para agregar un nuevo recurso de imagen a un proyecto de C++ no administrado

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija **Insertar recurso** en el menú contextual. (Si ya tiene un recurso de imagen existente en el archivo .rc, como un cursor, puede hacer simplemente clic en el **Cursor** carpeta y seleccione **insertar Cursor** en el menú contextual.)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el [cuadro de diálogo Insertar recurso](../windows/add-resource-dialog-box.md), seleccione el tipo de recurso de imagen que le gustaría crear (**mapa de bits**, por ejemplo), a continuación, haga clic en **New**.

   Si un signo más (**+**) aparece junto al tipo de recurso de imagen en el **Insertar recurso** cuadro de diálogo, significa que están disponibles plantillas de barra de herramientas. Haga clic en el signo más para expandir la lista de plantillas, seleccione una plantilla y haga clic en **New**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Para agregar un nuevo recurso de imagen a un proyecto en un lenguaje de programación de .NET

1. En **el Explorador de soluciones**, haga clic en la carpeta del proyecto (por ejemplo, `WindowsApplication1`).

2. En el menú contextual, haga clic en **agregar**, a continuación, elija **Agregar nuevo elemento**.

3. En el **categorías** panel, expanda el **elementos de proyecto Local** carpeta, a continuación, elija **recursos**.

4. En el **plantillas** panel, elija el tipo de recurso que le gustaría agregar a su proyecto.

   El recurso se agrega al proyecto en **el Explorador de soluciones** y el recurso se abrirá en el [editor de imágenes](../windows/image-editor-for-icons.md). Ahora puede usar todas las herramientas disponibles en el editor de imágenes para modificar la imagen. Para obtener más información sobre cómo agregar imágenes a un proyecto administrado, consulte [cargar una imagen en tiempo de diseño](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

   > [!NOTE]
   > Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados. Para obtener más información, consulte [crear archivos de recursos](/dotnet/framework/resources/creating-resource-files-for-desktop-apps) en el *Guía del desarrollador de .NET Framework*.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Iconos y cursores: recursos de imagen para dispositivos de presentación](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)  
[Conversión de mapas de bits en barras de herramientas](../windows/converting-bitmaps-to-toolbars.md)  
[Creación de nuevas barras de herramientas](../windows/creating-new-toolbars.md)  
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)