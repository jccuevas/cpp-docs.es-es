---
title: Ver y agregar controles ActiveX a un cuadro de diálogo (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 139407ec1d4e1bfad6bb06854dc24b86ce7014e8
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293616"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>Ver y agregar controles ActiveX a un cuadro de diálogo (C++)

Visual Studio le permite insertar controles ActiveX en el cuadro de diálogo.

El **insertar ActiveX Control** cuadro de diálogo le permite insertar controles ActiveX en el cuadro de diálogo al usar el [editor de cuadro de diálogo](../windows/dialog-editor.md). Este cuadro de diálogo contiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**ActiveX Control**|Muestra una lista de controles Active X. Insertar un control de este cuadro de diálogo no genera una clase contenedora. Si necesita una clase contenedora, utilice [vista de clases](/visualstudio/ide/viewing-the-structure-of-code) para crear uno (para obtener más información, consulte [agregar una clase](../ide/adding-a-class-visual-cpp.md)). Si un control ActiveX no aparece en este cuadro de diálogo, intente instalar el control de acuerdo con las instrucciones del proveedor.|
|**Ruta de acceso**|Muestra el archivo donde se encuentra el control ActiveX.|

Puede colocar controles en el **cuadro de herramientas** ventana para facilitar el acceso. Para obtener más información, vea [Cuadro de herramientas](/visualstudio/ide/reference/).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-see-the-activex-controls-you-have-available"></a>Para ver los controles ActiveX que tiene a su disposición

1. Abra un cuadro de diálogo en el editor del cuadro de diálogo.

1. Con el botón secundario en cualquier lugar en el cuerpo del cuadro de diálogo.

1. En el menú contextual, seleccione **insertar ActiveX Control**.

   El **insertar ActiveX Control** aparece el cuadro de diálogo que muestra todos los controles ActiveX en el sistema. En la parte inferior del cuadro de diálogo, aparece la ruta de acceso al archivo del control ActiveX.

## <a name="to-add-an-activex-control-to-a-dialog-box"></a>Para agregar un control ActiveX a un cuadro de diálogo

1. En el **insertar ActiveX Control** cuadro de diálogo, seleccione el control que desea agregar al cuadro de diálogo y seleccione **Aceptar**.

   El control aparece en el cuadro de diálogo, en el que puede editar o crear controladores para él como lo haría con cualquier otro control.

   > [!NOTE]
   > Puede agregar controles ActiveX a la [ventana del cuadro de herramientas](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Puede que no sea legal distribuir todos los controles ActiveX en el sistema. Consulte el contrato de licencia para el software que instaló los controles o póngase en contacto con la compañía del software.

   Puede colocar controles en el **cuadro de herramientas** ventana para facilitar el acceso. Para obtener más información, vea [Cuadro de herramientas](/visualstudio/ide/reference/toolbox).

## <a name="to-edit-properties-for-an-activex-control"></a>Para editar propiedades de un control ActiveX

Controles ActiveX suministrados por proveedores independientes pueden estar equipados con sus propias propiedades y características. Propiedades de los controles ActiveX se muestran en el **propiedades** ventana. Además, se muestran las páginas de propiedades creadas por los programadores del control ActiveX en el **las páginas de propiedades** cuadro de diálogo (para ver el **página de propiedades** de un control ActiveX concreto, haga clic en el  **Página de propiedades** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window)).

Se muestran distintas pestañas en la página de propiedades para un control ActiveX, dependiendo de las hojas de propiedades que se incluyen como parte del control ActiveX.

> [!NOTE]
> El siguiente procedimiento se aplica al uso de la página de propiedades para editar controles ActiveX. También puede examinar y editar las propiedades de ActiveX en el nuevo **propiedades** ventana.

1. Seleccione el **ActiveX** control.

1. En el **vista** menú, seleccione **página de propiedades** y ver las propiedades.

1. Realice los cambios necesarios en la página de propiedades.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)<br/>
[Visualización y adición de controles ActiveX a un cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[Editor de cuadros de diálogo (pestaña, cuadro de herramientas)](../windows/dialog-editor-tab-toolbox.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
