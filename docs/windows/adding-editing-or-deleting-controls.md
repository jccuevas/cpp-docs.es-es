---
title: 'Cómo: agregar, editar o eliminar controles (C++)'
ms.date: 02/15/2019
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: a42a64f93d334c0b5c63b0eca1567e6964d0a3ae
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447219"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Cómo: agregar, editar o eliminar controles (C++)

Con el **Editor de cuadros de diálogo**, puede Agregar, cambiar el tamaño, modificar y eliminar controles en los cuadros de diálogo. También puede editar las propiedades de un control, como su identificador, o si es visible inicialmente en tiempo de ejecución.

La pestaña **Editor de cuadros de diálogo** aparece en la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) cuando se trabaja en el editor de cuadros de **diálogo**. También puede personalizar la ventana del **cuadro de herramientas** para facilitar su uso. Para obtener más información, vea [usar el cuadro de herramientas](/visualstudio/ide/using-the-toolbox) y [Mostrar u ocultar la ventana del cuadro de herramientas](showing-or-hiding-the-dialog-editor-toolbar.md).

> [!TIP]
> Al usar el **Editor de cuadros de diálogo**, en muchos casos, puede seleccionar el botón secundario del mouse para mostrar un menú contextual de comandos de uso frecuente.

## <a name="add-controls"></a>para agregar controles

### <a name="to-add-a-control"></a>Para agregar un control

1. Asegúrese de que la ventana con pestañas de cuadro de diálogo sea el documento actual en el marco del editor. Si un cuadro de diálogo no es el documento actual, no verá la **pestaña Editor de cuadros de diálogo** en el **cuadro de herramientas**.

1. En la pestaña **Editor de cuadros de diálogo** de la ventana cuadro de **herramientas** , seleccione el control que desee y, a continuación:

   - Seleccione el cuadro de diálogo en la ubicación donde desea colocar el control y el control aparece donde se ha seleccionado.

   - Arrastre y coloque el control desde la ventana cuadro de **herramientas** hasta la ubicación del cuadro de diálogo. A continuación, puede mover el control alrededor o cambiar su tamaño y forma.

   - Haga doble clic en el control en la ventana cuadro de **herramientas** y aparecerá en el cuadro de diálogo. Cambie la posición del control a la ubicación que prefiera.

### <a name="to-add-multiple-controls"></a>Para agregar varios controles

1. Mientras mantiene presionada la tecla **Ctrl** , seleccione un control en la ventana **cuadro de herramientas** .

1. Suelte la tecla **Ctrl** y seleccione el cuadro de diálogo tantas veces como desee para agregar el control determinado.

1. Presione **ESC** para detener la colocación de controles.

### <a name="to-size-a-control-while-you-add-it"></a>Para ajustar el tamaño de un control mientras lo agrega

1. Seleccione un control en la ventana **cuadro de herramientas** .

1. Coloque el cursor que aparece como Cruz, donde desea que la esquina superior izquierda del nuevo control esté en el cuadro de diálogo.

1. Seleccione y mantenga presionado el botón del mouse para anclar la esquina superior izquierda del control en el cuadro de diálogo. A continuación, arrastre el cursor hacia la derecha y hacia abajo, hasta que el control tenga el tamaño que desee.

   > [!NOTE]
   > Puede anclar cualquiera de las cuatro esquinas del control que está dibujando. Este procedimiento usa la esquina superior izquierda como ejemplo.

1. Suelte el botón del mouse (ratón). El control se liquida en el cuadro de diálogo con el tamaño que se haya especificado.

