---
title: Procedimiento Definir el Control de acceso y valores (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.combo
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
ms.openlocfilehash: c49913597f51ef231073b89d60ad9718b1113f44
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041489"
---
# <a name="how-to-define-control-access-and-values-c"></a>Procedimiento Definir el Control de acceso y valores (C++)

## <a name="tab-order"></a>Orden de tabulación

El orden de tabulación es el orden en que el **ficha** tecla mueve el foco de entrada de un control al siguiente en un cuadro de diálogo. Normalmente, el orden de tabulación se realiza de izquierda a derecha y de arriba a abajo en un cuadro de diálogo. Cada control tiene un **Tabstop** propiedad que determina si un control recibe el foco de entrada.

- Para establecer el foco de entrada para un control, en el [ventana propiedades](/visualstudio/ide/reference/properties-window), seleccione **True** o **False** en el **Tabstop** propiedad.

Incluso los controles que no tienen la **Tabstop** propiedad establecida en **True** deben formar parte del orden de tabulación, especialmente para los controles que no tienen títulos. Texto estático que contiene una clave de acceso para un control relacionado debe preceder inmediatamente al control relacionado en el orden de tabulación.

> [!NOTE]
> Si el cuadro de diálogo contiene controles que se superponen, el orden de tabulación se cambia la manera en que se muestran los controles. Controles que se proporcionan más adelante en el orden de tabulación se muestran siempre encima de los controles que se superponen que preceden a ellos en el orden de tabulación.

- Para ver el orden de tabulación para todos los controles, vaya al menú **formato** > **orden de tabulación**, o bien presione **Ctrl** + **d.**.

   Un número en la esquina superior izquierda de cada control muestra su lugar en el orden de tabulación.

- Para cambiar el orden de tabulación para todos los controles, vaya al menú **formato** > **orden de tabulación** y establezca el orden de tabulación seleccionando cada control en el orden que desee la **ficha** clave seguir.

- Para cambiar el orden de tabulación para dos o más controles, vaya al menú **formato** > **orden de tabulación**. Mantenga presionada la tecla el **Ctrl** clave y se selecciona el control donde empezar el cambio en el orden y suelte el **Ctrl** clave y seleccione los controles en el orden que desee la **ficha** clave a Siga desde ese punto.

   Por ejemplo, si desea cambiar el orden de los controles `7` a través de `9`, mantenga presionada la tecla **Ctrl**, a continuación, seleccione el control `6` primero.

- Para configurar un control específico en número `1`, o en primer lugar en el orden de tabulación, haga doble clic en el control.

> [!TIP]
> Una vez que escriba **orden de tabulación** modo, presione **Esc** o **ENTRAR** para salir **orden de tabulación** modo y deshabilitar la capacidad de cambiar el orden de tabulación.

## <a name="mnemonics-access-keys"></a>Teclas de acceso

Normalmente, los usuarios del teclado mueve el foco de entrada de un control a otro en un cuadro de diálogo con el **ficha** y **flecha** claves. Sin embargo, puede definir una clave de acceso (un nombre mnemotécnico o fácil de recordar) que permite a los usuarios elegir un control presionando una sola clave.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Para definir una tecla de acceso para un control con un título visible (botones de comando, casillas y botones de radio)

1. Seleccione el control en el cuadro de diálogo.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), en el **título** propiedad, escriba un nombre nuevo para el control, escriba una y comercial (`&`) delante de la letra que desee como tecla de acceso para ese control. Por ejemplo: `&Radio1`.

1. Presione **ENTRAR**.

   Aparece un subrayado en el título mostrado para indicar la clave de acceso, por ejemplo, **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Para definir una tecla de acceso para un control sin un título visible

1. Cree un título para el control mediante el uso de un **texto estático** en controlar la [cuadro de herramientas](/visualstudio/ide/reference/toolbox).

1. En el título de texto estático, escriba una y comercial (`&`) delante de la letra que desee como tecla de acceso.

1. Asegúrese de que el control de texto estático precede inmediatamente al control correspondiente en el orden de tabulación.

> [!NOTE]
> Todas las claves de acceso dentro de un cuadro de diálogo deben ser únicas. Para comprobar si las claves de acceso duplicadas, vaya al menú **formato** > **Comprobar teclas de acceso**.

## <a name="combo-box-values"></a>Valores de cuadro combinado

Puede agregar valores a un control de cuadro combinado siempre que tenga el **Editor de cuadro de diálogo** abrir.

