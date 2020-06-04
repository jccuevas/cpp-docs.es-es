---
title: 'Cómo: definir el acceso y los valores deC++control ()'
ms.date: 02/15/2019
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: e782788832063e210356864e074c15e9ba3555f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160325"
---
# <a name="how-to-define-control-access-and-values-c"></a>Cómo: definir el acceso y los valores deC++control ()

## <a name="tab-order"></a>Orden de tabulación

El orden de tabulación es el orden en el que la tecla **Tab** mueve el foco de entrada de un control a otro dentro de un cuadro de diálogo. Normalmente, el orden de tabulación continúa de izquierda a derecha y de arriba abajo en un cuadro de diálogo. Cada control tiene una propiedad **TabStop** que determina si un control recibe el foco de entrada.

- Para establecer el foco de entrada de un control, en la [ventana Propiedades](/visualstudio/ide/reference/properties-window), seleccione **true** o **false** en la propiedad **TabStop** .

Incluso los controles que no tienen la propiedad **TabStop** establecida en **true** deben formar parte del orden de tabulación, especialmente en el caso de los controles que no tienen títulos. El texto estático que contiene una tecla de acceso para un control relacionado debe preceder inmediatamente al control relacionado en el orden de tabulación.

> [!NOTE]
> Si el cuadro de diálogo contiene controles superpuestos, cambiar el orden de tabulación puede cambiar la forma en que se muestran los controles. Los controles que se encuentran más adelante en el orden de tabulación siempre se muestran encima de los controles superpuestos que los preceden en el orden de tabulación.

- Para ver el orden de tabulación actual de todos los controles, vaya a **formato** de menú > **orden de tabulación**o presione **Ctrl** + **D**.

   Un número en la esquina superior izquierda de cada control muestra su lugar en el orden de tabulación actual.

- Para cambiar el orden de tabulación de todos los controles, vaya a **formato** de menú > **orden de tabulación** y establezca el orden de tabulación seleccionando cada control en el orden en el que desea que siga la tecla **Tab** .

- Para cambiar el orden de tabulación de dos o más controles, vaya a **formato** de menú > **orden de tabulación**. Mantenga presionada la tecla **Ctrl** y seleccione el control en el que se iniciará el cambio, suelte la tecla **Ctrl** y seleccione los controles en el orden en el que desea que la tecla **Tab** siga a partir de ese punto.

   Por ejemplo, si desea cambiar el orden de los controles `7` a través de `9`, mantenga presionada la **tecla Ctrl**y, a continuación, seleccione el control `6` primero.

- Para establecer un control específico para numerar `1`, o primero en el orden de tabulación, haga doble clic en el control.

> [!TIP]
> Una vez que escriba el modo de **orden de tabulación** , presione **ESC** o **entrar** para salir del modo de **orden de tabulación** y deshabilitar la capacidad de cambiar el orden de tabulación.

## <a name="mnemonics-access-keys"></a>Teclas de acceso

Normalmente, los usuarios de teclado mueven el foco de entrada de un control a otro en un cuadro de diálogo con la **pestaña** y las teclas de **Dirección** . Sin embargo, puede definir una tecla de acceso (un mnemotécnico o un nombre fácil de recordar) que permita a los usuarios elegir un control presionando una sola tecla.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Para definir una tecla de acceso para un control con un título visible (botones de inserción, casillas y botones de radio)

1. Seleccione el control en el cuadro de diálogo.

1. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), en la propiedad **título** , escriba un nuevo nombre para el control y escriba una y comercial (`&`) delante de la letra que desee como tecla de acceso para ese control. Por ejemplo, `&Radio1`.

1. Presione **Entrar**.

   Aparece un subrayado en el título que se muestra para indicar la tecla de acceso, por ejemplo, **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Para definir una tecla de acceso para un control sin un título visible

1. Cree un título para el control mediante un control de **texto estático** en el [cuadro de herramientas](/visualstudio/ide/reference/toolbox).

1. En el título de texto estático, escriba una y comercial (`&`) delante de la letra que desee usar como tecla de acceso.

1. Asegúrese de que el control de texto estático precede inmediatamente al control que etiqueta en el orden de tabulación.

> [!NOTE]
> Todas las claves de acceso dentro de un cuadro de diálogo deben ser únicas. Para comprobar si hay claves de acceso duplicadas, vaya a **formato** de menú > **Comprobar teclas**de acceso.

## <a name="combo-box-values"></a>Valores del cuadro combinado

Puede agregar valores a un control de cuadro combinado siempre que tenga abierto el **Editor de cuadros de diálogo** .

