---
title: Ver y editar recursos en un Editor de recursos (C++)
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
ms.openlocfilehash: 02ab58d37f3f188c3d65740b218cb9b2ac799714
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742666"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor-c"></a>Ver y editar recursos en un Editor de recursos (C++)

Cada tipo de recurso tiene un **recursos** editor de ese tipo de recurso específico. Puede reorganizar, cambiar el tamaño, agregar controles y características o modificar otros aspectos de un recurso con el editor asociado. También puede editar un recurso en [formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md) y [formato binario](../windows/opening-a-resource-for-binary-editing.md).

Algunos tipos de recursos son archivos individuales que se pueden importar y usar de diversas maneras; Estos incluyen los mapas de bits, iconos, cursores, barras de herramientas y los archivos html. Estos recursos tienen nombres de archivo y [identificadores de recursos](../windows/symbols-resource-identifiers.md). Otros, como cuadros de diálogo, menús y las tablas de cadenas en los proyectos de Win32, sólo existen como parte de un archivo de recursos (.rc) de la secuencia de comandos o el archivo de recursos (.rct) de la plantilla.

> [!NOTE]
> Propiedades de un recurso [puede modificarse mediante la ventana propiedades](../windows/changing-the-properties-of-a-resource.md).

## <a name="win32-resources"></a>Recursos de Win32

Puede obtener acceso a los recursos de Win32 en el [vista de recursos](../windows/resource-view-window.md) panel.

### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Para ver un recurso de Win32 en un editor de recursos

1. Seleccione **vista de recursos** desde el **vista** menú.

1. Si el **vista de recursos** ventana no es la ventana de nivel superior, seleccione el **vista de recursos** tab para colocarlo en la parte superior.

1. Desde **vista de recursos**, expanda la carpeta del proyecto que contiene recursos que desea ver. Por ejemplo, si desea ver un recurso de cuadro de diálogo, expanda el **diálogo** carpeta.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. Haga doble clic en el recurso, por ejemplo, **IDD_ABOUTBOX**.

   El recurso se abrirá en el editor correspondiente. Por ejemplo, para los recursos de cuadro de diálogo, el recurso se abrirá dentro de la **diálogo** editor.

   También puede [ver recursos en un archivo .rc (script de recursos) sin tener un proyecto abierto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-delete-an-existing-win-32-resource"></a>Para eliminar un recurso existente de Win 32

1. En **vista de recursos**, expanda el nodo de un tipo de recurso.

2. Haga doble clic en el recurso que desea eliminar y elija **eliminar** en el menú contextual.

   > [!NOTE]
   > Puede eliminar un recurso mediante el comando del menú contextual cuando tenga el archivo .rc abierto en una ventana de documento fuera de un proyecto.

## <a name="resources-in-managed-projects"></a>Recursos en proyectos administrados

Dado que los proyectos administrados no usan archivos de script de recursos, debe abrir los recursos desde **el Explorador de soluciones**. Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Para ver un recurso administrado en un editor de recursos

En **el Explorador de soluciones**, haga doble clic en el recurso, por ejemplo, **Bitmap1.bmp**.

   El recurso se abrirá en el editor correspondiente.

### <a name="to-delete-an-existing-managed-resource"></a>Para eliminar un recurso administrado existente

En **el Explorador de soluciones**, haga clic en el recurso que desea eliminar y elija **eliminar** en el menú contextual.

## <a name="changing-the-properties-of-resources"></a>Cambiar las propiedades de recursos

### <a name="to-edit-the-properties-of-a-resource"></a>Para editar las propiedades de un recurso

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el recurso que desea editar y elija **propiedades** en el menú contextual.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), cambiar las propiedades del recurso.

### <a name="to-undo-a-change-made-to-the-properties-of-a-resource"></a>Para deshacer un cambio realizado en las propiedades de un recurso

1. Asegúrese de que el recurso tiene el foco **vista de recursos**.

1. Elija **deshacer** desde el **editar** menú.

## <a name="previewing-resources"></a>Vista previa de recursos

Obtener una vista previa de los recursos para que pueda ver recursos gráficos sin abrirlos. Obtener una vista previa también es útil para los archivos ejecutables después de que haya compilado ya que cambian los identificadores de recursos a los números. Dado que estos identificadores numéricos a menudo no proporcionan suficiente información, vista previa de los recursos ayuda a identificarlos con rapidez.

Puede obtener una vista previa del diseño visual de los siguientes tipos de recursos:

- Bitmap

- Cuadro de diálogo

- Iconos

- Menú

- Cursor

- Barra de herramientas

La función de vista previa no se aplica a los recursos del acelerador, manifiesto, tabla de cadenas e información de versión.

### <a name="to-preview-resources"></a>Para obtener una vista previa de recursos

1. En [vista de recursos](../windows/resource-view-window.md) o una ventana de documento, seleccione el recurso, por ejemplo, **IDD_ABOUTBOX**.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), seleccione el **páginas de propiedades** botón.

   \- o -

   En el **vista** menú, seleccione **páginas de propiedades**.

   El **página de propiedades** para el recurso se abrirá una vista previa de ese recurso. A continuación, puede usar el **seguridad** y **hacia abajo** teclas de flecha para navegar por el árbol de control en **vista de recursos** o la ventana de documento. El **página de propiedades** permanecerá abierta y mostrará todos los recursos que tiene el foco y pueden obtener una vista previa.

> [!NOTE]
> Para obtener una vista previa de recursos requiere Win32.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Cómo: Abrir un archivo de script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Editores de recursos](../windows/resource-editors.md)