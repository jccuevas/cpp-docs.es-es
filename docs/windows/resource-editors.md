---
title: Editores de recursos (C++)
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: a0b5e3905daf72307702dbe4f05c2871cf768ac0
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328810"
---
# <a name="resource-editors-c"></a>Editores de recursos (C++)

Un editor de recursos es un entorno especializado para la creación o modificación de los recursos que se incluyen en un proyecto de Visual Studio. Los editores de recursos de Visual Studio comparten técnicas e interfaces que ayudan a crear y modificar recursos de la aplicación de forma rápida y sencilla. Editores de recursos permiten ver y editar recursos en los recursos adecuados de editor y vista previa.

Al crear o abrir un recurso, se abre automáticamente el editor correspondiente.

> [!NOTE]
> Dado que los proyectos administrados no usan archivos de script de recursos, debe abrir los recursos desde **el Explorador de soluciones**. Puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

|Use...|Para editar...|
|----------------|----------------|
|[Editor de aceleradores](../windows/accelerator-editor.md)|Tablas de aceleradores en proyectos de Visual C++.|
|[Binary Editor](binary-editor.md)|Información de datos binarios y recursos personalizados en proyectos de Visual C++, Visual Basic o Visual C#.|
|[Editor de cuadros de diálogo](../windows/dialog-editor.md)|Cuadros de diálogo en proyectos de Visual C++.|
|[Image Editor](../windows/image-editor-for-icons.md)|Mapas de bits, iconos, cursores y otros archivos de imagen en proyectos de Visual C++, Visual Basic o Visual C#.|
|[Editor de menús](../windows/menu-editor.md)|Recursos de menús en proyectos de Visual C++.|
|[Editor de Ribbon](../mfc/ribbon-designer-mfc.md)|Recursos de cinta de opciones en proyectos de MFC.|
|[Editor de cadenas](../windows/string-editor.md)|Tablas de cadenas en proyectos de Visual C++.|
|[Editor de barras de herramientas](../windows/toolbar-editor.md)|Recursos de barras de herramientas en proyectos de Visual C++. El **barra de herramientas del Editor** forma parte de la **Editor de imágenes**.|
|[Editor de la información de versión](../windows/version-information-editor.md)|Información de versión en proyectos de Visual C++.|

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Cómo: Crear recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Ver y editar recursos

Cada tipo de recurso tiene un editor de recursos específico de ese tipo de recurso. Puede reorganizar, cambiar el tamaño, agregar controles y características o modificar otros aspectos de un recurso con el editor asociado. También puede editar un recurso en [formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md) y [formato binario](../windows/opening-a-resource-for-binary-editing.md).

Algunos tipos de recursos son archivos individuales que se pueden importar y usar de diversas maneras; Estos incluyen los mapas de bits, iconos, cursores, barras de herramientas y los archivos html. Estos recursos tienen nombres de archivo y [identificadores de recursos](../windows/symbols-resource-identifiers.md). Otros, como cuadros de diálogo, menús y las tablas de cadenas en los proyectos de Win32, sólo existen como parte de un archivo de recursos (.rc) de la secuencia de comandos o el archivo de recursos (.rct) de la plantilla.

Los recursos también se pueden editar fuera del proyecto sin necesidad de abrir el proyecto, vea [Cómo: Crear recursos](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Propiedades de un recurso pueden modificarse mediante el **propiedades** ventana.

- Para editar las propiedades de un recurso, en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic en el recurso que desea editar y elija **propiedades**.  A continuación, en el [ventana propiedades](/visualstudio/ide/reference/properties-window), cambiar las propiedades del recurso.

- Para deshacer los cambios realizados en las propiedades de un recurso, asegúrese de que el recurso tiene el foco **vista de recursos** y elija **deshacer** desde el **editar** menú.

### <a name="win32-resources"></a>Recursos de Win32

Puede obtener acceso a los recursos de Win32 en el [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) panel.

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Para ver un recurso de Win32 en un editor de recursos

1. Vaya al menú **vista** > **vista de recursos**.

1. Si el **vista de recursos** ventana no es la ventana de nivel superior, seleccione el **vista de recursos** tab para colocarlo en la parte superior.

1. Desde **vista de recursos**, expanda la carpeta del proyecto que contiene recursos que desea ver. Por ejemplo, si desea ver un recurso de cuadro de diálogo, expanda el **diálogo** carpeta.

1. Haga doble clic en el recurso, por ejemplo, **IDD_ABOUTBOX**.

   El recurso se abrirá en el editor correspondiente. Por ejemplo, para los recursos de cuadro de diálogo, el recurso se abrirá dentro de la **Editor de cuadro de diálogo**.

#### <a name="to-delete-an-existing-win32-resource"></a>Para eliminar un recurso existente de Win32

1. En **vista de recursos**, expanda el nodo de un tipo de recurso.

1. Haga doble clic en el recurso que desea eliminar y elija **eliminar**.

> [!TIP]
> También puede usar este método cuando tenga el archivo .rc abierto en una ventana de documento fuera de un proyecto.

### <a name="managed-project-resources"></a>Recursos del proyecto administrado

Dado que los proyectos administrados no usan archivos de script de recursos, debe abrir los recursos desde **el Explorador de soluciones**. Use la [Editor de imágenes](../windows/image-editor-for-icons.md) y [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que se va a editar deberán estar vinculados y editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

- Para ver un recurso administrado en un editor de recursos, en **el Explorador de soluciones**, haga doble clic en el recurso, por ejemplo, *Bitmap1.bmp*, y el recurso se abrirá en el editor adecuado.

- Para eliminar un recurso administrado existente, en **el Explorador de soluciones**, haga clic en el recurso que desea eliminar y elija **eliminar**.

## <a name="preview-resources"></a>Recursos de la versión preliminar

Obtener una vista previa de los recursos para que pueda ver recursos gráficos sin abrirlos. Obtener una vista previa también es útil para archivos ejecutables ya compilados, ya que cambian los identificadores de recursos a los números. Dado que estos identificadores numéricos a menudo no proporcionan suficiente información, vista previa de los recursos ayuda a identificarlos con rapidez.

Los siguientes tipos de recursos proporcionan una vista previa de diseño visual: Mapa de bits, cuadro de diálogo, icono, menús, cursores, barra de herramientas

Los siguientes recursos no proporcionan una vista previa: Acelerador de la información de versión del manifiesto de la tabla de cadenas

> [!NOTE]
> Para obtener una vista previa de recursos requiere Win32.

### <a name="to-preview-resources"></a>Para obtener una vista previa de recursos

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) o una ventana de documento, seleccione el recurso, por ejemplo, **IDD_ABOUTBOX**.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), seleccione el **páginas de propiedades** botón.

   > [!TIP]
   > Usar un acceso directo, vaya al menú **vista** > **páginas de propiedades**.

   El **propiedad** página para el recurso abrirá una vista previa de ese recurso. Puede usar el **seguridad** y **abajo** teclas de flecha para navegar por el árbol de control en **vista de recursos** o la ventana de documento. El **propiedad** página permanecerá abierta y mostrará todos los recursos que tiene el foco y pueden obtener una vista previa.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>