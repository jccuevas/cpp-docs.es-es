---
title: Editor de cuadros de diálogo (C++)
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
ms.openlocfilehash: f1544d3a8e14f9373e21b77d888860d24ab1ed6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370288"
---
# <a name="dialog-editor-c"></a>Editor de cuadros de diálogo (C++)

El **Editor de cuadros** de diálogo le permite crear o editar recursos de cuadro de diálogo.

- Para abrir el editor, haga doble clic en el archivo .rc de un cuadro de diálogo en la ventana **Vista** de recursos o vaya al menú **Ver** > otra**vista**de recursos de**Windows** > .

Uno de los primeros pasos para crear un nuevo cuadro de diálogo o una plantilla de cuadro de diálogo es agregar controles. En el Editor de cuadros de **diálogo**, puede organizar los controles para que se ajusten a un determinado tamaño, forma o alineación, o puede moverlos para trabajar dentro del cuadro de diálogo. También es fácil eliminar un control.

Es posible almacenar un cuadro de diálogo como una plantilla para poder reutilizado más adelante. También es posible alternar entre el diseño del cuadro de diálogo y la edición del código que lo implementa.

También es posible editar las propiedades de uno o varios controles en el **Editor de cuadros**de diálogo . Puede cambiar el orden de tabulación, es decir, **Tab** el orden en el que los controles ganan el foco cuando se presiona la tecla Tabulador, o puede definir una tecla de acceso o una combinación de teclas que permita a los usuarios elegir un control con el teclado.

El **Editor de cuadros** de diálogo también permite usar controles personalizados, incluidos los controles ActiveX. También puede editar una vista de [formulario,](../mfc/reference/cformview-class.md)vistas de [registro](../data/record-views-mfc-data-access.md)o barras de [diálogo.](../mfc/dialog-bars.md)

A partir de Visual Studio 2015, puede usar el Editor de **cuadros** de diálogo para definir diseños dinámicos, que especifican cómo se mueven y cambian de tamaño los controles cuando el usuario cambia el tamaño de un cuadro de diálogo. Para obtener más información, vea [Dynamic Layout](../mfc/dynamic-layout.md).

