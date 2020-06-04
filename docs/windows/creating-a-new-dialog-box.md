---
title: 'Cómo: crear un cuadro de diálogo (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: 3eae1aca53c40a33b8d120b02fdde8f68d58b723
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160430"
---
# <a name="how-to-create-a-dialog-box-c"></a>Cómo: crear un cuadro de diálogo (C++)

La ubicación y el tamaño de C++ un cuadro de diálogo, así como la ubicación y el tamaño de los controles que contiene, se miden en unidades de cuadro de diálogo. Los valores de los controles individuales y del cuadro de diálogo aparecen en la parte inferior derecha de la barra de estado de Visual Studio cuando se seleccionan.

> [!NOTE]
> Si el proyecto aún no contiene un archivo. rc, consulte [crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Procedimientos

El **Editor de cuadros de diálogo** le permite:

### <a name="to-create-a-new-dialog-box"></a>Para crear un nuevo cuadro de diálogo

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic con el botón secundario en el archivo *. RC* y seleccione **Agregar recurso**.

1. En el cuadro de diálogo **Agregar recurso** , seleccione cuadro de **diálogo** en la lista **tipo de recurso** y, a continuación, elija **nuevo**.

   Si aparece un signo más ( **+** ) junto al tipo de recurso de cuadro de **diálogo** , significa que están disponibles las plantillas de cuadro de diálogo. Seleccione el signo más para expandir la lista de plantillas, seleccione una plantilla y elija **nuevo**.

   El nuevo cuadro de diálogo se abre en el **Editor de cuadros de diálogo**.

También puede abrir los cuadros de diálogo existentes en el editor de cuadros de diálogo para su edición.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Para crear un cuadro de diálogo que un usuario no pueda salir

Puede crear un cuadro de diálogo en tiempo de ejecución que un usuario no pueda salir. Este tipo de cuadro de diálogo es útil para inicios de sesión y para bloqueos de documentos o aplicaciones.

1. En el panel **Propiedades** para el cuadro de diálogo, establezca la propiedad **Menú del sistema** en **false**.

   Esta configuración deshabilita el menú del sistema del cuadro de diálogo y el botón **cerrar** .

1. En el formulario del cuadro de diálogo, elimine los botones **Cancelar** y **Aceptar** .

   En tiempo de ejecución, un usuario no puede salir de un cuadro de diálogo modal que tenga estas características.

Para habilitar la prueba de este tipo de cuadro de diálogo, la función del cuadro de diálogo probar detecta cuándo se presiona **ESC** . **ESC** también se conoce como la clave virtual VK_ESCAPE. Independientemente de la forma en que el cuadro de diálogo esté diseñado para comportarse en tiempo de ejecución, puede finalizar el modo de prueba si presiona **ESC**.

> [!NOTE]
> En el caso de las aplicaciones MFC, para crear un cuadro de diálogo que los usuarios no puedan salir, debe invalidar el comportamiento predeterminado de `OnOK` y `OnCancel` porque, aunque elimine los botones asociados, todavía se puede descartar el cuadro de diálogo presionando **entrar** o **ESC**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Para especificar la ubicación y el tamaño de un cuadro de diálogo

Hay propiedades que puede establecer en la [ventana Propiedades](/visualstudio/ide/reference/properties-window) para especificar dónde aparecerá un cuadro de diálogo en la pantalla.

- Propiedad de **Centro** booleana.

   Si establece el valor en **true**, el cuadro de diálogo aparecerá siempre en el centro de la pantalla. Si establece esta propiedad en **false**, puede establecer las propiedades **XPOS** e **YPOS** .

- Las propiedades **XPOS** e **YPOS** que se usan para definir explícitamente dónde aparecerá el cuadro de diálogo.

   Estas propiedades de posición son valores de desplazamiento desde la esquina superior izquierda del área de visualización, que se define como `{X=0, Y=0}`.

- Propiedad de **alineación absoluta** que afecta a la posición.

   Si **es true**, las coordenadas son relativas a la pantalla. Si **es false**, las coordenadas son relativas a la ventana del propietario del cuadro de diálogo.

### <a name="to-test-a-dialog-box"></a>Para probar un cuadro de diálogo

Cuando se está diseñando un cuadro de diálogo, se puede simular y probar su comportamiento en tiempo de ejecución sin compilar el programa. En este modo, se puede:

- Escribir texto, seleccionar opciones de listas de cuadro combinado, activar y desactivar opciones y elegir comandos.

- Probar el orden de tabulación.

- Probar la agrupación de controles, como botones de radio y casillas.

- Probar los métodos abreviados de teclado para los controles del cuadro de diálogo.

> [!NOTE]
> Las conexiones con el código del cuadro de diálogo realizada mediante los asistentes no se incluyen en la simulación.

Cuando se prueba un cuadro de diálogo, normalmente se muestra en una ubicación relativa a la ventana principal del programa. Si ha establecido la propiedad de **alineación absoluta** del cuadro de diálogo en **true**, el cuadro de diálogo se muestra en una posición relativa a la esquina superior izquierda de la pantalla.

1. Cuando el **Editor de cuadros de diálogo** es la ventana activa, vaya a **formato** de menú > cuadro de **diálogo de prueba**.

1. Para finalizar la simulación, presione **ESC** o seleccione el botón **cerrar** en el cuadro de diálogo que está probando.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Editor de cuadros de diálogo](../windows/dialog-editor.md)<br/>
[Cómo: administrar controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
