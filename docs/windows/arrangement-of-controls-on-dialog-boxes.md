---
title: 'Cómo: diseñar controles (C++) | Microsoft Docs'
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
ms.openlocfilehash: ee732cfb414f011e95edbbb57b218d81179d44f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168582"
---
# <a name="how-to-layout-controls-c"></a>Cómo: diseñar controles (C++)

El **Editor de cuadros de diálogo** proporciona herramientas de diseño que alinean y ajustan el tamaño de los controles automáticamente. Para la mayoría de las tareas, puede usar la [barra de herramientas del editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md). Todos los comandos de la barra de herramientas del **Editor de cuadros de diálogo** también están disponibles en el menú **formato** y la mayoría tienen [teclas de método abreviado](../windows/accelerator-keys-for-the-dialog-editor.md).

Muchos comandos de diseño para los cuadros de diálogo solo están disponibles cuando se selecciona más de un control. Puede seleccionar un solo control o varios controles y, cuando se selecciona más de un control, el primero que seleccione es el control dominante de forma predeterminada.

La ubicación, el alto y el ancho del control actual se muestran en la esquina inferior derecha de la barra de estado. Cuando se selecciona el cuadro de diálogo completo, la barra de estado muestra la posición del cuadro de diálogo en su conjunto, así como su alto y ancho.

## <a name="arrange-controls"></a>Organizar controles

Puede organizar los controles en los cuadros de diálogo con el editor de cuadros de **diálogo** en uno de tres Estados diferentes:

- Con las guías y los márgenes activado, establezca como predeterminado.

- Con la cuadrícula de diseño en.

- Sin características de ajuste o alineación.

La [barra de herramientas del editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) contiene botones que controlan el estado.

- Para cambiar el estado, seleccione el icono adecuado o vaya a **formato** de menú > **configuración**de la guía.

El cuadro de diálogo Configuración de la **Guía** tiene las siguientes propiedades:

|Propiedad|Descripción|
|---|---|
|**Guías de diseño**|Muestra la configuración de las guías de diseño.|
|**None**|Oculta las herramientas de diseño.|
|**Reglas y guías**|Cuando está habilitada, agrega reglas a las herramientas de diseño y permite que las guías se coloquen en las reglas. Las guías predeterminadas son los márgenes.|
|**Grid**|Crea una cuadrícula de diseño. Los nuevos controles se alinearán automáticamente con la cuadrícula.|
|**Espaciado de cuadrícula**|Muestra la configuración del espaciado de cuadrícula en unidades del cuadro de diálogo (DLU).|
|**Ancho: DLU**|Establece el ancho de la cuadrícula de diseño en DLU. Una DLU horizontal es el ancho medio de la fuente del cuadro de diálogo dividido entre 4.|
|**Alto: DLU**|Establece el alto de la cuadrícula de diseño en DLU. Un DLU vertical es el alto medio de la fuente del cuadro de diálogo dividido entre 8.|

### <a name="guides-and-margins"></a>Guías y márgenes

Tanto si está moviendo controles, agregando controles o reorganizando un diseño, guías y márgenes actuales pueden ayudarle a alinear los controles con precisión dentro de un cuadro de diálogo.

Cuando se crea un cuadro de diálogo, se proporcionan cuatro guías modificadas denominadas márgenes y aparecen como líneas de puntos azules.

- Para mover los márgenes, arrastre el margen hasta la nueva posición.

- Para que un margen desaparezca, mueva el margen a una posición de cero.

- Para devolver el margen, coloque el puntero sobre la posición cero del margen y mueva el margen a la posición.

Las guías aparecen como líneas de puntos azules en el cuadro de diálogo que se muestra en el editor y las flechas correspondientes en las reglas de la parte superior y a lo largo del lado izquierdo del **Editor de cuadros de diálogo**. Los controladores de tamaño de los controles se ajustan a las guías cuando se mueven los controles y las guías se ajustan a los controles si no hay ningún control previamente ajustado a la guía. Cuando se mueve una guía, los controles que se ajustan a él también se mueven. Los controles ajustados a más de una guía cambian de tamaño cuando se mueve una de las guías.

