---
title: Definición de Control de acceso y valores
ms.date: 11/04/2016
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
ms.openlocfilehash: 3a885ad57ba05304d51cb45d0b498d81ad37a148
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264860"
---
# <a name="defining-control-access-and-values"></a>Definición de Control de acceso y valores

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="change-the-tab-order-of-controls"></a>Cambiar el orden de tabulación de controles

El orden de tabulación es el orden en que el **ficha** tecla mueve el foco de entrada de un control al siguiente en un cuadro de diálogo. Normalmente, el orden de tabulación se realiza de izquierda a derecha y de arriba a abajo en un cuadro de diálogo. Cada control tiene un **Tabstop** propiedad que determina si un control recibe el foco de entrada.

### <a name="to-set-input-focus-for-a-control"></a>Para establecer el foco de entrada para un control

En el [ventana propiedades](/visualstudio/ide/reference/properties-window), seleccione **True** o **False** en el **Tabstop** propiedad.

Incluso los controles que no tienen la **Tabstop** propiedad establecida en **True** deben formar parte del orden de tabulación. Orden de tabulación es importante, por ejemplo, cuando se [definir teclas de acceso (teclas de acceso)](../windows/defining-mnemonics-access-keys.md) para los controles que no tienen títulos. Texto estático que contiene una clave de acceso para un control relacionado debe preceder inmediatamente al control relacionado en el orden de tabulación.

> [!NOTE]
> Si el cuadro de diálogo contiene controles que se superponen, el orden de tabulación se cambia la manera en que se muestran los controles. Controles que se proporcionan más adelante en el orden de tabulación se muestran siempre encima de los controles que se superponen que preceden a ellos en el orden de tabulación.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Para ver el orden de tabulación para todos los controles en un cuadro de diálogo

En el **formato** menú, seleccione **orden de tabulación**.

\- o -

- Presione **Ctrl** + **d**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Para cambiar el orden de tabulación para todos los controles en un cuadro de diálogo

1. En el **formato** menú, seleccione **orden de tabulación**.

   Un número en la esquina superior izquierda de cada control muestra su lugar en el orden de tabulación.

1. Establecer el orden de tabulación, haga clic en cada control en el orden que desee la **ficha** clave para seguir.

1. Presione **ENTRAR** para salir **orden de tabulación** modo.

   > [!TIP]
   > Una vez que escriba **orden de tabulación** modo, puede presionar **Esc** o **ENTRAR** para deshabilitar la capacidad de cambiar el orden de tabulación.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Para cambiar el orden de tabulación para dos o más controles

1. Desde el **formato** menú, elija **orden de tabulación**.

1. Especifique donde se iniciará el cambio en el orden. En primer lugar, mantenga presionada la **Ctrl** clave y seleccione el control, seleccione lo donde que desee cambiar el orden para comenzar.

   Por ejemplo, si desea cambiar el orden de los controles `7` a través de `9`, mantenga presionada la tecla **Ctrl**, a continuación, seleccione el control `6` primero.

   > [!NOTE]
   > Para configurar un control específico en número `1` (primero en el orden de tabulación), haga doble clic en el control.

1. Versión del **Ctrl** clave, a continuación, seleccione los controles en el orden que desee la **ficha** clave seguir desde ese punto.

1. Presione **ENTRAR** para salir **orden de tabulación** modo.

## <a name="define-mnemonics-access-keys"></a>Definir teclas de acceso

Normalmente, los usuarios del teclado mueve el foco de entrada de un control a otro en un cuadro de diálogo con el **ficha** y **flecha** claves. Sin embargo, puede definir una clave de acceso (un nombre mnemotécnico o fácil de recordar) que permite a los usuarios elegir un control presionando una sola clave.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Para definir una tecla de acceso para un control con un título visible (botones de comando, casillas y botones de radio)

1. Seleccione el control en el cuadro de diálogo.

2. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), en el **título** propiedad, escriba un nombre nuevo para el control, escriba una y comercial (`&`) delante de la letra que desee como tecla de acceso para ese control. Por ejemplo: `&Radio1`.

3. Presione **ENTRAR**.

   Aparece un subrayado en el título mostrado para indicar la clave de acceso, por ejemplo, **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Para definir una tecla de acceso para un control sin un título visible

1. Cree un título para el control mediante el uso de un **texto estático** en controlar la [cuadro de herramientas](/visualstudio/ide/reference/toolbox).

2. En el título de texto estático, escriba una y comercial (`&`) delante de la letra que desee como tecla de acceso.

3. Asegúrese de que el control de texto estático precede inmediatamente al control correspondiente en el orden de tabulación.

Todas las claves de acceso dentro de un cuadro de diálogo deben ser únicas.

### <a name="to-check-for-duplicate-access-keys"></a>Comprobar teclas de acceso duplicadas

1. En el **formato** menú, haga clic en **Comprobar teclas de acceso**.

## <a name="add-values-to-a-combo-box-control"></a>Agregar valores a un control de cuadro combinado

Puede agregar valores a un control de cuadro combinado siempre que tenga el **diálogo** editor abierto.

> [!TIP]
> Es una buena idea agregar todos los valores al cuadro combinado *antes* tamaño en el cuadro de la **diálogo** editor, o se puede truncar el texto que debe aparecer en el control de cuadro combinado.

### <a name="to-enter-values-into-a-combo-box-control"></a>Para introducir valores en un control de cuadro combinado

1. Seleccione el control de cuadro combinado haciendo clic en él.

1. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), desplácese hacia abajo hasta la **datos** propiedad.

   > [!NOTE]
   > Si se muestra propiedades agrupadas por tipo, **datos** aparece en el **Misc** propiedades.

1. Seleccione el área de valores de la **datos** propiedad y escriba los valores de los datos, separados por punto y coma.

   > [!NOTE]
   > No incluya espacios entre los valores porque podrían afectar al orden alfabético de la lista desplegable.

1. Presione **ENTRAR** cuando haya terminado de agregar valores.

Para obtener información sobre la ampliación de la parte desplegable de un cuadro combinado, vea [establecer el tamaño del cuadro combinado y su lista desplegable](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> No se puede agregar valores a los proyectos de Win32 mediante este procedimiento (la **datos** propiedad está atenuada para los proyectos de Win32). Dado que los proyectos de Win32 no tienen bibliotecas que agregar esta funcionalidad, debe agregar valores mediante programación a un cuadro combinado con un proyecto de Win32.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Para probar la apariencia de los valores en un cuadro combinado

Después de escribir valores en el **datos** propiedad, seleccione el **prueba** situado en la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Pruebe a desplazarse por la lista de valores todo. Los valores aparecen exactamente como se escriben en el **datos** propiedad en el **propiedades** ventana. Hay ningún ortografía ni la comprobación de mayúsculas y minúsculas.

   Presione **Esc** para volver a la **cuadro de diálogo** editor.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)