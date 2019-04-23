---
title: Cómo Crear un cuadro de diálogo (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: c5f026683881ba8e608bd00089879e0e2a7b4af2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036333"
---
# <a name="how-to-create-a-dialog-box-c"></a>Procedimiento Crear un cuadro de diálogo (C++)

La ubicación y el tamaño de un cuadro de diálogo de C++ y la ubicación y tamaño de los controles dentro de ella, se miden en unidades de cuadro de diálogo. Los valores de los controles individuales y el cuadro de diálogo aparecen en la esquina inferior derecha de la barra cuando seleccionarlas de estado de Visual Studio.

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Procedimientos

El **Editor de cuadro de diálogo** le permite:

### <a name="to-create-a-new-dialog-box"></a>Para crear un nuevo cuadro de diálogo

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic en su *.rc* de archivo y seleccione **Agregar recurso**.

1. En el **Agregar recurso** cuadro de diálogo, seleccione **diálogo** en el **tipo de recurso** lista y luego elija **New**.

   Si un signo más (**+**) aparece junto a la **diálogo** tipo de recurso, significa que están disponibles plantillas de cuadro de diálogo. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **New**.

   Se abre el cuadro de diálogo nuevo en el **Editor de cuadro de diálogo**.

También puede abrir cuadros de diálogo existentes en el editor de cuadro de diálogo para su edición.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Para crear un cuadro de diálogo que un usuario no puedan salir

Puede crear un cuadro de diálogo en tiempo de ejecución que un usuario no pueda salir. Este tipo de cuadro de diálogo es útil para inicios de sesión y para bloqueos de documentos o aplicaciones.

1. En el panel **Propiedades** para el cuadro de diálogo, establezca la propiedad **Menú del sistema** en **false**.

   Esta configuración deshabilita el menú de sistema del cuadro de diálogo y **cerrar** botón.

1. En el formulario del cuadro de diálogo, elimine los botones **Cancelar** y **Aceptar** .

   En tiempo de ejecución, un usuario no puede salir de un cuadro de diálogo modal que tenga estas características.

Para habilitar la comprobación de este tipo de cuadro de diálogo, la función de cuadro de diálogo de prueba detecta cuando **Esc** está presionado. **ESC** es también conocida como tecla virtual VK_ESCAPE. Independientemente de cómo el cuadro de diálogo está diseñado para comportarse en tiempo de ejecución, puede finalizar el modo de prueba presionando **Esc**.

> [!NOTE]
> Para aplicaciones MFC, para crear un cuadro de diálogo que los usuarios no puedan salir, debe invalidar el comportamiento predeterminado de `OnOK` y `OnCancel` porque si elimina los botones asociados, todavía se puede descartar el cuadro de diálogo presionando  **Escriba** o **Esc**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Para especificar la ubicación y tamaño de un cuadro de diálogo

Hay propiedades que puede establecer en el [ventana propiedades](/visualstudio/ide/reference/properties-window) para especificar dónde aparecerá un cuadro de diálogo en la pantalla.

- El valor booleano **Center** propiedad.

   Si establece el valor en **True**, el cuadro de diálogo siempre aparecerá en el centro de la pantalla. Si establece esta propiedad en **False**, a continuación, puede establecer el **XPos** y **YPos** propiedades.

- El **XPos** y **YPos** propiedades que se usan para definir explícitamente donde en la pantalla aparecerá el cuadro de diálogo.

   Estas propiedades de posición son valores de desplazamiento de la esquina superior izquierda del área de visualización, que se define como `{X=0, Y=0}`.

- El **Absolute Align** propiedad que afecta a la posición.

   Si **True**, las coordenadas son relativas a la pantalla. Si **False**, las coordenadas son relativas a la ventana del propietario del cuadro de diálogo.

### <a name="to-test-a-dialog-box"></a>Para probar un cuadro de diálogo

Cuando se está diseñando un cuadro de diálogo, se puede simular y probar su comportamiento en tiempo de ejecución sin compilar el programa. En este modo, se puede:

- Escribir texto, seleccionar opciones de listas de cuadro combinado, activar y desactivar opciones y elegir comandos.

- Probar el orden de tabulación.

- Probar la agrupación de controles, como botones de radio y casillas.

- Probar los métodos abreviados de teclado para los controles del cuadro de diálogo.

> [!NOTE]
> Las conexiones con el código del cuadro de diálogo realizadas mediante asistentes no se incluyen en la simulación.

Cuando se prueba un cuadro de diálogo, normalmente se muestra en una ubicación relativa a la ventana principal del programa. Si ha configurado el cuadro de diálogo **Absolute Align** propiedad **True**, muestra el cuadro de diálogo en una posición relativa a la esquina superior izquierda de la pantalla.

1. Cuando el **Editor de cuadro de diálogo** es la ventana activa, vaya al menú **formato** > **Probar cuadro de diálogo**.

1. Para finalizar la simulación, presione **Esc** o seleccione el **cerrar** botón en el cuadro de diálogo que está probando.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cuadros de diálogo](../windows/dialog-editor.md)<br/>
[Cómo: Administrar controles de cuadro de diálogo](../windows/controls-in-dialog-boxes.md)<br/>