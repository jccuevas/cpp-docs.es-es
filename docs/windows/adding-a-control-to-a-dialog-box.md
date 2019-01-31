---
title: Agregar un Control a un cuadro de diálogo (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
helpviewer_keywords:
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
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
ms.openlocfilehash: 92b644769bcbe2649d00ba68437bd474ee06dfcc
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293629"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>Agregar un Control a un cuadro de diálogo (C++)

El **Editor de cuadro de diálogo** ficha aparece en la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) cuando está trabajando en el **diálogo** editor. Para agregar controles al cuadro de diálogo de nuevo, arrastre controles desde el **cuadro de herramientas** en el cuadro de diálogo que se va a crear. Después, puede mover los controles o cambiar su tamaño y su forma.

Los controles estándares disponibles en el **cuadro de herramientas** son:

- [Control de botón](../mfc/reference/cbutton-class.md)

- [Control de casilla de verificación](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Control de cuadro combinado](../mfc/reference/ccombobox-class.md)

- [Control de edición](../mfc/reference/cedit-class.md)

- Cuadro de grupo

- [Control de cuadro de lista](../mfc/reference/clistbox-class.md)

- [Control de botón de radio](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Control de texto estático](../mfc/reference/cstatic-class.md)

- [Control de imagen](../mfc/reference/cpictureholder-class.md)

- [Control Rich Edit 2.0](../mfc/using-cricheditctrl.md)

- [Control de barra de desplazamiento](../mfc/reference/cscrollbar-class.md)

El [controles comunes de Windows](../mfc/controls-mfc.md) disponibles en el **cuadro de herramientas** ofrecen una mayor funcionalidad en la aplicación. Son los siguientes:

- [Control deslizante](../mfc/slider-control-styles.md)

- [Control de número](../mfc/using-cspinbuttonctrl.md)

- [Control de progreso](../mfc/styles-for-the-progress-control.md)

- [Hot Key (control)](../mfc/using-a-hot-key-control.md)

- [Control de lista](../mfc/list-control-and-list-view.md)

- [Control de árbol](../mfc/tree-control-styles.md)

- [Control de pestaña](../mfc/tab-controls-and-property-sheets.md)

- [Control de animación](../mfc/using-an-animation-control.md)

- [Control de selector de hora de fecha](../mfc/creating-the-date-and-time-picker-control.md)

- [Control de calendario mensual](../mfc/month-calendar-control-examples.md)

- [Control de dirección IP](../mfc/reference/cipaddressctrl-class.md)

- [Control de cuadro combinado extendido](../mfc/creating-an-extended-combo-box-control.md)

- [Control personalizado](custom-controls-in-the-dialog-editor.md)

Puede agregar controles personalizados al cuadro de diálogo seleccionando el **Control personalizado** icono en el **cuadro de herramientas** y arrástrela al cuadro de diálogo. Para agregar un **Syslink** de control, agregue un control personalizado y cambie el control **clase** propiedad **Syslink**. Esto hará que las propiedades actualizar y mostrar el **Syslink** propiedades del control. Para obtener información sobre la clase contenedora MFC, vea [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

También puede [agregar controles ActiveX al cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

También puede personalizar el **cuadro de herramientas** ventana para facilitar su uso. Para obtener más información, vea [Usar el cuadro de herramientas](/visualstudio/ide/using-the-toolbox).

Para obtener más información sobre el uso de la **RichEdit 1.0** control con MFC, vea [con el Control RichEdit 1.0 con MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-add-a-control-to-a-dialog-box"></a>Para agregar un control a un cuadro de diálogo

1. Asegúrese de que la ventana con pestañas de cuadro de diálogo sea el documento actual en el marco del editor. Si un cuadro de diálogo no se encuentra el documento actual, no verá el **pestaña del cuadro de diálogo Editor** en el **cuadro de herramientas**.

1. En el **Editor de cuadro de diálogo** pestaña de la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox), seleccione el control que desee y, a continuación:

   - Seleccione el cuadro de diálogo en la ubicación donde desea colocar el control. El control aparece donde ha seleccionado.

       \- o -

   - Arrastre y coloque el control desde el **cuadro de herramientas** ventana hasta la ubicación en el cuadro de diálogo.

       \- o -

   - Haga doble clic en el control en el **cuadro de herramientas** ventana (aparece en el cuadro de diálogo), a continuación, cambiar de posición el control a la ubicación que prefiera.

## <a name="to-add-multiple-controls"></a>Para agregar varios controles

1. Mientras mantiene presionada la **Ctrl** clave, seleccione un control en el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox).

1. Versión del **Ctrl** clave y se selecciona el cuadro de diálogo tantas veces como desee agregar un control determinado.

1. Presione **Esc** para finalizar la colocación de controles.

## <a name="to-size-a-control-while-you-add-it"></a>Cambiar el tamaño de un control al agregarlo

1. Seleccione un control en el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox).

1. Coloque el cursor (que aparece como en cruz) donde desea que la esquina superior izquierda del nuevo control en el cuadro de diálogo.

1. Seleccione y mantenga presionado el botón del mouse para fijar la esquina superior izquierda del control en el cuadro de diálogo, a continuación, arrastre el cursor a la derecha y hacia abajo hasta que el control es el tamaño que desee.

   > [!NOTE]
   > En realidad puede anclar cualquiera de las cuatro esquinas del control que se está dibujando. Este procedimiento utiliza la esquina superior izquierda como ejemplo.

1. Suelte el botón del mouse. El control se coloca en el cuadro de diálogo en el tamaño especificado.

   > [!TIP]
   > Puede cambiar el tamaño del control después de colocarlo en el cuadro de diálogo, mueva los controladores de tamaño en el borde del control. Para obtener más información, consulte [controles individuales de ajuste de tamaño](../windows/sizing-individual-controls.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Agregar controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controles](../mfc/controls-mfc.md)<br/>
[Clases de control](../mfc/control-classes.md)<br/>
[Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)<br/>
[Estilos de barra de desplazamiento](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)<br/>
[Ejemplos de control Rich Edit](../mfc/rich-edit-control-examples.md)<br/>
