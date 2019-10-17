---
title: Editores de recursosC++()
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
ms.openlocfilehash: 893ddf3b4d030384572baf77647e09d4d2a9d719
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444994"
---
# <a name="resource-editors-c"></a>Editores de recursosC++()

Un editor de recursos es un entorno especializado para crear o modificar recursos que se incluyen en un proyecto de Visual Studio. Los editores de recursos de Visual Studio comparten técnicas e interfaces que ayudan a crear y modificar recursos de la aplicación de forma rápida y sencilla. Los editores de recursos permiten ver y editar recursos en el editor adecuado y obtener una vista previa de los recursos.

Al crear o abrir un recurso, se abre automáticamente el editor correspondiente.

> [!NOTE]
> Dado que los proyectos administrados no usan archivos de script de recursos, debe abrir los recursos desde **Explorador de soluciones**. Puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

|Use...|Para editar...|
|----------------|----------------|
|[Editor de aceleradores](../windows/accelerator-editor.md)|Tablas de aceleradores en C++ proyectos de Visual Studio.|
|[Binary Editor](binary-editor.md)|Información de datos binarios y recursos personalizados en proyectos de Visual C++, Visual Basic o Visual C#.|
|[Editor de cuadros de diálogo](../windows/dialog-editor.md)|Cuadros de diálogo en proyectos C++ de Visual Studio.|
|[Image Editor](../windows/image-editor-for-icons.md)|Mapas de bits, iconos, cursores y otros archivos de imagen en proyectos de Visual C++, Visual Basic o Visual C#.|
|[Editor de menús](../windows/menu-editor.md)|Recursos de menús en proyectos C++ de Visual Studio.|
|[Editor de Ribbon](../mfc/ribbon-designer-mfc.md)|Recursos de cinta de opciones en proyectos de MFC.|
|[Editor de cadenas](../windows/string-editor.md)|Tablas de cadenas en proyectos C++ de Visual Studio.|
|[Editor de barras de herramientas](../windows/toolbar-editor.md)|Recursos de la barra de C++ herramientas en proyectos de Visual Studio. El **Editor** de la barra de herramientas forma parte del **Editor de imágenes**.|
|[Editor de información de versión](../windows/version-information-editor.md)|Información de versión en proyectos C++ de Visual Studio.|

> [!NOTE]
> Si el proyecto aún no contiene un archivo. rc, consulte [Cómo: crear recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Ver y editar recursos

Cada tipo de recurso tiene un editor de recursos específico para ese tipo de recurso. Puede reorganizar, cambiar el tamaño, agregar controles y características, o bien modificar los aspectos de un recurso mediante el editor asociado. También puede modificar un recurso en formato de [texto](../windows/how-to-open-a-resource-script-file-in-text-format.md) y [formato binario](../windows/opening-a-resource-for-binary-editing.md).

Algunos tipos de recursos son archivos individuales que se pueden importar y usar de varias maneras; entre ellas se incluyen mapas de bits, iconos, cursores, barras de herramientas y archivos HTML. Estos recursos tienen nombres de archivo e [identificadores de recursos](../windows/symbols-resource-identifiers.md). Otros, como cuadros de diálogo, menús y tablas de cadenas en proyectos de Win32, solo existen como parte de un archivo de script de recursos (. RC) o un archivo de plantilla de recursos (. RCT).

Los recursos también se pueden editar fuera del proyecto sin tener el proyecto abierto; consulte [Cómo: crear recursos](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Las propiedades de un recurso se pueden modificar mediante la ventana **propiedades** .

- Para editar las propiedades de un recurso, en [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic con el botón secundario en el recurso que desea editar y elija **propiedades**.  A continuación, en el [ventana Propiedades](/visualstudio/ide/reference/properties-window), cambie las propiedades del recurso.

- Para deshacer un cambio realizado en las propiedades de un recurso, asegúrese de que el recurso tiene el foco en **vista de recursos** y elija **Deshacer** en el menú **edición** .

### <a name="win32-resources"></a>Recursos de Win32

Puede tener acceso a los recursos de Win32 en el panel [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) .

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Para ver un recurso de Win32 en un editor de recursos

1. Vaya a la **vista**de menú  > **otras ventanas** > **vista de recursos**.

1. Si la ventana de **vista de recursos** no es la ventana de nivel superior, seleccione la pestaña **vista de recursos** para colocarla en la parte superior.

1. En **vista de recursos**, expanda la carpeta del proyecto que contiene los recursos que desea ver. Por ejemplo, si desea ver un recurso de cuadro de diálogo, expanda la carpeta del **cuadro de diálogo** .

1. Haga doble clic en el recurso, por ejemplo, **IDD_ABOUTBOX**.

   El recurso se abrirá en el editor correspondiente. Por ejemplo, para los recursos de diálogo, el recurso se abre en el **Editor de cuadros de diálogo**.

#### <a name="to-delete-an-existing-win32-resource"></a>Para eliminar un recurso de Win32 existente

1. En **vista de recursos**, expanda el nodo de un tipo de recurso.

1. Haga clic con el botón derecho en el recurso que desea eliminar y elija **eliminar**.

> [!TIP]
> También puede usar este método cuando tenga el archivo. RC abierto en una ventana de documento fuera de un proyecto.

### <a name="managed-project-resources"></a>Recursos del proyecto administrado

Dado que los proyectos administrados no usan archivos de script de recursos, debe abrir los recursos desde **Explorador de soluciones**. Use el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Los recursos administrados que desee editar deben ser recursos vinculados y los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

- Para ver un recurso administrado en un editor de recursos, en **Explorador de soluciones**, haga doble clic en el recurso, por ejemplo, *Bitmap1. bmp*y el recurso se abrirá en el editor adecuado.

- Para eliminar un recurso administrado existente, en **Explorador de soluciones**, haga clic con el botón secundario en el recurso que desea eliminar y elija **eliminar**.

## <a name="preview-resources"></a>Vista previa de recursos

Obtenga una vista previa de los recursos para que pueda ver los recursos gráficos sin abrirlos. La vista previa también es útil para los ejecutables después de compilarlos, ya que los identificadores de recursos cambian a números. Dado que estos identificadores numéricos a menudo no proporcionan suficiente información, la vista previa de los recursos ayuda a identificarlos rápidamente.

Los siguientes tipos de recursos proporcionan una vista previa del diseño visual: mapa de bits, cuadro de diálogo, icono, menú, cursor, barra de herramientas

Los siguientes recursos no proporcionan una vista previa visual: acelerador, manifiesto, tabla de cadenas, información de versión

> [!NOTE]
> Para obtener una vista previa de los recursos se requiere Win32.

### <a name="to-preview-resources"></a>Para obtener una vista previa de los recursos

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) o una ventana de documento, seleccione el recurso, por ejemplo, **IDD_ABOUTBOX**.

1. En el [ventana Propiedades](/visualstudio/ide/reference/properties-window), seleccione el botón **páginas de propiedades** .

   > [!TIP]
   > Usar un acceso directo, vaya a la **vista**de menú  > **páginas de propiedades**.

   Se abre la página de **propiedades** del recurso que muestra una vista previa de ese recurso. Puede utilizar las teclas de dirección **arriba** y **abajo** para navegar por el control de árbol en **vista de recursos** o en la ventana de documento. La página de **propiedades** permanecerá abierta y mostrará cualquier recurso que tenga el foco y se podrá obtener una vista previa.

## <a name="requirements"></a>Requisitos

Ninguno

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>