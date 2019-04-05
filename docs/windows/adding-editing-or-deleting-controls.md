---
title: Cómo Agregar, editar o eliminar los controles (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
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
ms.openlocfilehash: 2e3e671cd92313ad120d2cd6aae3f7e815e09e65
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025369"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Cómo Agregar, editar o eliminar los controles (C++)

Mediante el **Editor de cuadro de diálogo**, puede agregar, cambiar el tamaño, editar y eliminar los controles de cuadros de diálogo. También puede editar las propiedades de un control, como su identificador, o si está visible inicialmente en tiempo de ejecución.

El **Editor de cuadro de diálogo** ficha aparece en la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) cuando está trabajando en el **Editor de cuadro de diálogo**. También puede personalizar el **cuadro de herramientas** ventana para facilitar su uso. Para obtener más información, consulte [mediante el cuadro de herramientas](/visualstudio/ide/using-the-toolbox) y [mostrar u ocultar la ventana de cuadro de herramientas](showing-or-hiding-the-dialog-editor-toolbar.md).

> [!TIP]
> Al usar el **Editor de cuadro de diálogo**, en muchos casos, puede seleccionar el botón secundario del mouse para mostrar un menú contextual de comandos usados con frecuencia.

## <a name="add-controls"></a>Agregar controles

### <a name="to-add-a-control"></a>Para agregar un control

1. Asegúrese de que la ventana con pestañas de cuadro de diálogo sea el documento actual en el marco del editor. Si un cuadro de diálogo no se encuentra el documento actual, no verá el **pestaña del cuadro de diálogo Editor** en el **cuadro de herramientas**.

1. En el **Editor de cuadro de diálogo** pestaña de la **cuadro de herramientas** ventana, seleccione el control que desee y, a continuación, ya sea:

   - Seleccione el cuadro de diálogo en la ubicación donde desea colocar el control y el control aparece donde ha seleccionado.

   - Arrastre y coloque el control desde el **cuadro de herramientas** ventana a la ubicación en el cuadro de diálogo y, a continuación, puede mover los controles o cambiar su tamaño y la forma.

   - Haga doble clic en el control en el **cuadro de herramientas** ventana y aparece en el cuadro de diálogo, a continuación, volver a colocar el control a la ubicación que prefiera.

### <a name="to-add-multiple-controls"></a>Para agregar varios controles

1. Mientras mantiene presionada la **Ctrl** clave, seleccione un control en el **cuadro de herramientas** ventana.

1. Versión del **Ctrl** clave y se selecciona el cuadro de diálogo tantas veces como desee agregar un control determinado.

1. Presione **Esc** para finalizar la colocación de controles.

### <a name="to-size-a-control-while-you-add-it"></a>Cambiar el tamaño de un control al agregarlo

1. Seleccione un control en el **cuadro de herramientas** ventana.

1. Coloque el cursor que aparece de forma de cruz, donde desea que la esquina superior izquierda del nuevo control en el cuadro de diálogo.

1. Seleccione y mantenga presionado el botón del mouse para fijar la esquina superior izquierda del control en el cuadro de diálogo, a continuación, arrastre el cursor a la derecha y hacia abajo hasta que el control es el tamaño que desee.

   > [!NOTE]
   > Puede anclar cualquiera de las cuatro esquinas del control que se está dibujando. Este procedimiento utiliza la esquina superior izquierda como ejemplo.

1. Suelte el botón del mouse. El control se coloca en el cuadro de diálogo en el tamaño especificado.