Para obtener más información sobre los recursos, vea [cómo crear un](../windows/creating-a-new-dialog-box.md) cuadro de diálogo y controles de cuadro de [diálogo](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Al utilizar el Editor de **cuadros**de diálogo , en muchos casos, puede seleccionar con el botón derecho del ratón para mostrar un menú contextual de comandos utilizados con frecuencia.

## <a name="dialog-editor-toolbar"></a>Barra de herramientas del Editor de cuadros de diálogo

La barra de herramientas **Editor** de cuadros de diálogo contiene botones para organizar el diseño de los controles en el cuadro de diálogo, por ejemplo, el tamaño y la alineación. **Los** botones de la barra de herramientas del Editor de cuadros de diálogo corresponden a los comandos del menú **Formato.**

|Icono|Significado|Icono|Significado|
|----------|-------------|----------|-------------|
|![Botón Probar cuadro de diálogo](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Probar cuadro de diálogo|![Botón Espaciar horizontalmente](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalmente|
|![Botón Alinear lados izquierdos](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Alinear lados izquierdos|![Botón Espaciar verticalmente](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Bajar|
|![Botón Alinear lados derechos](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Alinear lados derechos|![Botón Igualar ancho](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Igualar ancho|
|![Botón Alinear lados superiores](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Alinear lados superiores|![Botón Igualar alto](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Igualar alto|
|![Botón Alinear lados inferiores](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Alinear lados inferiores|![Botón Igualar tamaño](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Igualar tamaño|
|![Botón Centrar verticalmente](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Botón Alternar cuadrícula](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Alternar cuadrícula|
|![Botón Centrar horizontalmente](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Botón Alternar guías](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Alternar guías|

- Para mostrar u ocultar la barra de herramientas Del Editor de cuadros de **diálogo,** vaya al menú **Ver** > editor de**cuadros** > de diálogo de barras de**herramientas**.

Al abrir el Editor de **cuadros** de diálogo en un proyecto de C++, la barra de herramientas **Editor** de cuadros de diálogo aparece automáticamente en la parte superior de la solución, sin embargo, si cierra explícitamente la barra de herramientas, deberá invocarla la próxima vez que abra el Editor de **cuadros**de diálogo . Puede alternar su visualización seleccionándola en la lista de barras de herramientas y ventanas disponibles.

## <a name="switch-between-dialog-box-controls-and-code"></a>Cambiar entre controles de cuadro de diálogo y código

En las aplicaciones MFC, puede hacer doble clic en los controles del cuadro de diálogo para saltar a su código de controlador o para crear rápidamente funciones de controlador de código auxiliar.

Con un control seleccionado, seleccione el botón **ControlEvents** o el botón **Mensajes** en la [ventana Propiedades](/visualstudio/ide/reference/properties-window) para ver una lista completa de los mensajes y eventos de Windows disponibles para el elemento seleccionado. Elija de la lista para crear o editar funciones de controlador.

- Para saltar al código desde el Editor de **cuadros**de diálogo , haga doble clic en un control dentro del cuadro de diálogo para saltar a la declaración de su función de control de mensajes implementada más recientemente.

   Para las clases de cuadro de diálogo basadas en ATL, siempre salta a la definición del constructor.

- Para ver los eventos de un control, con un control seleccionado, elija el botón **ControlEvents** en la ventana **Propiedades.**

   Cuando un único control tiene el foco en el cuadro de diálogo, puede hacer clic con el botón derecho y seleccionar **Agregar controlador**de eventos . Esto le permite especificar la clase a la que se agrega el controlador. Para obtener más información, consulte [Agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Al elegir el botón **ControlEvents** cuando el cuadro de diálogo tiene el foco, se expone una lista de todos los controles del cuadro de diálogo, que puede expandir para editar los eventos de los controles individuales.

- Para ver los mensajes de un cuadro de diálogo, con el cuadro de diálogo seleccionado, elija el botón **Mensajes** en la ventana **Propiedades.**

## <a name="accelerator-keys"></a>Teclas de aceleración

A continuación se muestran las teclas de aceleración predeterminadas para los comandos del **Editor de cuadros** de diálogo.  

|Get-Help|Claves|Descripción|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **Shift** + **Flecha abajo**|Alinea los bordes inferiores de los controles seleccionados con el control dominante.|
|Format.AlignCenters|**Shift** + **F9**|Alinea los centros verticales de los controles seleccionados con el control dominante.|
|Format.AlignLefts|**Ctrl** + **Shift** + **Flecha izquierda**|Alinea los bordes izquierdos de los controles seleccionados con el control dominante.|
|Format.AlignMiddles|**F9**|Alinea los centros horizontales de los controles seleccionados con el control dominante.|
|Format.AlignRights|**Ctrl** + **Shift** + **Flecha derecha**|Alinea los bordes rectos de los controles seleccionados con el control dominante.|
|Format.AlignTops|**Ctrl** + **Shift** + **Flecha Arriba**|Alinea los bordes superiores de los controles seleccionados con el control dominante.|
|Format.ButtonBottom|**Ctrl** + **B**|Coloca los botones seleccionados a lo largo del centro inferior del cuadro de diálogo.|
|Format.ButtonRight|**Ctrl** + **R**|Coloca los botones seleccionados en la esquina superior derecha del cuadro de diálogo.|
|Format.CenterHorizontal|**Ctrl** + **Shift** + **F9**|Centra los controles horizontalmente en el cuadro de diálogo.|
|Format.CenterVertical|**Ctrl** + **F9**|Centra los controles verticalmente dentro del cuadro de diálogo.|
|Format.CheckMnemonics|**Ctrl** + **M**|Comprueba la singularidad de los mnemotécnicos.|
|Format.SizeToContent|**Shift** + **F7**|Cambia el tamaño de los controles seleccionados para que se ajusten al texto del título.|
|Format.SpaceAcross|**Alt** + **Flecha izquierda**|Separa uniformemente los controles seleccionados horizontalmente.|
|Format.SpaceDown|**Alt** + **Flecha abajo**|Separa uniformemente los controles seleccionados verticalmente.|
|Format.TabOrder|**Ctrl** + **D**|Establece el orden de los controles dentro del cuadro de diálogo.|
|Format.TestDialog|**Ctrl** + **T**|Ejecuta el cuadro de diálogo para probar la apariencia y el comportamiento.|
|Format.ToggleGuides|**Ctrl** + **G**|Ciclos entre ninguna cuadrícula, directrices y cuadrícula para la edición de cuadros de diálogo.|

- Para cambiar las teclas **Tools** > de método abreviado, vaya al menú**Opciones**de herramientas y elija **Teclado** en la carpeta **Entorno.**

   Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Para cambiar la configuración, vaya al menú **Herramientas** > **Importar y exportar ajustes**.

   Las opciones disponibles en los cuadros de diálogo y los nombres y ubicaciones de los comandos de menú que ve pueden diferir de lo que se describe en **la Ayuda** en función de la configuración activa o la edición.  Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Cómo: Crear un cuadro de diálogo](../windows/creating-a-new-dialog-box.md)<br/>
[Controles de cuadro de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
