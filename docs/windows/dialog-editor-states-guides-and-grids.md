---
title: Estados del Editor de cuadro de diálogo (guías y cuadrículas) (C++)
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: dbacf9ef-e8b0-4125-a7ce-84911c482e98
ms.openlocfilehash: 52fc19d8a39680c16692177e2758fba78afc7d3a
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484999"
---
# <a name="dialog-editor-states-guides-and-grids-c"></a>Estados del Editor de cuadro de diálogo (guías y cuadrículas) (C++)

Puede organizar los controles de cuadros de diálogo con el **diálogo** editor en uno de tres estados diferentes:

- Con las guías y márgenes en (valor predeterminado)

- Con la cuadrícula de diseño en

- Sin ninguna característica de ajuste o alineación

El [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) contiene botones que controlan el estado. Para cambiar el estado, haga clic en el icono adecuado. También puede cambiar el estado mediante el uso de la **configuración de la guía** comando el **formato** menú.

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

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-and-set-guides-and-margins"></a>Crear y establecer las guías y márgenes

Si está moviendo los controles, agregar controles o reorganizar un diseño actual, las guías pueden ayudarle a alinear los controles con precisión dentro de un cuadro de diálogo. Las guías aparecen en azul las líneas de puntos en el cuadro de diálogo que aparece en el editor y flechas correspondientes en las reglas en la parte superior y en el lado izquierdo de la **diálogo** editor.

Cuando se crea un cuadro de diálogo, se proporcionan cuatro márgenes. Los márgenes son guías modificadas, que aparecen como líneas de puntos azules.

### <a name="to-create-a-guide"></a>Para crear una guía

Dentro de la regla, haga clic una vez para crear a una guía. (Un solo clic crea una nueva guía; hacer doble clic en los lanzamientos de la **configuración de la guía** cuadro de diálogo en el que puede especificar la configuración de la guía.)

### <a name="to-set-a-guide"></a>Para establecer una guía

En el cuadro de diálogo, haga clic en la guía y arrástrelo a una nueva posición. (También puede hacer clic en la flecha de la regla para arrastrar a la guía asociada.)

Las coordenadas de la guía se muestran en la barra de estado en la parte inferior de la ventana y en la regla. Mueva el puntero sobre la flecha de la regla para mostrar la posición exacta de la guía.

### <a name="to-delete-a-guide"></a>Para eliminar una guía

Arrastre a la guía fuera del cuadro de diálogo.

\- o -

Arrastre la flecha correspondiente fuera de la regla.

### <a name="to-move-margins"></a>Para mover los márgenes

Arrastre el margen a la nueva posición.

Para que desaparezca un margen, mueva el margen a una posición cero. Para devolver el margen, coloque el puntero sobre el margen de la posición cero y mueva el margen a posición.

## <a name="align-controls-on-a-guide"></a>Alinear controles en una guía

Los controladores de tamaño de los controles se ajustan a las guías cuando se mueven los controles y las guías se ajustan a los controles, si no hay ningún control previamente ajustados a la guía. Cuando se mueve una guía, también se mueven los controles que se ajustan a él. Controles ajustados a más de una guía cambian de tamaño cuando se mueve una de las guías.

Las marcas de graduación en las reglas que determinan el espaciado de las guías y los controles se definen mediante unidades de cuadro de diálogo (DLU). Las unidades se basan en el tamaño de la fuente del cuadro de diálogo, normalmente de 8 puntas MS Shell Dlg. Una DLU horizontal es el ancho promedio de la fuente del cuadro de diálogo dividido por cuatro. Una vertical equivale al alto medio de la fuente dividido por ocho.

### <a name="to-size-a-group-of-controls-with-guides"></a>Para cambiar el tamaño de un grupo de controles con guías

1. Ajustar un lado del control (o controles) a una guía.

1. Arrastre a una guía para el otro lado del control (o controles).

   Si es necesario con varios controles, cambiar el tamaño de cada uno que se ajuste a la segunda guía.

1. Mueva una de las guías para cambiar el tamaño del control (o controles).

### <a name="to-change-the-intervals-of-the-tick-marks"></a>Cambiar los intervalos de las marcas de graduación

1. Desde el **formato** menú, elija **configuración de la guía**.

1. En el **configuración de la guía** cuadro de diálogo el **espaciado de cuadrícula** , especifique un nuevo ancho y alto en DLU.

## <a name="disable-guides"></a>Deshabilitar guías

Puede usar las teclas especiales junto con el mouse para deshabilitar el efecto de las guías de ajuste. Mediante el **Alt** clave deshabilita los efectos de ajuste de la Guía seleccionada. Mover una guía con el **MAYÚS** clave impide que los controles ajustados mover con la guía.

### <a name="to-disable-the-snapping-effect-of-the-guides"></a>Para deshabilitar el efecto de ajuste de las guías

Arrastre el control mientras mantiene presionada la **Alt** clave.

### <a name="to-move-guides-without-moving-the-snapped-controls"></a>Para mover guías sin mover los controles ajustados

Arrastre la guía mientras mantiene presionada la **MAYÚS** clave.

### <a name="to-turn-off-the-guides"></a>Para desactivar las guías

1. Desde el **formato** menú, elija **configuración de la guía**.

1. En el **configuración de la guía** cuadro de diálogo **las guías de diseño**, seleccione **ninguno**.

   > [!NOTE]
   > También puede haga doble clic en la barra de la regla para tener acceso a la **configuración de la guía** cuadro de diálogo.

\- o -

En el **formato** menú, seleccione **Alternar guías**.

## <a name="modify-the-layout-grid"></a>Modificar la cuadrícula de diseño

Cuando se coloca u organizar controles en un cuadro de diálogo, puede usar la cuadrícula de diseño para una ubicación más precisa. Cuando la cuadrícula está activada, los controles aparecen en "Ajustar a" las líneas de puntos de la cuadrícula como si estuvieran imantados. Puede activar y desactivar la esta característica "Ajustar a la cuadrícula" y cambiar el tamaño de las celdas de cuadrícula de diseño.

### <a name="to-turn-the-layout-grid-on-or-off"></a>Para activar y desactivar la cuadrícula de diseño

1. Desde el **formato** menú, elija **configuración de la guía**.

1. En el **configuración de la guía** cuadro de diálogo, active o desactive el **cuadrícula** botón.

   Todavía puede controlar la cuadrícula en persona **diálogo** ventanas del editor mediante el **Alternar cuadrícula** situado en la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

### <a name="to-change-the-size-of-the-layout-grid"></a>Para cambiar el tamaño de la cuadrícula de diseño

1. Desde el **formato** menú, elija **configuración de la guía**.

1. En el **configuración de la guía** diálogo cuadro, escriba el alto y ancho en DLU para las celdas de la cuadrícula. El alto o ancho mínimo es de 4 DLU. Para obtener más información sobre las unidades DLU, vea [distribución de los controles en cuadros de diálogo](../windows/arrangement-of-controls-on-dialog-boxes.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles (MFC)](../mfc/controls-mfc.md)<br/>
