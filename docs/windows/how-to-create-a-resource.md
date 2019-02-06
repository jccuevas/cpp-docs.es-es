---
title: Filtrar Crear un recurso (C++)
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- resources [C++], viewing
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
ms.openlocfilehash: fdf158bab7894497dbcfb147eb2c6e061879be75
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764056"
---
# <a name="how-to-create-a-resource-c"></a>Filtrar Crear un recurso (C++)

El **vista de recursos** ventana muestra los archivos de recursos incluidos en los proyectos. Al expandir la carpeta superior (por ejemplo, Project1.rc) se muestran los tipos de recursos que contiene ese archivo .rc. Al expandir cada tipo de recurso se muestran los recursos individuales de ese tipo.

> [!NOTE]
> Esta información no se aplica a los recursos en aplicaciones de la plataforma Universal de Windows. Para obtener más información al respecto, consulte [recursos de la aplicación y el sistema de administración de recursos](/windows/uwp/app-resources/).

> [!NOTE]
> **Vista de recursos** no se admite en las ediciones Express.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

El **vista de recursos** ventana usa la **Agregar recurso** cuadro de diálogo Agregar recursos a un proyecto de aplicación de escritorio de Windows de C++. Este cuadro de diálogo tiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**Tipo de recurso**|Especifica el tipo de recurso que se desea crear.<br/><br/>Se pueden expandir las categorías de recursos de cursor y de cuadro de diálogo para mostrar otros recursos. Estos recursos están ubicados en ...\Microsoft Visual Studio `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Si agrega archivos .rct, debe colocarlos en este directorio o se debe especificar un [incluir ruta de acceso](../windows/how-to-specify-include-directories-for-resources.md) para ellos. Los recursos de esos archivos aparecen en el segundo nivel de la categoría correspondiente. No hay ningún límite preestablecido respecto al número de archivos .rct que puede agregar.<br/><br/>Los recursos que se muestran en el nivel superior del control de árbol son los recursos predeterminados suministrados por Visual Studio.|
|**Nuevo**|Crea un recurso en función del tipo que ha seleccionado en el **tipo de recurso** cuadro. El recurso se abrirá en el editor correspondiente. Por ejemplo, si crea un recurso de cuadro de diálogo, se abre en el [editor de cuadro de diálogo](../windows/dialog-editor.md).|
|**Import**|Se abre el **importar** cuadro de diálogo en el que se puede navegar a un recurso quiere importar en el proyecto actual. Se puede importar mapas de bits, iconos, cursores, archivos de recursos HTML, archivos de recursos de sonido (.WAV) o archivos de recursos personalizados.|
|**Custom**|Se abre el **nuevo recurso personalizado** cuadro de diálogo en el que puede crear un recurso personalizado. Los recursos personalizados solo se pueden editar en el Editor binario.|

El **nuevo recurso personalizado** cuadro de diálogo le permite crear un nuevo recurso personalizado en un proyecto de C++. Este cuadro de diálogo tiene la propiedad siguiente:

|Property|Descripción|
|---|---|
|**Tipo de recurso**|Proporciona un cuadro de texto para escribir el nombre de un tipo de recurso personalizado. Visual C++ aprovecha automáticamente el nombre cuando se cierra el **nuevo recurso personalizado** cuadro de diálogo.|

Cuando se crea un nuevo recurso, Visual C++ le asigna un nombre único, por ejemplo, `IDD_Dialog1`. Puede personalizar este identificador editando las propiedades del recurso en el editor de recursos asociado o en la [ventana Propiedades](/visualstudio/ide/reference/properties-window).

Puede crear un recurso como recursos nuevos predeterminados (es decir, un recurso que no se basa en una plantilla) o como un recurso basado en un [plantilla](../windows/how-to-use-resource-templates.md).

> [!NOTE]
> No especifique un nombre de recurso o un identificador que está reservado por Visual Studio. Los nombres reservados son DESIGNINFO, HWB y TEXTINCLUDE y el identificador reservado es 255.

## <a name="to-open-the-resource-view-window"></a>Para abrir la ventana de la Vista de recursos

Seleccione **vista de recursos** en el **vista** menú.

   \- o -

Presione **Ctrl** + **MAYÚS** + **E**.

> [!TIP]
> Puede haga doble clic en el **vista de recursos** ventana se abre un menú contextual de comandos. También se puede hacer doble clic en la barra de título para acoplar o desacoplar la ventana. Al hacer clic con el botón secundario en la barra de título se muestran comandos adicionales que permiten controlar el comportamiento de la ventana. Para obtener más información, consulte [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

## <a name="to-create-a-new-resource-in-resource-view"></a>Para crear un recurso nuevo en la Vista de recursos

1. Con el foco en el archivo .rc en **vista de recursos**, seleccione el **editar** menú y elija **Agregar recurso** (o haga clic en el archivo .rc en **devistaderecursos** y elija **Agregar recurso** en el menú contextual).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el **Agregar recurso** cuadro de diálogo, seleccione el tipo de recurso que le gustaría agregar a su proyecto.

## <a name="to-create-a-new-resource-in-solution-explorer"></a>Para crear un recurso nuevo en el Explorador de soluciones

1. En el **Explorador de soluciones**, haga clic con el botón secundario en la carpeta del proyecto y elija **Agregar**; a continuación, haga clic en **Agregar recurso** en el menú contextual.

   Si aún no tiene un archivo .rc en el proyecto, este paso creará uno. A continuación puede repetir este paso para agregar tipos de recurso específicos al nuevo archivo .rc.

2. En el **Agregar recurso** cuadro de diálogo, seleccione el tipo de recurso que le gustaría agregar a su proyecto.

## <a name="to-create-a-new-resource-in-class-view"></a>Para crear un recurso nuevo en la Vista de clases

1. En [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en la clase y elija **agregar**, a continuación, seleccione **Agregar recurso** en el menú contextual.

2. En el **Agregar recurso** cuadro de diálogo, seleccione el tipo de recurso que le gustaría agregar a su proyecto.

## <a name="to-create-a-new-resource-from-the-project-menu"></a>Para crear un recurso nuevo desde el menú Proyecto

En el menú **Proyecto** , seleccione **Agregar recurso**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