> [!TIP]
> Es una buena idea agregar todos los valores al cuadro combinado *antes* tamaño en el cuadro de la **Editor de cuadro de diálogo**, o puede truncar el texto que debe aparecer en el control de cuadro combinado.

### <a name="to-enter-values-into-a-combo-box-control"></a>Para introducir valores en un control de cuadro combinado

1. Elija al cuadro combinado del control de cuadro, selecciónelo.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), desplácese hacia abajo hasta la **datos** propiedad.

   > [!NOTE]
   > Si se muestra propiedades agrupadas por tipo, **datos** aparece en el **Misc** propiedades.

1. Seleccione el área de valores de la **datos** propiedad y escriba los valores de los datos, separados por punto y coma.

   > [!NOTE]
   > No incluya espacios entre los valores, ya que podrían afectar al orden alfabético de la lista desplegable.

1. Presione **ENTRAR** cuando haya terminado de agregar valores.

Para obtener información sobre la ampliación de la parte desplegable de un cuadro combinado, vea [establecer el tamaño del cuadro combinado y su lista desplegable](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> No se puede agregar valores a los proyectos de Win32 mediante este procedimiento (la **datos** propiedad está atenuada para los proyectos de Win32). Dado que los proyectos de Win32 no tienen bibliotecas que agregar esta funcionalidad, debe agregar valores mediante programación a un cuadro combinado con un proyecto de Win32.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Para probar la apariencia de los valores en un cuadro combinado

1. Después de escribir valores en el **datos** propiedad, seleccione el **prueba** situado en la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

1. Pruebe a desplazarse por la lista de valores todo. Los valores aparecen exactamente como se escriben en el **datos** propiedad en el **propiedades** ventana. Hay ningún ortografía ni la comprobación de mayúsculas y minúsculas.

1. Presione **Esc** para volver a la **cuadro de diálogo** editor.

## <a name="radio-button-values"></a>Valores de botón de radio

Al agregar botones de radio a un cuadro de diálogo, tratarlos como un grupo estableciendo una **grupo** propiedad en el **propiedades** ventana para el primer botón en el grupo. Después, aparecerá un id. de control para ese botón de opción en el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), lo que le permite agregar una variable miembro para el grupo de botones de radio.

Puede tener más de un grupo de botones de radio en un cuadro de diálogo. Agregue cada grupo mediante el procedimiento siguiente.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Para agregar un grupo de botones de radio a un cuadro de diálogo

1. Seleccione el control de botón de radio en el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox) y elegir la ubicación en el cuadro de diálogo dónde desea colocar el control.

1. Repita el paso anterior para agregar tantos botones de radio como necesite. Asegúrese de que los botones de radio del grupo sean consecutivos en el orden de tabulación.

1. En la [Ventana Propiedades](/visualstudio/ide/reference/properties-window), establezca la propiedad **Grupo** del *primer* botón de radio en el orden de tabulación en **True**.

   Cambiar el **grupo** propiedad **True** agrega el estilo WS_GROUP a la entrada del botón en el cuadro de diálogo del script de recursos y se impide que el usuario puede seleccionar más de un botón de radio a la vez en el grupo de botones (si el usuario selecciona un botón, los demás miembros del grupo se ha desactivado).

   > [!NOTE]
   > Solo el primer botón de radio del grupo debe tener la propiedad **Grupo** establecida en **True**. Si dispone de otros controles que no forman parte del grupo de botones, establezca la **grupo** propiedad del primer control *que esté fuera del grupo* a **True** también. Puede identificar rápidamente el primer control fuera del grupo mediante el uso de **Ctrl**+**d.** para ver el orden de tabulación.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Para agregar una variable miembro para el grupo de botones de radio

1. Haga clic en el primer control de botón de radio en el orden de tabulación (el control dominante y el otro con el **grupo** propiedad establecida en **True**) y elija **agregar Variable**.

1. En el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md), active la casilla **Variable de control** y luego seleccione el botón de radio **Valor** .

   - En el cuadro **Nombre de variable** , escriba un nombre para la nueva variable miembro.

   - En el cuadro de lista **Tipo de variable** , seleccione **int** o escriba *int*.

   Ahora puede modificar el código para especificar qué botón de radio debe aparecer seleccionado. Por ejemplo, `m_radioBox1 = 0;` selecciona el primer botón de radio del grupo.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Administrar controles de cuadro de diálogo](controls-in-dialog-boxes.md)<br/>
[Cómo: Agregar, editar o eliminar controles](adding-editing-or-deleting-controls.md)<br/>
[Cómo: Controles de diseño](arrangement-of-controls-on-dialog-boxes.md)<br/>