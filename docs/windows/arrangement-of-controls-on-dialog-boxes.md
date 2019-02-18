---
title: Cómo Organizar los controles (C++) | Microsoft Docs
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: d9bd73c9cc81b113f222bbc090c62200c93554b2
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336636"
---
# <a name="how-to-arrange-controls-c"></a>Cómo Organizar los controles (C++)

El **diálogo** editor proporciona herramientas de diseño que alinean y ajustar automáticamente el tamaño de controles. Para la mayoría de las tareas, puede usar el [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Todos los **Editor de cuadro de diálogo** comandos de la barra de herramientas también están disponibles en el **formato** menú y la mayoría tiene [teclas de método abreviado](../windows/accelerator-keys-for-the-dialog-editor.md).

Muchos comandos de diseño para los cuadros de diálogo están disponibles solo cuando se selecciona más de un control. Puede seleccionar un control único o varios controles, y cuando se selecciona más de un control, es el primero de ellos que selecciona de forma predeterminada el control "principal". Para obtener información sobre la selección de controles y el control dominante, vea [seleccionar controles](../windows/selecting-controls.md).

La ubicación, alto y ancho del control actual se muestran en la esquina inferior derecha de la barra de estado. Cuando se selecciona el cuadro de diálogo completa, la barra de estado muestra la posición del cuadro de diálogo como un todo y su alto y ancho.

## <a name="guides-and-grids"></a>Guías y cuadrículas

Puede organizar los controles de cuadros de diálogo con el **diálogo** editor en uno de tres estados diferentes:

- Con las guías y márgenes en (valor predeterminado)

- Con la cuadrícula de diseño en

- Sin ninguna característica de ajuste o alineación

El [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) contiene botones que controlan el estado. Para cambiar el estado, seleccione el icono adecuado. También puede cambiar el estado mediante el uso de la **configuración de la guía** comando el **formato** menú.

El **configuración de la guía** cuadro de diálogo tiene las siguientes propiedades:

|Property|Descripción|
|---|---|
|**Guías de diseño**|Muestra la configuración de las guías de diseño.|
|**Ninguno**|Oculta las herramientas de diseño.|
|**Reglas y guías**|Cuando se habilita, agrega reglas a las herramientas de diseño; las guías se pueden colocar en las reglas. Las guías predeterminadas son los márgenes, que se pueden mover arrastrando. Seleccione las reglas para ubicar a una guía. Los controles "ajustarán" a las guías cuando se mueven los controles a través o junto a ellos. Los controles también se mueven con una guía de una vez que se adjuntan. Cuando un control está asociado a una guía en cada lado y se mueve una guía, el control cambia de tamaño.|
|**Grid**|Crea una cuadrícula de diseño. Nuevos controles se alinearán automáticamente a la cuadrícula.|
|**Espaciado de cuadrícula**|Muestra la configuración para el espaciado de cuadrícula en unidades de cuadro de diálogo (DLU).|
|**Ancho: DLU**|Establece el ancho de la cuadrícula de diseño en DLU. Una DLU horizontal es el ancho promedio de la fuente del cuadro de diálogo dividido por cuatro.|
|**Alto: DLU**|Establece el alto de la cuadrícula de diseño en DLU. Una vertical equivale al alto medio de la fuente del cuadro de diálogo dividido por ocho.|

### <a name="to-create-edit-and-delete-guides-and-margins"></a>Para crear, editar y eliminar guías y márgenes

Si está moviendo los controles, agregar controles o reorganizar un diseño actual, las guías pueden ayudarle a alinear los controles con precisión dentro de un cuadro de diálogo. Las guías aparecen en azul las líneas de puntos en el cuadro de diálogo que aparece en el editor y flechas correspondientes en las reglas en la parte superior y en el lado izquierdo de la **diálogo** editor.

Cuando se crea un cuadro de diálogo, se proporcionan cuatro márgenes. Los márgenes son guías modificadas, que aparecen como líneas de puntos azules. Consulte las siguientes acciones:

- Para crear a una guía, dentro de la regla, seleccione una vez para crear a una guía. (Un solo clic crea una nueva guía; hacer doble clic en los lanzamientos de la **configuración de la guía** cuadro de diálogo en el que puede especificar la configuración de la guía.)

- Para establecer a una guía, en el cuadro de diálogo, seleccione a la guía y arrástrelo a una nueva posición. (También puede seleccionar la flecha de la regla para arrastrar a la guía asociada.) Las coordenadas de la guía se muestran en la barra de estado en la parte inferior de la ventana y en la regla. Mueva el puntero sobre la flecha de la regla para mostrar la posición exacta de la guía.

- Para mover los márgenes, arrastre el margen a la nueva posición. Para que desaparezca un margen, mueva el margen a una posición cero. Para devolver el margen, coloque el puntero sobre el margen de la posición cero y mueva el margen a posición.

- Para eliminar a una guía, arrastre a la guía fuera del cuadro de diálogo o la flecha correspondiente fuera de la regla.

### <a name="to-align-controls-on-a-guide"></a>Para alinear controles en una guía

Los controladores de tamaño de los controles se ajustan a las guías cuando se mueven los controles y las guías se ajustan a los controles, si no hay ningún control previamente ajustados a la guía. Cuando se mueve una guía, también se mueven los controles que se ajustan a él. Controles ajustados a más de una guía cambian de tamaño cuando se mueve una de las guías.

Las marcas de graduación en las reglas que determinan el espaciado de las guías y los controles se definen mediante unidades de cuadro de diálogo (DLU). Las unidades se basan en el tamaño de la fuente del cuadro de diálogo, normalmente de 8 puntas MS Shell Dlg. Una DLU horizontal es el ancho promedio de la fuente del cuadro de diálogo dividido por cuatro. Una vertical equivale al alto medio de la fuente dividido por ocho.

#### <a name="to-size-a-group-of-controls-with-guides"></a>Para cambiar el tamaño de un grupo de controles con guías

1. Ajustar un lado del control (o controles) a una guía.

1. Arrastre a una guía para el otro lado del control (o controles).

   Si es necesario con varios controles, cambiar el tamaño de cada uno que se ajuste a la segunda guía.

1. Mueva una de las guías para cambiar el tamaño del control (o controles).

#### <a name="to-change-the-intervals-of-the-tick-marks"></a>Cambiar los intervalos de las marcas de graduación

Desde el **formato** menú, elija **configuración de la guía**, a continuación, en el **espaciado de cuadrícula** , especifique un nuevo ancho y alto en DLU.

### <a name="to-disable-guides"></a>Deshabilitar guías

Puede usar las teclas especiales junto con el mouse para deshabilitar el efecto de las guías de ajuste. Mediante el **Alt** clave deshabilita los efectos de ajuste de la Guía seleccionada. Mover una guía con el **MAYÚS** clave impide que los controles ajustados mover con la guía.

- Para deshabilitar el efecto de ajuste de las guías, arrastre el control mientras mantiene presionada la **Alt** clave.

- Para mover guías sin mover los controles ajustados, arrastre la guía mientras mantiene presionada la **MAYÚS** clave.

- Para desactivar las guías, desde el **formato** menú, elija **configuración de la guía**. A continuación, en el **configuración de la guía** cuadro de diálogo **las guías de diseño**, seleccione **ninguno**.

   > [!NOTE]
   > También puede haga doble clic en la barra de la regla para tener acceso a la **configuración de la guía** cuadro de diálogo.

> [!TIP]
> Es un acceso directo para desactivar las guías en el **formato** menú, seleccione **Alternar guías**.

### <a name="to-modify-the-layout-grid"></a>Para modificar la cuadrícula de diseño

Cuando se coloca u organizar controles en un cuadro de diálogo, puede usar la cuadrícula de diseño para una ubicación más precisa. Cuando la cuadrícula está activada, los controles aparecen en "Ajustar a" las líneas de puntos de la cuadrícula como si estuvieran imantados. Puede activar y desactivar la esta característica "Ajustar a la cuadrícula" y cambiar el tamaño de las celdas de cuadrícula de diseño.

- Para activar la cuadrícula de diseño o desactivar, desde el **formato** menú, elija **configuración de la guía**, a continuación, active o desactive el **cuadrícula** botón.

   Todavía puede controlar la cuadrícula en persona **diálogo** ventanas del editor mediante el **Alternar cuadrícula** situado en la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Para cambiar el tamaño de la cuadrícula de diseño, desde el **formato** menú, elija **configuración de la guía**, a continuación, escriba el alto y ancho en DLU para las celdas de la cuadrícula. El alto o ancho mínimo es de 4 DLU.

## <a name="select-controls"></a>Seleccionar controles

Seleccione los controles de tamaño, alinear, mover, copiar, o eliminarlas y, a continuación, complete la operación que desee. En la mayoría de los casos, deberá seleccionar más de un control para utilizar las herramientas de ajuste de tamaño y alineación de la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Cuando se selecciona un control, tiene un borde sombreado alrededor de ella con sólidos (activos) o "cuadros de tamaño" hueco (inactivo) pequeños cuadros que aparecen en el borde de selección. Cuando se seleccionan varios controles, el control dominante tiene controladores de tamaño sólido y todos los controles seleccionados tienen controladores de tamaño hueco.

Al cambiar el tamaño o alinear varios controles, el **diálogo** editor usa el "control dominante" para determinar cómo los otros controles o un tamaño alineados. De forma predeterminada, el control dominante es el primer control seleccionado.

### <a name="to-select-controls"></a>Seleccionar controles

1. En el [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox), seleccione el **puntero** herramienta.

1. Para hacer su selección, utilice uno de los pasos siguientes:

   - Arrastre el puntero para dibujar un cuadro de selección alrededor de los controles que desea seleccionar en el cuadro de diálogo. Al soltar el botón del mouse, todos los controles internos y se selecciona el cuadro de selección de intersección.

   - Mantenga presionada la **MAYÚS** clave y seleccione los controles que le gustaría incluir en la selección.

   - Mantenga presionada la **Ctrl** clave y seleccione los controles que le gustaría incluir en la selección.

1. Para agregar o quitar un control de grupo de controles seleccionados, mantenga presionada la **MAYÚS** clave y se selecciona el control que desea agregar o quitar.

> [!NOTE]
> Manteniendo presionada la tecla el **Ctrl** clave y seleccione un control dentro de una selección hará que controlan el control dominante en esa selección.

### <a name="to-select-a-dominant-control"></a>Para seleccionar un control dominante

- Para especificar el control dominante, mantenga presionada la **Ctrl** clave y se selecciona el control que desea usar para influir en el tamaño o la ubicación de otros controles *primera*.

- Para cambiar el control dominante, anule la selección actual mediante la selección fuera de todos los controles seleccionados actualmente y repita el procedimiento anterior, seleccione primero un control diferente.

> [!NOTE]
> Los controladores de tamaño del control dominante son sólidos, mientras que los de los controles subordinados serán huecos. Todos los aún más el cambio de tamaño o la alineación se basa en el control dominante.

## <a name="size-controls"></a>Tamaño de los controles

Use los controladores de tamaño para cambiar el tamaño de un control. Cuando el puntero se coloca en un controlador de tamaño, cambia la forma para indicar las instrucciones que aparecen en el que se puede cambiar el tamaño del control. Controladores de tamaño Active son sólidas y si un controlador de tamaño está vacío, el control no puede cambiarse a lo largo de ese eje.

> [!TIP]
> También puede cambiar el tamaño de un control ajustando el control a las guías o los márgenes o moviendo un control ajustado y guía fuera de otra.

### <a name="to-size-a-control"></a>Para cambiar el tamaño de un control

1. Seleccione el control.

1. Arrastre los controladores de tamaño para cambiar el tamaño del control:

   - Controladores de tamaño en la parte superior y cambiar el tamaño horizontal o vertical.

   - Controladores de tamaño en las esquinas cambiar el tamaño horizontal y vertical.

   > [!TIP]
   > Puede cambiar el tamaño la unidad de control de un cuadro de diálogo (DLU) a la vez, mantenga presionada la **MAYÚS** clave y usar el **derecha** y **hacia abajo** teclas de dirección.

> [!TIP]
> Para cambiar automáticamente el tamaño de un control para ajustar el texto dentro de ella, abra el **formato** menú o haga clic en el control y elija **tamaño al contenido**.

### <a name="to-make-controls-the-same-size"></a>Para que los controles del mismo tamaño

Puede cambiar el tamaño de un grupo de controles en función del tamaño del control principal.

1. Seleccione los controles que desee cambiar el tamaño.

   El control seleccionado en primer lugar de la serie es el control dominante. El tamaño final de los controles en el grupo depende del tamaño del control principal.

1. Desde el **formato** menú, elija **Igualar tamaño**, a continuación, elija **ambos**, **alto**, o **ancho**.

### <a name="combo-box"></a>Cuadro combinado

Puede ajustar el tamaño de un cuadro combinado cuando se agrega al cuadro de diálogo. También puede especificar el tamaño del cuadro de lista desplegable. Para obtener más información, consulte [agregar valores a un Control de cuadro combinado](../windows/adding-values-to-a-combo-box-control.md).

1. Seleccione el botón de flecha de lista desplegable situado a la derecha del cuadro combinado.

   ![Flecha de un cuadro combinado en un proyecto MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   El contorno del control cambia para mostrar el tamaño del cuadro combinado con el área de la lista desplegable extendido.

1. Use el controlador de tamaño inferior para cambiar el tamaño inicial del área de la lista desplegable.

   ![Cuadro combinado&#45;ajuste de tamaño de cuadro en un proyecto MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Seleccione la flecha desplegable para cerrar la parte de la lista desplegable del cuadro combinado.

### <a name="horizontal-scroll-bar"></a>Barra de desplazamiento horizontal

Cuando se agrega un cuadro de lista con una barra de desplazamiento horizontal para un cuadro de diálogo mediante clases de MFC, la barra de desplazamiento no aparecerá automáticamente en la aplicación.

Establecer un ancho máximo para el elemento más amplio mediante una llamada a [CListBox:: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) en el código. Establecer este valor, la barra de desplazamiento no aparecerá, incluso cuando los elementos del cuadro de lista son más amplio que el cuadro.

## <a name="align-controls"></a>Alinear controles

1. Seleccione los controles que desee alinear. Asegúrese de seleccionar el control que se va a ser dominante en primer lugar o establecerlo el control dominante antes de ejecutar la alineación o ajustar el tamaño de comando.

   La posición final del grupo de controles depende de la posición del control principal.

1. Desde el **formato** menú, elija **alinear**y, a continuación, elija una de las alineaciones siguientes:

   |Alineación|Descripción|
   |-----|-----------|
   |`Lefts`|Alinea los controles seleccionados a lo largo de los lados izquierdos.|
   |`Centers`|Alinea los controles seleccionados horizontalmente a lo largo de sus puntos centrales.|
   |`Rights`|Alinea los controles seleccionados a lo largo de los lados derecho.|
   |`Tops`|Alinea los controles seleccionados por sus bordes superiores.|
   |`Middles`|Alinea los controles seleccionados verticalmente a lo largo de sus puntos medios.|
   |`Bottoms`|Alinea los controles seleccionados a lo largo de su borde inferior.|

### <a name="to-even-spacing-between-controls"></a>Incluso el espaciado entre controles

El **diálogo** editor le permite a los controles del espacio uniformemente entre los controles más externos seleccionados.

1. Seleccione los controles que desee reorganizar.

1. Desde el **formato** menú, elija **espaciar uniformemente**y, a continuación, elija una de las alineaciones siguientes:

   |Espaciado|Descripción|
   |---|---|
   |`Across`|Controles de espacio uniformemente entre el extremo izquierdo y el extremo derecho control seleccionado.|
   |`Down`|Controles de espacio uniformemente entre el primer y el más bajo control seleccionado.|

### <a name="to-center-controls"></a>Para centrar controles

1. Seleccione el control o controles que desea reorganizar.

1. Desde el **formato** menú, elija **centrar en el cuadro de diálogo**y, a continuación, elija una de las distribuciones siguientes:

   |Organización|Descripción|
   |---|---|
   |`Vertical`|Centrar controles verticalmente en el cuadro de diálogo.|
   |`Horizontal`|Centrar controles horizontalmente en el cuadro de diálogo.|

### <a name="to-arrange-push-buttons"></a>Organizar botones de comando

1. Seleccione uno o varios botones de comando.

1. Desde el **formato** menú, elija **organizar botones**y, a continuación, elija una de las distribuciones siguientes:

   |Organización|Descripción|
   |---|---|
   |`Right`|Alinea los botones de inserción en el borde derecho del cuadro de diálogo.|
   |`Bottom`|Alinea los botones de inserción en el borde inferior del cuadro de diálogo.|

   Si selecciona un control que no sea un botón de comando, su posición no se ve afectada.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)