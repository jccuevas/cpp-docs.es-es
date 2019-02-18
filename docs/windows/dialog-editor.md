---
title: Cuadro de diálogo Editor (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: fef4a7f0d4c785a40ea946127d8e3c84c797e1aa
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336701"
---
# <a name="dialog-editor-c"></a>Cuadro de diálogo Editor (C++)

El **diálogo** editor le permite crear o editar recursos de cuadro de diálogo. Abra el editor de cuadro de diálogo haciendo doble clic en el archivo .rc de un cuadro de diálogo en el **vista de recursos** ventana (**vista** > **vista de recursos**). Tenga en cuenta que **vista de recursos** no está disponible en las ediciones Express.

Uno de los primeros pasos para crear un cuadro de diálogo nuevo (o una plantilla de cuadro de diálogo) consiste en agregar controles. En el **diálogo** editor, puede organizar los controles para ajustarse a un determinado tamaño, forma o alineación o moverlos a fin de trabajar en el cuadro de diálogo. También es fácil eliminar un control.

Es posible almacenar un cuadro de diálogo como una plantilla para poder reutilizado más adelante. También es posible alternar entre el diseño del cuadro de diálogo y la edición del código que lo implementa.

Asimismo, en el Editor de cuadros de diálogo se pueden editar las propiedades de uno o varios controles. Puede cambiar el orden de tabulación, es decir, el orden en que se obtienen los controles centrarse cuando la **ficha** se presiona la tecla o puede definir una clave de acceso (una combinación de teclas) que permite a los usuarios elegir un control mediante el teclado.

El **diálogo** editor también permite usar controles personalizados, incluidos los controles ActiveX. Además, se puede editar una [vista de formulario](../mfc/reference/cformview-class.md), [vistas de registros](../data/record-views-mfc-data-access.md)o [barras de cuadro de diálogo](../mfc/dialog-bars.md).

A partir de Visual Studio 2015, puede usar el editor de cuadro de diálogo para definir diseños dinámicos, que especifican cómo los controles moverán y cambiar el tamaño cuando el usuario cambia el tamaño de un cuadro de diálogo. Para obtener más información, vea [Dynamic Layout](../mfc/dynamic-layout.md).

- [Cómo: Crear un cuadro de diálogo](../windows/creating-a-new-dialog-box.md)

- [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)

   > [!TIP]
   > Al usar el **diálogo** editor, en muchos casos, puede seleccionar el botón secundario del mouse para mostrar un menú contextual de comandos usados con frecuencia.

## <a name="dialog-editor-toolbar"></a>Barra de herramientas del Editor de cuadros de diálogo

Al abrir el **diálogo** editor en un proyecto de C++, el **Editor de cuadro de diálogo** barra de herramientas aparece automáticamente en la parte superior de la solución.

|Iconos|Significado|Iconos|Significado|
|----------|-------------|----------|-------------|
|![Botón de cuadro de diálogo de prueba](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Probar cuadro de diálogo|![Botón espaciar horizontalmente](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalmente|
|![Botón Alinear lados izquierdos](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Alinear lados izquierdos|![Botón Espaciar verticalmente](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Verticalmente|
|![Botón Alinear lados derechos](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Alinear lados derechos|![Asegúrese de mismo ancho botón](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Igualar ancho|
|![Botón Alinear lados superiores](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Alinear lados superiores|![Botón de la misma altura de Make](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Igualar alto|
|![Botón Alinear lados inferiores](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Alinear lados inferiores|![Botón de tamaño de la misma marca](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Igualar tamaño|
|![Botón Centrar verticalmente](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Botón Alternar cuadrícula](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Alternar cuadrícula|
|![Botón Centrar horizontalmente](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Botón Alternar guías](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Alternar guías|

El **Editor de cuadro de diálogo** barra de herramientas contiene botones para organizar el diseño de controles en el cuadro de diálogo, por ejemplo tamaño y la alineación. **Cuadro de diálogo Editor** botones de barra de herramientas se corresponden con los comandos de la **formato** menú.

Cuando esté en el **diálogo** editor, puede alternar la presentación de la **Editor de cuadro de diálogo** barra de herramientas, selecciónelo en la lista de ventanas y barras de herramientas disponibles.

- Para mostrar u ocultar la barra de herramientas del editor de cuadro de diálogo, en el **vista** menú, seleccione **las barras de herramientas**, a continuación, elija **Editor de cuadro de diálogo** desde el submenú.

   > [!NOTE]
   > El **Editor de cuadro de diálogo** barra de herramientas se muestra de forma predeterminada al abrir un recurso de cuadro de diálogo en el editor de cuadro de diálogo; sin embargo, si cierra explícitamente la barra de herramientas, debe invocarse la próxima vez que abra un recurso de cuadro de diálogo.

## <a name="switch-between-dialog-box-controls-and-code"></a>Cambiar entre los controles de cuadro de diálogo y el código

En las aplicaciones MFC, puede hacer doble clic en los controles de cuadro de diálogo para saltar al código de su controlador o para crear rápidamente código auxiliar de funciones del controlador.

Con un control seleccionado, haga clic en el **eventos de control** botón o la **mensajes** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window) para ver una lista completa de eventos y mensajes de Windows está disponible para el elemento seleccionado. Elija en la lista para crear o editar funciones de controlador.

- Para saltar al código desde el editor de cuadro de diálogo, haga doble clic en un control en el cuadro de diálogo para saltar a la declaración de su función de control de mensajes más recientemente implementada. (Para las clases de cuadro de diálogo basado en ATL, siempre se salta a la definición del constructor.)

- Para ver los eventos de un control con un control seleccionado, elija la **eventos de control** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window).

   > [!NOTE]
   > Elegir el **eventos de control** botón cuando el *cuadro de diálogo* tiene foco expone una lista de todos los controles en el cuadro de diálogo, que, a continuación, se puede expandir para modificar los eventos para los controles individuales.

   Cuando un solo control tiene el foco en el cuadro de diálogo, puede haga clic en él y seleccione **Add Event Handler** en el menú contextual. Esto le permite especificar la clase a la que se agrega el controlador. Para obtener más información, consulte [agregando un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).

- Para ver los mensajes para un cuadro de diálogo con el cuadro de diálogo seleccionado, elija la **mensajes** situado en la [ventana propiedades](/visualstudio/ide/reference/properties-window).

## <a name="accelerator-keys"></a>Teclas de aceleración

A continuación son el valor predeterminado de las teclas de aceleración para los comandos del editor de cuadro de diálogo. Para cambiar las teclas de método abreviado, seleccione **opciones** en el **herramientas** menú, a continuación, elija **teclado** bajo el **entorno** carpeta. Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Comando|Teclas|Descripción|
|-------------|----------|-----------------|
|Format.AlignBottoms|**CTRL** + **MAYÚS** + **flecha abajo**|Alinea el borde inferior de los controles seleccionados con el control dominante|
|Format.AlignCenters|**MAYÚS** + **F9**|Alinea los centros verticales de los controles seleccionados con el control dominante|
|Format.AlignLefts|**CTRL** + **MAYÚS** + **flecha izquierda**|Alinea el borde izquierdo de los controles seleccionados con el control dominante|
|Format.AlignMiddles|**F9**|Alinea los centros horizontales de los controles seleccionados con el control dominante|
|Format.AlignRights|**CTRL** + **MAYÚS** + **flecha derecha**|Alinea el borde derecho de los controles seleccionados con el control dominante|
|Format.AlignTops|**CTRL** + **MAYÚS** + **flecha arriba**|Alinea el borde superior de los controles seleccionados con el control dominante|
|Format.ButtonBottom|**Ctrl** + **B**|Coloca los botones seleccionados a lo largo de la parte inferior central del cuadro de diálogo|
|Format.ButtonRight|**Ctrl** + **R**|Coloca los botones seleccionados en la esquina superior derecha del cuadro de diálogo|
|Format.CenterHorizontal|**CTRL** + **MAYÚS** + **F9**|Centra los controles horizontalmente en el cuadro de diálogo|
|Format.CenterVertical|**Ctrl** + **F9**|Centra los controles verticalmente en el cuadro de diálogo|
|Format.CheckMnemonics|**CTRL** + **M**|Comprobaciones de unicidad de las teclas de acceso|
|Format.SizeToContent|**MAYÚS** + **F7**|Cambia el tamaño de los controles seleccionados para ajustar el texto del título|
|Format.SpaceAcross|**Alt** + **Flecha izquierda**|Distribuye uniformemente los controles seleccionados horizontalmente|
|Format.SpaceDown|**ALT** + **flecha abajo**|Un espaciado uniforme a los controles seleccionados verticalmente|
|Format.TabOrder|**Ctrl** + **D**|Establece el orden de los controles en el cuadro de diálogo|
|Format.TestDialog|**Ctrl** + **T**|Se ejecuta el cuadro de diálogo para probar la apariencia y comportamiento|
|Format.ToggleGuides|**Ctrl** + **G**|Ciclos entre ninguna cuadrícula, directrices y cuadrícula de cuadro de diálogo de edición|

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Cómo: Crear un recurso](../windows/how-to-create-a-resource.md)<br/>
[Controles](../mfc/controls-mfc.md)<br/>
[Clases de control](../mfc/control-classes.md)<br/>
[Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)<br/>
[Tipos de controles de cuadro de diálogo y tipos de variable](../ide/dialog-box-controls-and-variable-types.md)