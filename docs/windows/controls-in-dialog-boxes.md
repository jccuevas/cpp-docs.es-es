---
title: Controles de cuadros de diálogo (C++) | Microsoft Docs
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
ms.openlocfilehash: 6360491ebb4478ee4ce22115eced7ed672866565
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336519"
---
# <a name="controls-in-dialog-boxes-c"></a>Controles de cuadros de diálogo (C++)

Puede agregar controles a un cuadro de diálogo mediante la [pestaña del cuadro de diálogo Editor](../windows/dialog-editor-tab-toolbox.md) en el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox), que le permite elegir el control que desee y arrástrelo hasta el cuadro de diálogo. De forma predeterminada, la ventana de cuadro de herramientas se establece en la opción Ocultar automáticamente. Aparece como una pestaña en el margen izquierdo de la solución cuando se abre el editor de cuadro de diálogo. Sin embargo, puede anclar el **cuadro de herramientas** ventana a su posición, haga clic en el **Ocultar automáticamente** botón en la esquina superior derecha de la ventana. Para obtener más información sobre cómo controlar el comportamiento de esta ventana, consulte [administración de ventanas](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

La manera más rápida de agregar controles a un cuadro de diálogo, volver a colocar los controles existentes o mover los controles de cuadro de diálogo de uno a otro, es usar el método de arrastrar y colocar. La posición del control se muestra en una línea de puntos hasta que se coloca en el cuadro de diálogo. Al agregar un control a un cuadro de diálogo con el método de arrastrar y colocar, el control tiene un alto estándar adecuado para ese tipo de control.

Al agregar un control a un cuadro de diálogo o cambia la posición, su ubicación final puede verse determinado por las guías o los márgenes, o si tiene activada la cuadrícula de diseño.

Una vez haya agregado un control al cuadro de diálogo, puede cambiar las propiedades como su título en el [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede seleccionar varios controles y cambiar sus propiedades a la vez.

- [Cómo: Agregar, editar o eliminar los controles](adding-editing-or-deleting-controls.md)

- [Cómo: Organizar controles](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [Cómo: Definir el Control de acceso y valores](../windows/defining-mnemonics-access-keys.md)

Los controles estándares disponibles en el **cuadro de herramientas** no tiene valor predeterminado de los eventos son:

|Nombre del control|Evento predeterminado|
|---|---|
|[Control de botón](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Control de casilla de verificación](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Control de cuadro combinado](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Control de edición](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Cuadro de grupo|(No aplicable)|
|[Control de cuadro de lista](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Control de botón de radio](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Control de texto estático](../mfc/reference/cstatic-class.md)|(No aplicable)|
|[Control de imagen](../mfc/reference/cpictureholder-class.md)|(No aplicable)|
|[Control Rich Edit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Control de barra de desplazamiento](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

Para obtener más información sobre el uso de la **RichEdit 1.0** control con MFC, vea [con el Control RichEdit 1.0 con MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) y [ejemplos de Control de edición enriquecida](../mfc/rich-edit-control-examples.md).

El [controles comunes de Windows](../mfc/controls-mfc.md) disponibles en el **cuadro de herramientas** ofrecen una mayor funcionalidad en la aplicación. Son los siguientes:

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

Para obtener más información, consulte [clases de Control](../mfc/control-classes.md), [clases de cuadro de diálogo](../mfc/dialog-box-classes.md), y [estilos de barra de desplazamiento](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

## <a name="custom-controls"></a>Controles personalizados

El editor de cuadro de diálogo permite usar existente "custom" o "" controles de usuario en una plantilla de cuadro de diálogo.

> [!NOTE]
> Controles personalizados en este sentido no son debe confundirse con los controles ActiveX. Controles ActiveX se denominan controles personalizados OLE. Además, no confunda estos controles con los controles dibujados por el propietario de Windows.

Esta funcionalidad está diseñada para permitir el uso de controles distintos de los proporcionados por Windows. En tiempo de ejecución, el control está asociado con una clase de ventana (no es el mismo que una clase de C++). Una manera más común para realizar la misma tarea consiste en instalar cualquier control, como un control estático, en el cuadro de diálogo. A continuación, en tiempo de ejecución, en el [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funcione, quita el control y reemplazarlo con su propio control personalizado.

Esta es una técnica anterior. Hoy en día se recomienda en la mayoría de los casos a escribir un control ActiveX o una subclase de un control común de Windows.

Para estos controles personalizados, estará limitado a:

- Configuración de la ubicación en el cuadro de diálogo.

- Escriba un título.

- Que identifica el nombre de clase de Windows del control (el código de aplicación debe registrar el control con este nombre).

- Escriba un valor hexadecimal de 32 bits que establece el estilo del control.

- Establecer el estilo extendido.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Agregar controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)<br/>
[Controles](../mfc/controls-mfc.md)<br/>