- Para crear una guía dentro de la regla, seleccione una vez para crear una guía o haga doble clic para abrir el cuadro de diálogo Configuración de la **Guía** , donde puede especificar la configuración de la guía.

- Para establecer una guía en el cuadro de diálogo, seleccione la guía y arrástrela hasta una nueva posición, o bien seleccione la flecha en la regla para arrastrar la guía asociada.

   Las coordenadas de la guía se muestran en la barra de estado en la parte inferior de la ventana y en la regla o mueven el puntero sobre la flecha en la regla para mostrar la posición exacta de la guía.

- Para eliminar una guía, arrastre la guía fuera del cuadro de diálogo o arrastre la flecha correspondiente hacia fuera de la regla.

Las marcas de graduación de las reglas que determinan el espaciado de las guías y los controles se definen mediante unidades de cuadro de diálogo (DLU). Un DLU se basa en el tamaño de la fuente del cuadro de diálogo, normalmente MS Shell Dlg de 8 puntos. Una DLU horizontal es el ancho medio de la fuente del cuadro de diálogo dividido entre cuatro. Una DLU vertical es la altura media de la fuente dividida entre 8.

- Para cambiar los intervalos de las marcas de graduación, vaya a **formato** de menú > **configuración**de la guía y, a continuación, en el campo **espaciado de cuadrícula** , especifique un nuevo ancho y alto en DLU.

### <a name="layout-grid"></a>Cuadrícula de diseño

Al colocar o organizar los controles en un cuadro de diálogo, use la cuadrícula de diseño para obtener un posicionamiento más preciso. Cuando se activa la cuadrícula, los controles se ajustan a las líneas de puntos de la cuadrícula como si se magnetizaran.

