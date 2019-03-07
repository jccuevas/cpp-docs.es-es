---
title: Controles de cuadro de diálogo (C++) | Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: 152113200fd7aa9ee87b749380e370fe4e6ad9ff
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563360"
---
# <a name="dialog-box-controls-c"></a>Controles de cuadro de diálogo (C++)

Puede agregar controles a un cuadro de diálogo mediante la **Editor de cuadro de diálogo** pestaña en el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) que le permite elegir el control que desee y arrástrelo hasta el cuadro de diálogo. De forma predeterminada, el **cuadro de herramientas** ventana está establecida en la opción Ocultar automáticamente. Aparece como una pestaña en el margen izquierdo de la solución cuando el **Editor de cuadro de diálogo** está abierto. Sin embargo, puede anclar el **cuadro de herramientas** ventana a su posición seleccionando el **Ocultar automáticamente** botón en la esquina superior derecha de la ventana. Para obtener más información sobre cómo controlar el comportamiento de esta ventana, consulte [administración de ventanas](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

La manera más rápida de agregar controles a un cuadro de diálogo, volver a colocar los controles existentes o mover los controles de cuadro de diálogo de uno a otro, es usar el método de arrastrar y colocar. La posición del control se muestra en una línea de puntos hasta que se coloca en el cuadro de diálogo. Al agregar un control a un cuadro de diálogo con el método de arrastrar y colocar, el control tiene un alto estándar adecuado para ese tipo de control.

Al agregar un control a un cuadro de diálogo o cambia la posición, su ubicación final puede verse determinado por las guías o los márgenes, o si tiene activada la cuadrícula de diseño.

Una vez haya agregado un control al cuadro de diálogo, puede cambiar las propiedades como su título en el [ventana propiedades](/visualstudio/ide/reference/properties-window). También puede seleccionar varios controles y cambiar sus propiedades a la vez.

Para obtener más información sobre la **Editor de cuadro de diálogo**, vea cómo [agregar, modificar o eliminar controles](adding-editing-or-deleting-controls.md), [controles de diseño](../windows/arrangement-of-controls-on-dialog-boxes.md), y [definir Control de acceso y valores](../windows/defining-mnemonics-access-keys.md).

Para obtener más información sobre los controles y cuadros de diálogo, vea [clases de Control](../mfc/control-classes.md), [clases de cuadro de diálogo](../mfc/dialog-box-classes.md), y [estilos de barra de desplazamiento](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Los controles estándares disponibles en el **cuadro de herramientas** no tiene valor predeterminado de los eventos son:

|Nombre del control|Evento predeterminado|
|---|---|
|[Control de botón](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Control de casilla de verificación](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Control de cuadro combinado](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Control de edición](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Cuadro de grupo|(no aplicable)|
|[Control de cuadro de lista](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Control de botón de radio](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Control de texto estático](../mfc/reference/cstatic-class.md)|(no aplicable)|
|[Control de imagen](../mfc/reference/cpictureholder-class.md)|(no aplicable)|
|[Control Rich Edit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Control de barra de desplazamiento](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Para obtener más información sobre el uso de la **RichEdit 1.0** control con MFC, vea [con el Control RichEdit 1.0 con MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) y [ejemplos de Control de edición enriquecida](../mfc/rich-edit-control-examples.md).

El [controles comunes de Windows](../mfc/controls-mfc.md) disponibles en el **cuadro de herramientas** para proporcionar una mayor funcionalidad son:

|Nombre del control|Evento predeterminado|
|---|---|
|[Control deslizante](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Control de número](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Control de progreso](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Hot Key (control)](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Control de lista](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Control de árbol](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Control de pestaña](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Control de animación](../mfc/using-an-animation-control.md)|ACN_START|
|[Control de selector de hora de fecha](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Control de calendario mensual](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Control de dirección IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Control de cuadro combinado extendido](../mfc/creating-an-extended-combo-box-control.md)||
|Custom (control)|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Controles personalizados

El **Editor de cuadro de diálogo** le permite usar existente personalizados o controles de usuario en una plantilla de cuadro de diálogo.

> [!NOTE]
> Controles personalizados en este sentido no son debe confundirse con los controles ActiveX. Controles ActiveX se denominan controles personalizados OLE. Además, no confunda estos controles con los controles dibujados por el propietario de Windows.

Esta funcionalidad está diseñada para permitir el uso de controles distintos de los proporcionados por Windows. En tiempo de ejecución, el control está asociado con una clase de ventana (no es el mismo que una clase de C++). Una manera más común para realizar la misma tarea consiste en instalar cualquier control, como un control estático, en el cuadro de diálogo. A continuación, en tiempo de ejecución, en el [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funcione, quita el control y reemplazarlo con su propio control personalizado.

> [!NOTE]
> Esta es una técnica anterior. Hoy en día se recomienda en la mayoría de los casos a escribir un control ActiveX o una subclase de un control común de Windows.

Para estos controles personalizados, estará limitado a:

- Configuración de la ubicación en el cuadro de diálogo.

- Escriba un título.

- Identifica el nombre de la clase del control Windows dado que el código de aplicación debe registrar el control con este nombre.

- Escriba un valor hexadecimal de 32 bits que establece el estilo del control.

- Establecer el estilo extendido.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cuadros de diálogo](../windows/dialog-editor.md)<br/>

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->