> [!TIP]
> Puede cambiar el tamaño del control después de colocarlo en el cuadro de diálogo moviendo los controladores de tamaño del borde del control. Para obtener más información, vea [ajustar el tamaño de los controles individuales](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>Para agregar un control personalizado

Puede Agregar controles personalizados al cuadro de diálogo. Seleccione el icono de **control personalizado** en el cuadro de **herramientas** y arrástrelo hasta el cuadro de diálogo. Para agregar un control de `Syslink`, agregue un control personalizado y, a continuación, cambie la propiedad de **clase** del control a `Syslink`. Esta acción hará que las propiedades se actualicen y muestren las propiedades del control `Syslink`. Para obtener información sobre la clase contenedora de MFC, vea [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Controles de edición

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Para editar las propiedades de un control o de los controles

1. En el cuadro de diálogo, seleccione el control que desea modificar.

   > [!NOTE]
   > Si selecciona varios controles, solo se pueden editar las propiedades comunes a los controles seleccionados.

1. En el [ventana Propiedades](/visualstudio/ide/reference/properties-window), cambie las propiedades del control.

   > [!NOTE]
   > Cuando se establece la propiedad **Bitmap** para un botón, botón de radio o control de casilla igual a **true**, se implementa el estilo BS_BITMAP para el control. Para obtener más información, consulte [estilos de botón](../mfc/reference/styles-used-by-mfc.md#button-styles). Para obtener un ejemplo de cómo asociar un mapa de bits a un control, vea [CButton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Los mapas de bits no aparecerán en el control mientras esté en el **Editor de cuadros de diálogo**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Para deshacer los cambios en las propiedades de un control

1. Asegúrese de que el control tiene el foco en el **Editor de cuadros de diálogo**.

1. Vaya a menú **editar** > **Deshacer**. Si el foco no está en el control, el comando **Deshacer** no estará disponible.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Para definir una variable miembro para un control de cuadro de diálogo (que no sea un botón)

> [!NOTE]
> Este proceso solo se aplica a los controles de cuadro de diálogo de un proyecto MFC. Los proyectos ATL deben usar el cuadro de diálogo **nuevos mensajes y controladores de eventos de Windows** . Para obtener más información, consulte [tipos de mensajes asociados a objetos de la interfaz de usuario](../mfc/reference/message-types-associated-with-user-interface-objects.md), edición de [un controlador de mensajes](../mfc/reference/editing-a-message-handler.md)y [definición de un controlador de mensajes para un mensaje reflejado](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. En el [Editor de cuadros de diálogo](../windows/dialog-editor.md), seleccione un control.

1. Mientras presiona la tecla **Ctrl** , haga doble clic en el control cuadro de diálogo.

   Aparecerá el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) .

1. Escriba la información adecuada en el Asistente para **agregar variables miembro** . Para obtener más información, vea [intercambio de datos de cuadros de diálogo](../mfc/dialog-data-exchange.md).

1. Seleccione **Aceptar** para volver al **Editor de cuadros de diálogo**.

> [!TIP]
> Para saltar de un control de cuadro de diálogo a su controlador existente, haga doble clic en el control.

También puede usar la pestaña **variables miembro** del Asistente para [clases MFC](../mfc/reference/mfc-class-wizard.md) para agregar nuevas variables miembro para una clase especificada y ver las variables miembro ya definidas.

## <a name="delete-controls"></a>Eliminar controles

En el cuadro de diálogo, seleccione el control y, a continuación, presione la tecla **suprimir** o vaya a **edición** de menú > **eliminar**.

## <a name="other-issues"></a>Otras incidencias

### <a name="troubleshooting"></a>Solución de problemas

Después de agregar un control común o un control Rich Edit a un cuadro de diálogo, no aparecerá al probar el cuadro de diálogo. O bien, el cuadro de diálogo no aparece. Por ejemplo:

1. Cree un proyecto de Win32 y modifique la configuración de la aplicación para crear una aplicación de Windows (no una aplicación de consola).

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga doble clic en el archivo *. RC* .

1. En la opción de diálogo, haga doble clic en el cuadro **acerca de** .

1. Agregue un **control dirección IP** al cuadro de diálogo.

1. Guardar y **volver a generar todo**.

1. Ejecute el programa.

1. En el menú **ayuda** del cuadro de diálogo, seleccione el comando acerca de y observe que no se muestra ningún cuadro **de** diálogo.

Actualmente, el **Editor de cuadros de diálogo** no agrega automáticamente código al proyecto cuando se arrastran y colocan los siguientes controles comunes o controles Rich Edit en un cuadro de diálogo. Ni Visual Studio proporcionan un error o una advertencia cuando se produce este problema. Para corregirlo, agregue el código para el control manualmente.

||||
|-|-|-|
|Control deslizante|Control de árbol|Date Time Picker|
|Control de número|Control de pestaña|Month Calendar|
|Control de progreso|Animation (control)|IP Address Control|
|Tecla de acceso rápido|Rich Edit (control)|Cuadro combinado extendido|
|Control de lista|Control Rich Edit 2,0|Control personalizado|

Para usar controles comunes en un cuadro de diálogo, debe llamar a [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) o `AFXInitCommonControls` antes de crear el cuadro de diálogo.

Para utilizar controles RichEdit, debe llamar a `LoadLibrary`. Para obtener más información, vea acerca de los [controles Rich Edit](/windows/win32/Controls/about-rich-edit-controls) en el Windows SDK e [información general del control Rich Edit](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Para usar un control RichEdit con MFC, primero debe llamar a [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) para cargar el control RichEdit 2,0 (riched20. DLL) o llame a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) para cargar el Control RichEdit 1,0 anterior (Riched32. DLL).
>
> Puede usar la clase [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) actual con el control RichEdit 1,0 anterior, pero `CRichEditCtrl` solo está diseñado para admitir el control RichEdit 2,0. Dado que RichEdit 1,0 y RichEdit 2,0 son similares, la mayoría de los métodos funcionarán. Sin embargo, hay algunas diferencias entre los controles 1,0 y 2,0, por lo que algunos métodos pueden funcionar de forma incorrecta o no funcionar en absoluto.

### <a name="activex-controls"></a>Controles ActiveX

Visual Studio le permite insertar controles ActiveX en el cuadro de diálogo. Para obtener más información, vea [controles ActiveX MFC](../mfc/mfc-activex-controls.md) y [contenedores de controles ActiveX](../mfc/activex-control-containers.md).

El cuadro de diálogo **Insertar control ActiveX** permite insertar controles ActiveX en el cuadro de diálogo mientras se usa el [Editor de cuadros de diálogo](../windows/dialog-editor.md). Este cuadro de diálogo contiene las siguientes propiedades:

|Propiedad|Descripción|
|---|---|
|**Control ActiveX**|Muestra una lista de controles ActiveX.<br/><br/>Al insertar un control desde este cuadro de diálogo, no se genera una clase contenedora. Si necesita una clase contenedora, utilice [vista de clases](/visualstudio/ide/viewing-the-structure-of-code) para crear una, consulte [Agregar una clase](../ide/adding-a-class-visual-cpp.md).<br/><br/>Si un control ActiveX no aparece en este cuadro de diálogo, intente instalar el control de acuerdo con las instrucciones del proveedor.|
|**Path**|Muestra el archivo en el que se encuentra el control ActiveX.|

> [!CAUTION]
> Puede que no sea legal distribuir todos los controles ActiveX en el sistema. Consulte el contrato de licencia para el software que instaló los controles o póngase en contacto con la compañía del software.

#### <a name="to-add-an-activex-control"></a>Para agregar un control ActiveX

1. Abra un cuadro de diálogo en el **Editor de cuadros de diálogo**.

1. Haga clic con el botón secundario en cualquier lugar del cuerpo del cuadro de diálogo y seleccione **Insertar control ActiveX**.

   Aparece el cuadro de diálogo **Insertar control ActiveX** , que muestra todos los controles ActiveX del sistema. En la parte inferior del cuadro de diálogo, aparece la ruta de acceso al archivo del control ActiveX.

1. Seleccione el control que desea agregar al cuadro de diálogo y elija **Aceptar**.

   El control aparece en el cuadro de diálogo, en el que puede editar o crear controladores para él como lo haría con cualquier otro control.

> [!TIP]
> Puede utilizar el menú contextual del **Editor de cuadros de diálogo** para agregar rápidamente controles ActiveX registrados a un cuadro de diálogo o intentar agregar controles ActiveX a la ventana del cuadro de **herramientas** para facilitar el acceso.

#### <a name="to-edit-properties-for-an-activex-control"></a>Para editar las propiedades de un control ActiveX

Los controles ActiveX suministrados por proveedores independientes pueden estar equipados con sus propias propiedades y características. Estas propiedades se muestran en la ventana **propiedades** . Las páginas de propiedades creadas por los escritores del control ActiveX se muestran en el cuadro de diálogo **páginas de propiedades** . (Para ver la **Página de propiedades** de un control ActiveX específico, seleccione el botón **Página de propiedades** en el [ventana Propiedades](/visualstudio/ide/reference/properties-window)).

- Seleccione el control **ActiveX** y vaya a la **vista** de menú > **Página de propiedades** para ver las propiedades. Realice los cambios necesarios en la página de propiedades.

   En la página de propiedades de un control ActiveX se muestran varias pestañas, en función de las hojas de propiedades que se incluyen como parte del control ActiveX.

> [!NOTE]
> Este procedimiento se aplica al uso de la página de propiedades para editar controles ActiveX. También puede examinar y editar las propiedades de ActiveX en la nueva ventana **propiedades** .

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Administrar controles del cuadro de diálogo](controls-in-dialog-boxes.md)<br/>
[Cómo: diseñar controles](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Cómo: definir el acceso y los valores de control](defining-mnemonics-access-keys.md)

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->