- Para activar o desactivar la cuadrícula de diseño, vaya a **formato** de menú > configuración de la **Guía** y Active o desactive el botón **cuadrícula** .

   Todavía puede controlar la cuadrícula en ventanas individuales del **Editor de cuadros de diálogo** mediante el botón **alternar cuadrícula** de la [barra de herramientas del editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

- Para cambiar el tamaño de la cuadrícula de diseño, vaya a **formato** de menú > configuración de la **Guía** y escriba el alto y el ancho en DLU para las celdas de la cuadrícula. El alto o ancho mínimo es 4.

### <a name="disable-guides"></a>Deshabilitar guías

Puede usar teclas especiales junto con el mouse para deshabilitar el efecto de ajuste de las guías. Al usar la tecla **Alt** , se deshabilitan los efectos de ajuste de la guía seleccionada. Mover una guía con la tecla **MAYÚS** evita que los controles ajustados se muevan con la guía.

- Para deshabilitar el efecto de ajuste de las guías, arrastre el control manteniendo presionada la tecla **Alt** .

- Para mover guías sin mover los controles ajustados, arrastre la guía mientras mantiene presionada la tecla **MAYÚS** .

- Para desactivar las guías, vaya a **formato** de menú > **configuración**de la guía. A continuación, en **guías de diseño**, seleccione **ninguno**.

   > [!TIP]
   > También puede usar el acceso directo en el **formato** de menú > **alternar guías**.

## <a name="select-controls"></a>Seleccionar controles

Seleccione controles para cambiar su tamaño, alinearlos, moverlos, copiarlos o eliminarlos y, a continuación, completar la operación que desee. En la mayoría de los casos, es necesario seleccionar más de un control para usar las herramientas de ajuste de tamaño y alineación en la [barra de herramientas del editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Cuando se selecciona un control, tiene un borde sombreado en torno a él con controladores de tamaño opacos (activos) o huecos (inactivos), cuadrados pequeños que aparecen en el borde de la selección. Cuando se seleccionan varios controles, el control dominante tiene controladores de tamaño sólidos y todos los demás controles seleccionados tienen controladores de tamaño huecos.

- Para seleccionar controles, en la [ventana cuadro de herramientas](/visualstudio/ide/reference/toolbox), seleccione la herramienta **puntero** y use uno de los siguientes pasos para realizar la selección:

  - Arrastre el puntero para dibujar un cuadro de selección alrededor de los controles que desea seleccionar en el cuadro de diálogo. Al soltar el botón del mouse, se seleccionan todos los controles que se encuentran dentro y en intersección con el cuadro de selección.

  - Mantenga presionada la tecla **MAYÚS** y seleccione los controles que desea incluir en la selección.

  - Mantenga presionada la tecla **Ctrl** y seleccione los controles que desea incluir en la selección.

- Para agregar o quitar un control del grupo de controles seleccionados, mantenga presionada la tecla **MAYÚS** y seleccione el control que desea agregar o quitar.

### <a name="dominant-controls"></a>Controles dominantes

Al cambiar el tamaño o la alineación de varios controles, el **Editor de cuadros de diálogo** utiliza el control dominante para determinar el tamaño o la alineación de los demás controles. De forma predeterminada, el control dominante es el primer control seleccionado.

- Para especificar el control dominante, mantenga presionada la tecla **Ctrl** y seleccione el control que desea utilizar para influir *primero*en el tamaño o la ubicación de otros controles. Si mantiene presionada la tecla **Ctrl** y selecciona un control dentro de una selección, también hará que ese control sea el control dominante de la selección.

- Para cambiar el control dominante, borre la selección actual; para ello, seleccione fuera de todos los controles seleccionados actualmente y repita el procedimiento anterior y seleccione *primero*un control diferente.

> [!NOTE]
> Los controladores de tamaño del control dominante son sólidos mientras que los identificadores de los controles subordinados son huecos. Todo el cambio de tamaño o la alineación se basa en el control dominante.

## <a name="size-controls"></a>Controles de tamaño

Use los controladores de tamaño para cambiar el tamaño de un control. Cuando el puntero se coloca en un controlador de tamaño, cambia de forma para indicar las direcciones en las que se puede cambiar el tamaño del control. Los identificadores de tamaño activos son sólidos y, si un controlador de tamaño es hueco, no se puede cambiar el tamaño del control a lo largo de ese eje.

- Para ajustar el tamaño de un control, seleccione el control y arrastre los controladores de tamaño para cambiar el tamaño.

  - Los manipuladores de tamaño de la parte superior y los lados cambian el tamaño horizontal o vertical.

  - Los manipuladores de tamaño en las esquinas cambian el tamaño horizontal y vertical.

   > [!TIP]
   > Puede cambiar el tamaño del control en una unidad de cuadro de diálogo (DLU) cada vez manteniendo presionada la tecla **MAYÚS** y usando las teclas de dirección **derecha** **e izquierda.**

- Para ajustar automáticamente el tamaño de un control al texto que contiene, vaya a **formato** de menú o haga clic con el botón derecho en el control y elija **tamaño de contenido**.

- Para que los controles tengan el mismo tamaño, seleccione los controles que desea cambiar de tamaño y vaya al **formato** de menú > **igualar tamaño**y, a continuación, elija **ambos**, **alto**o **ancho**.

   Cambia el tamaño de un grupo de controles en función del tamaño del control dominante, que es el control seleccionado en primer lugar en la serie. El tamaño final de los controles del grupo depende del tamaño del control dominante.

- Para ajustar el tamaño de un grupo de controles con guías, ajuste un lado del control (o los controles) a una guía y, a continuación, arrastre una guía al otro lado del control (o los controles). Ahora puede cambiar cualquier guía para ajustar el tamaño del control (o de los controles).

   Si es necesario con varios controles, ajuste cada uno de ellos para ajustarse a la segunda guía.

### <a name="other-controls"></a>Otros controles

Puede cambiar el tamaño de un cuadro combinado al agregarlo al cuadro de diálogo. También puede especificar el tamaño del cuadro de lista desplegable. Para obtener más información, vea [Agregar valores a un control de cuadro combinado](../windows/adding-values-to-a-combo-box-control.md).

1. Seleccione el botón de flecha desplegable que se encuentra a la derecha del cuadro combinado.

   ![Flecha de un cuadro combinado en un proyecto MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   El contorno del control cambia para mostrar el tamaño del cuadro combinado con el área de la lista desplegable extendida.

1. Use el controlador de tamaño inferior para cambiar el tamaño inicial del área de la lista desplegable.

   ![Ajuste&#45;de tamaño del cuadro combinado en un proyecto MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Vuelva a seleccionar la flecha desplegable para cerrar la parte de la lista desplegable del cuadro combinado.

> [!NOTE]
> Al agregar un cuadro de lista con una barra de desplazamiento horizontal a un cuadro de diálogo mediante MFC, la barra de desplazamiento no aparecerá automáticamente en la aplicación.
>
> Establezca un ancho máximo para el elemento más ancho llamando a [CListBox:: SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) en el código. Si no se establece este valor, no aparecerá la barra de desplazamiento, aunque los elementos del cuadro de lista sean más anchos que el cuadro.

## <a name="align-controls"></a>Alinear controles

- Para alinear controles, seleccione los controles que desea alinear. Vaya a **formato** de menú > **alinear** y elija una de las siguientes alineaciones:

   |Alignment|Descripción|
   |-----|-----------|
   |**Lados izquierdos**|Alinea los controles seleccionados a lo largo de los lados izquierdos.|
   |**Implicados**|Alinea los controles seleccionados horizontalmente a lo largo de sus puntos centrales.|
   |**Derechos**|Alinea los controles seleccionados a lo largo de los lados de la derecha.|
   |**Partes superiores**|Alinea los controles seleccionados a lo largo de sus bordes superiores.|
   |**Puntos medios**|Alinea los controles seleccionados verticalmente a lo largo de sus puntos medios.|
   |**Lados inferiores**|Alinea los controles seleccionados a lo largo de sus bordes inferiores.|

   Asegúrese de seleccionar el control que desea que sea dominante primero o establézcalo en el control dominante antes de ejecutar el comando Alignment o sizing, ya que la posición final del grupo de controles depende de la posición del control dominante.

- Para espaciar uniformemente los controles, seleccione los controles que desea reorganizar. Vaya a **formato** de menú > espacio de manera **uniforme** y elija una de las siguientes alineaciones de espaciado:

   |Spacing|Descripción|
   |---|---|
   |**Transferir**|Espaciar los controles uniformemente entre el extremo izquierdo y el control situado más a la derecha.|
   |**Bajar**|Los controles de espacio se seleccionan uniformemente entre el control de nivel superior y el de la parte inferior.|

- Para centrar controles, seleccione el control o los controles que desea reorganizar. Vaya a menú **formato** > **centro en el cuadro de diálogo** y elija una de las siguientes disposiciones:

   |Organización|Descripción|
   |---|---|
   |**Vertical**|Centrar los controles verticalmente en el cuadro de diálogo.|
   |**Horizontal**|Centrar los controles horizontalmente en el cuadro de diálogo.|

- Para alinear los botones de la selección, seleccione uno o más botones de reenvío. Vaya a **formato** de menú > **organizar botones**y, a continuación, elija una de las siguientes disposiciones:

   |Organización|Descripción|
   |---|---|
   |**Right**|Alinea los botones de reenvío a lo largo del borde derecho del cuadro de diálogo.|
   |**Inferior**|Alinea los botones de reenvío a lo largo del borde inferior del cuadro de diálogo.|

   Si selecciona un control que no sea un botón de reenvío, su posición no se verá afectada.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Administrar controles del cuadro de diálogo](controls-in-dialog-boxes.md)<br/>
[Cómo: agregar, editar o eliminar controles](adding-editing-or-deleting-controls.md)<br/>
[Cómo: definir el acceso y los valores de control](defining-mnemonics-access-keys.md)<br/>
