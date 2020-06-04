---
title: Controles de cuadro deC++diálogo () | Microsoft Docs
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
ms.openlocfilehash: c79021387de2c8bc8f7f106a93797b7efb07d6df
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160416"
---
# <a name="dialog-box-controls-c"></a>Controles de cuadro deC++diálogo ()

Puede Agregar controles a un cuadro de diálogo mediante la pestaña **Editor de cuadros de diálogo** de la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) , que le permite elegir el control que desee y arrastrarlo hasta el cuadro de diálogo. De forma predeterminada, la ventana **cuadro de herramientas** está establecida en ocultar automáticamente. Aparece como una pestaña en el margen izquierdo de la solución cuando el **Editor de cuadros de diálogo** está abierto. Sin embargo, puede anclar la ventana **cuadro de herramientas** en posición seleccionando el botón **Ocultar automáticamente** en la esquina superior derecha de la ventana. Para obtener más información sobre cómo controlar el comportamiento de esta ventana, vea [Administración de ventanas](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

La manera más rápida de agregar controles a un cuadro de diálogo, cambiar la posición de los controles existentes o mover controles de un cuadro de diálogo a otro es usar el método de arrastrar y colocar. La posición del control se describe en una línea de puntos hasta que se coloca en el cuadro de diálogo. Cuando se agrega un control a un cuadro de diálogo con el método de arrastrar y colocar, el control recibe un alto estándar adecuado para ese tipo de control.

Cuando se agrega un control a un cuadro de diálogo o se vuelve a colocar, su ubicación final se puede determinar mediante guías o márgenes, o si la cuadrícula de diseño está activada.

Una vez que haya agregado un control al cuadro de diálogo, puede cambiar las propiedades, como su título, en la [ventana Propiedades](/visualstudio/ide/reference/properties-window). También puede seleccionar varios controles y cambiar sus propiedades todos a la vez.

Para obtener más información sobre **el editor de cuadros de diálogo**, vea cómo [Agregar, editar o eliminar controles](adding-editing-or-deleting-controls.md), [diseñar controles](../windows/arrangement-of-controls-on-dialog-boxes.md)y [definir el acceso a controles y los valores](../windows/defining-mnemonics-access-keys.md).

Para obtener más información sobre los controles y cuadros de diálogo, vea [clases de control](../mfc/control-classes.md), clases de [cuadro de diálogo](../mfc/dialog-box-classes.md)y [estilos de barra de desplazamiento](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Los controles estándar disponibles en el **cuadro de herramientas** con eventos predeterminados son:

|Nombre del control|Evento predeterminado|
|---|---|
|[Button (control)](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Control de casilla](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Control de cuadro combinado](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Control de edición](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Cuadro de grupo|(no aplicable)|
|[Control de cuadro de lista](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Control de botón de radio](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Control de texto estático](../mfc/reference/cstatic-class.md)|(no aplicable)|
|[Control de imagen](../mfc/reference/cpictureholder-class.md)|(no aplicable)|
|[Control Rich Edit 2,0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Control de barra de desplazamiento](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Para obtener más información sobre el uso del control **richedit 1,0** con MFC, vea [usar el control RICHEDIT 1,0 con MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) y [ejemplos de controles Rich Edit](../mfc/rich-edit-control-examples.md).

Los [controles comunes de Windows](../mfc/controls-mfc.md) disponibles en el **cuadro de herramientas** para proporcionar una mayor funcionalidad son:

|Nombre del control|Evento predeterminado|
|---|---|
|[Control deslizante](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Control de número](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Control de progreso](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Control de tecla de acceso rápido](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Control de lista](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Control de árbol](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Control de pestaña](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Animation (control)](../mfc/using-an-animation-control.md)|ACN_START|
|[Control selector de fecha y hora](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Month Calendar (control)](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Control de direcciones IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Control de cuadro combinado extendido](../mfc/creating-an-extended-combo-box-control.md)||
|Custom (control)|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Controles personalizados

El **Editor de cuadros de diálogo** permite usar controles personalizados o de usuario existentes en una plantilla de cuadro de diálogo.

> [!NOTE]
> En este sentido, los controles personalizados no se deben confundir con los controles ActiveX. Los controles ActiveX a veces se denominaban controles personalizados OLE. Además, no confunda estos controles con los controles dibujados por el propietario en Windows.

Esta funcionalidad está pensada para permitirle usar controles distintos de los proporcionados por Windows. En tiempo de ejecución, el control está asociado a una clase de ventana (no es igual C++ que una clase). Una manera más común de realizar la misma tarea es instalar cualquier control, como un control estático, en el cuadro de diálogo. A continuación, en tiempo de ejecución, en la función [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) , quite ese control y reemplácelo por su propio control personalizado.

> [!NOTE]
> Se trata de una técnica antigua. En la actualidad, en la mayoría de los casos se recomienda escribir un control ActiveX o una subclase de un control común de Windows.

Para estos controles personalizados, está limitado a:

- Establecer la ubicación en el cuadro de diálogo.

- Escribir un título.

- Identificar el nombre de la clase de Windows del control, ya que el código de la aplicación debe registrar el control por este nombre.

- Escribir un valor hexadecimal de 32 bits que establezca el estilo del control.

- Establecer el estilo extendido.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Editor de cuadros de diálogo](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