> [!TIP]
> Puede cambiar el tamaño del control después de colocarlo en el cuadro de diálogo, mueva los controladores de tamaño en el borde del control. Para obtener más información, consulte [controles individuales de ajuste de tamaño](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>Para agregar un control personalizado

Puede agregar controles personalizados al cuadro de diálogo seleccionando el **Control personalizado** icono en el **cuadro de herramientas** y arrástrela al cuadro de diálogo. Para agregar un **Syslink** de control, agregue un control personalizado y cambie el control **clase** propiedad **Syslink**. Esta acción hará que las propiedades actualizar y mostrar el **Syslink** propiedades del control. Para obtener información sobre la clase contenedora MFC, vea [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Controles de edición

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Para editar las propiedades de un control o controles

1. En el cuadro de diálogo, seleccione el control que desea modificar.

   > [!NOTE]
   > Si selecciona varios controles, se pueden editar las propiedades comunes a los controles seleccionados.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), cambiar las propiedades del control.

   > [!NOTE]
   > Al establecer el **mapa de bits** propiedad para un botón, el botón de radio o el control de casilla de verificación igual a **True**, el estilo BS_BITMAP se implementa para el control. Para obtener más información, consulte [estilos de botón](../mfc/reference/styles-used-by-mfc.md#button-styles). Para obtener un ejemplo de asociación de un mapa de bits con un control, vea [CButton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Los mapas de bits no aparecerán en el control mientras está en el **Editor de cuadro de diálogo**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Para deshacer los cambios realizados en las propiedades de un control

1. Asegúrese de que el control tiene el foco el **Editor de cuadro de diálogo**.

1. Vaya al menú **editar** > **deshacer**. Si el foco no está en el control, el **deshacer** comando dejará de estar disponible.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Para definir una variable miembro para un control de cuadro de diálogo (que no sea un botón)

> [!NOTE]
> Este proceso se aplica sólo a los controles de cuadro de diálogo de un proyecto MFC. Los proyectos ATL deben usar el **nuevos mensajes de Windows y controladores de eventos** cuadro de diálogo. Para obtener más información, consulte [tipos de mensaje asociado a los objetos de interfaz de usuario](../mfc/reference/message-types-associated-with-user-interface-objects.md), [edición de un controlador de mensajes](../mfc/reference/editing-a-message-handler.md), y [definir un controlador de mensajes para un mensaje reflejado](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. En el [Editor de cuadro de diálogo](../windows/dialog-editor.md), seleccione un control.

1. Al presionar el **Ctrl** clave, haga doble clic en el control de cuadro de diálogo.

   El [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) aparece.

1. Escriba la información correspondiente en el **agregar variables miembro** asistente. Para obtener más información, consulte [intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md).

1. Seleccione **Aceptar** para volver a la **Editor de cuadro de diálogo**.

> [!TIP]
> Para saltar de un control de cuadro de diálogo a su controlador existente, haga doble clic en el control.

También puede usar el **Variables miembro** pestaña en el [Asistente para clases MFC](../mfc/reference/mfc-class-wizard.md) para agregar nuevas variables miembro a una clase especificada y ver variables de miembro que ya se han definido.

## <a name="delete-controls"></a>Eliminar los controles

En el cuadro de diálogo, seleccione el control, a continuación, presione el **eliminar** clave o vaya al menú **editar** > **eliminar**.

## <a name="other-issues"></a>Otros problemas

### <a name="troubleshooting"></a>Solución de problemas

Después de agregar un control común o un control rich edit a un cuadro de diálogo, pero no aparecerá cuando se prueba el cuadro de diálogo o, por ejemplo, no aparecerá el cuadro de diálogo:

1. Cree un proyecto de Win32, modifique la configuración de la aplicación para crear una aplicación de Windows (no una aplicación de consola).

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga doble clic en el *.rc* archivo.

1. En la opción de cuadro de diálogo, haga doble clic en el **sobre** cuadro.

1. Agregar un **Control de dirección IP** al cuadro de diálogo.

1. Guardar y **volver a generar todo**.

1. Ejecute el programa.

1. En el cuadro de diálogo **ayuda** menú, seleccione el **sobre** comando y observe que no se muestra ningún cuadro de diálogo.

Actualmente, el **Editor de cuadro de diálogo** no agrega automáticamente código al proyecto cuando arrastra y coloca los siguientes controles comunes o controles rich edit en un cuadro de diálogo. Ni Visual Studio proporciona un error o una advertencia cuando se produce este problema. Para solucionar el problema, agregue el código para el control manualmente.

||||
|-|-|-|
|Control deslizante|Control de árbol|Date Time Picker|
|Control de número|Control de pestaña|Calendario mensual|
|Control de progreso|Control de animación|IP Address Control|
|Tecla de acceso rápido|Control Rich Edit|Cuadro combinado extendido|
|Control de lista|Control Rich Edit 2.0|Control personalizado|

Para usar controles comunes en un cuadro de diálogo, debe llamar a [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) o `AFXInitCommonControls` antes de crear el cuadro de diálogo.

Para utilizar controles RichEdit, debe llamar a `LoadLibrary`. Para obtener más información, consulte [acerca de los controles Rich Edit](/windows/desktop/Controls/about-rich-edit-controls) en el SDK de Windows y [información general sobre el Control Rich Edit](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Para usar un control RichEdit con MFC, primero debe llamar a [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) para cargar el Control RichEdit 2.0 (RICHED20. Archivo DLL), o llamar a [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) para cargar el Control RichEdit 1.0 anterior (RICHED32. (DLL).
>
> Puede usar actual [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) clase con el control RichEdit 1.0 anterior, pero `CRichEditCtrl` sólo está diseñada para admitir el control RichEdit 2.0. Porque RichEdit 1.0 y 2.0 RichEdit son similares, funcionará la mayoría de los métodos. Sin embargo, hay algunas diferencias entre los controles 1.0 y 2.0, por lo que algunos métodos podrían no funcionen correctamente o no funcionará en absoluto.

### <a name="activex-controls"></a>Controles ActiveX

Visual Studio le permite insertar controles ActiveX en el cuadro de diálogo. Para obtener más información, consulte [controles ActiveX MFC](../mfc/mfc-activex-controls.md) y [contenedores de controles ActiveX](../mfc/activex-control-containers.md).

El **insertar ActiveX Control** cuadro de diálogo le permite insertar controles ActiveX en el cuadro de diálogo al usar el [Editor de cuadro de diálogo](../windows/dialog-editor.md). Este cuadro de diálogo contiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**Control ActiveX**|Muestra una lista de controles ActiveX.<br/><br/>Insertar un control de este cuadro de diálogo no genera una clase contenedora. Si necesita una clase contenedora, utilice [vista de clases](/visualstudio/ide/viewing-the-structure-of-code) para crear uno, consulte [agregar una clase](../ide/adding-a-class-visual-cpp.md).<br/><br/>Si un control ActiveX no aparece en este cuadro de diálogo, intente instalar el control de acuerdo con las instrucciones del proveedor.|
|**Ruta de acceso**|Muestra el archivo donde se encuentra el control ActiveX.|

> [!CAUTION]
> Puede que no sea legal distribuir todos los controles ActiveX en el sistema. Consulte el contrato de licencia para el software que instaló los controles o póngase en contacto con la compañía del software.

#### <a name="to-add-an-activex-control"></a>Para agregar un control ActiveX

1. Abrir un cuadro de diálogo el **Editor de cuadro de diálogo**.

1. Haga clic en cualquier lugar en el cuerpo del cuadro de diálogo y seleccione **insertar ActiveX Control**.

   El **insertar ActiveX Control** aparece el cuadro de diálogo que muestra todos los controles ActiveX en el sistema. En la parte inferior del cuadro de diálogo, aparece la ruta de acceso al archivo del control ActiveX.

1. Seleccione el control que desea agregar al cuadro de diálogo y elija **Aceptar**.

   El control aparece en el cuadro de diálogo, en el que puede editar o crear controladores para él como lo haría con cualquier otro control.

> [!TIP]
> Puede usar el menú contextual de la **Editor de cuadro de diálogo** para agregar controles ActiveX registrados en un cuadro de diálogo de inmediato o pruebe a agregar controles ActiveX a la **cuadro de herramientas** ventana para facilitar el acceso.

#### <a name="to-edit-properties-for-an-activex-control"></a>Para editar propiedades de un control ActiveX

Controles ActiveX suministrados por proveedores independientes pueden estar equipados con sus propias propiedades y características. Estas propiedades se muestran en el **propiedades** ventana, incluida cualquier propiedad páginas creadas por los escritores del control ActiveX se muestran en el **las páginas de propiedades** cuadro de diálogo (para ver el  **Página de propiedades** de un control ActiveX concreto, seleccione el **página de propiedades** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window)).

- Seleccione el **ActiveX** control y vaya al menú **vista** > **página de propiedades** para ver las propiedades. Realice los cambios necesarios en la página de propiedades.

   Se muestran distintas pestañas en la página de propiedades para un control ActiveX, dependiendo de las hojas de propiedades que se incluyen como parte del control ActiveX.

> [!NOTE]
> Este procedimiento se aplica al uso de la página de propiedades para editar controles ActiveX. También puede examinar y editar las propiedades de ActiveX en el nuevo **propiedades** ventana.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Administrar controles de cuadro de diálogo](controls-in-dialog-boxes.md)<br/>
[Cómo Controles de diseño](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Filtrar Definir el Control de acceso y valores](defining-mnemonics-access-keys.md)<br/>

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