> [!TIP]
> Es una buena idea agregar todos los valores al cuadro combinado *antes* de ajustar el tamaño del cuadro en el **Editor de cuadros de diálogo**, o puede truncar el texto que debe aparecer en el control combinado.

### <a name="to-enter-values-into-a-combo-box-control"></a>Para especificar valores en un control de cuadro combinado

1. Seleccione el control de cuadro combinado.

1. En la [ventana Propiedades](/visualstudio/ide/reference/properties-window), desplácese hacia abajo hasta la propiedad **datos** .

   > [!NOTE]
   > Si va a mostrar las propiedades agrupadas por tipo, los **datos** aparecen en las propiedades **varias** .

1. Seleccione el área valor para la propiedad **datos** y escriba los valores de los datos, separados por punto y coma.

   > [!NOTE]
   > No incluya espacios entre los valores, ya que los espacios interfieren con el orden alfabético en la lista desplegable.

1. Presione **entrar** cuando termine de agregar valores.

Para obtener información sobre cómo ampliar la parte desplegable de un cuadro combinado, vea [establecer el tamaño del cuadro combinado y la lista](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)desplegable.

> [!NOTE]
> No se pueden agregar valores a los proyectos de Win32 mediante este procedimiento (la propiedad **datos** está atenuada para los proyectos Win32). Dado que los proyectos de Win32 no tienen bibliotecas que agreguen esta funcionalidad, debe agregar los valores a un cuadro combinado con un proyecto de Win32 mediante programación.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Para probar la apariencia de los valores de un cuadro combinado

1. Después de escribir los valores en la propiedad **datos** , seleccione el botón **probar** en la [barra de herramientas del editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

1. Intente desplazarse hacia abajo en toda la lista de valores. Los valores aparecen exactamente como se escriben en la propiedad **datos** de la ventana **propiedades** . No hay ninguna comprobación de mayúsculas o minúsculas.

1. Presione **ESC** para volver al editor de **cuadros de diálogo** .

## <a name="radio-button-values"></a>Valores de botón de radio

Al agregar botones de radio a un cuadro de diálogo, Tratelos como un grupo estableciendo una propiedad de **Grupo** en la ventana **propiedades** para el primer botón del grupo. Después, aparecerá un id. de control para ese botón de opción en el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), lo que le permite agregar una variable miembro para el grupo de botones de radio.

Puede tener más de un grupo de botones de radio en un cuadro de diálogo. Agregue cada grupo mediante el procedimiento siguiente.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Para agregar un grupo de botones de radio a un cuadro de diálogo

1. Seleccione el control de botón de radio en la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) y elija la ubicación en el cuadro de diálogo donde se colocará el control.

1. Repita el paso anterior para agregar tantos botones de radio como necesite. Asegúrese de que los botones de radio del grupo sean consecutivos en el orden de tabulación.

1. En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), establezca la propiedad **Grupo** del *primer* botón de radio en el orden de tabulación en **True**.

   Al cambiar la propiedad **Grupo** a **true** se agrega el estilo WS_GROUP a la entrada del botón en el objeto de cuadro de diálogo del script de recursos y se impide que el usuario seleccione más de un botón de radio a la vez en el grupo de botones (si el usuario selecciona un botón de radio, se desactivan los demás del grupo).

   > [!NOTE]
   > Solo el primer botón de radio del grupo debe tener la propiedad **Grupo** establecida en **True**. Si tiene controles adicionales que no forman parte del grupo de botones, establezca la propiedad **Grupo** del primer control *que se encuentra fuera del grupo* también en **true** . Puede identificar rápidamente el primer control fuera del grupo mediante **Ctrl**+**D** para ver el orden de tabulación.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Para agregar una variable miembro para el grupo de botones de radio

1. Haga clic con el botón secundario en el primer control de botón de radio en el orden de tabulación (el control dominante y el que tiene la propiedad de **Grupo** establecida en **true**) y elija **Agregar variable**.

1. En el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), active la casilla **Variable de control** y luego seleccione el botón de radio **Valor** .

   - En el cuadro **Nombre de variable** , escriba un nombre para la nueva variable miembro.

   - En el cuadro de lista **Tipo de variable** , seleccione **int** o escriba *int*.

   Ahora puede modificar el código para especificar qué botón de radio debe aparecer seleccionado. Por ejemplo, `m_radioBox1 = 0;` selecciona el primer botón de radio del grupo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Administrar controles del cuadro de diálogo](controls-in-dialog-boxes.md)<br/>
[Cómo: agregar, editar o eliminar controles](adding-editing-or-deleting-controls.md)<br/>
[Cómo: diseñar controles](arrangement-of-controls-on-dialog-boxes.md)<br/>
