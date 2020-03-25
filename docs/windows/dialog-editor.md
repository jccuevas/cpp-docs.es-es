---
title: Editor de cuadrosC++de diálogo ()
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
ms.openlocfilehash: 9d0f9993d81c499f67a08e5401c5e56dba7b281c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215259"
---
# <a name="dialog-editor-c"></a>Editor de cuadrosC++de diálogo ()

El **Editor de cuadros de diálogo** permite crear o editar recursos de cuadro de diálogo.

- Para abrir el editor, haga doble clic en el archivo. rc de un cuadro de diálogo en la ventana de **vista de recursos** o vaya a la **vista** de menú > **otras ventanas** > **vista de recursos**.

Uno de los primeros pasos para crear una plantilla de cuadro de diálogo o cuadro de diálogo nuevo es agregar controles. En el **Editor de cuadros de diálogo**, puede organizar los controles para ajustarse a un determinado tamaño, forma o alineación, o puede desplazarlos para trabajar en el cuadro de diálogo. También es fácil eliminar un control.

Es posible almacenar un cuadro de diálogo como una plantilla para poder reutilizado más adelante. También es posible alternar entre el diseño del cuadro de diálogo y la edición del código que lo implementa.

También es posible editar las propiedades de uno o varios controles en el **Editor de cuadros de diálogo**. Puede cambiar el orden de tabulación, es decir, el orden en que los controles obtienen el foco cuando se presiona la tecla **Tab** , o puede definir una tecla de acceso o una combinación de teclas que permita a los usuarios elegir un control con el teclado.

El **Editor de cuadros de diálogo** también permite usar controles personalizados, incluidos los controles ActiveX. También puede editar una [vista de formulario](../mfc/reference/cformview-class.md), [vistas de registros](../data/record-views-mfc-data-access.md)o [barras de cuadro de diálogo](../mfc/dialog-bars.md).

A partir de Visual Studio 2015, puede usar el **Editor de cuadros de diálogo** para definir diseños dinámicos, que especifican cómo se mueven y se cambia el tamaño de los controles cuando el usuario cambia el tamaño de un cuadro de diálogo. Para obtener más información, vea [Dynamic Layout](../mfc/dynamic-layout.md).

Para obtener más información sobre los recursos, vea cómo [crear un cuadro de diálogo](../windows/creating-a-new-dialog-box.md) y [controles de cuadro de diálogo](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Al usar el **Editor de cuadros de diálogo**, en muchos casos, puede seleccionar con el botón secundario del mouse para mostrar un menú contextual de comandos de uso frecuente.

## <a name="dialog-editor-toolbar"></a>Barra de herramientas del Editor de cuadros de diálogo

La barra de herramientas del **Editor de cuadros de diálogo** contiene botones para organizar el diseño de los controles en el cuadro de diálogo, por ejemplo, el tamaño y la alineación. Los botones de la barra de herramientas del **Editor de cuadros de diálogo** corresponden a comandos del menú **formato** .

|Icono|Significado|Icono|Significado|
|----------|-------------|----------|-------------|
|![Botón de cuadro de diálogo probar](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Probar cuadro de diálogo|![Espacio entre el botón](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Horizontalmente|
|![Botón alinear lados izquierdos](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Alinear lados izquierdos|![Botón espaciar verticalmente](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Bajar|
|![Botón alinear derechos](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Alinear lados derechos|![Botón igualar ancho](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Igualar ancho|
|![Botón alinear lados superiores](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Alinear lados superiores|![Botón igualar alto](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Igualar alto|
|![Botón alinear lados inferiores](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Alinear lados inferiores|![Botón igualar tamaño](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Igualar tamaño|
|![Botón centrar verticalmente](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Vertical|![Botón alternar cuadrícula](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Alternar cuadrícula|
|![Botón central horizontal](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Botón alternar guías](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Alternar guías|

- Para mostrar u ocultar la barra de herramientas del **Editor de cuadros de diálogo** , vaya a la **vista** de menú > **barras de herramientas** > editor de **cuadros de diálogo**.

Al abrir el **Editor de cuadros** de diálogo C++ en un proyecto, la barra de herramientas del **Editor de cuadros de diálogo** aparece automáticamente en la parte superior de la solución. sin embargo, si cierra explícitamente la barra de herramientas, deberá invocarla la próxima vez que abra el editor de cuadros de **diálogo**. Puede alternar la presentación seleccionándola en la lista de barras de herramientas y ventanas disponibles.

## <a name="switch-between-dialog-box-controls-and-code"></a>Cambiar entre los controles de cuadro de diálogo y el código

En aplicaciones MFC, puede hacer doble clic en los controles de cuadro de diálogo para saltar a su código de controlador o para crear rápidamente funciones de controlador de código auxiliar.

Con un control seleccionado, seleccione el botón **ControlEvents** o el botón **mensajes** en la [ventana Propiedades](/visualstudio/ide/reference/properties-window) para ver una lista completa de los mensajes y eventos de Windows disponibles para el elemento seleccionado. Elija en la lista para crear o editar funciones controladoras.

- Para saltar al código desde el **Editor de cuadros de diálogo**, haga doble clic en un control en el cuadro de diálogo para saltar a la declaración de su función de control de mensajes implementada más recientemente.

   En el caso de las clases de cuadro de diálogo basadas en ATL, siempre salta a la definición del constructor.

- Para ver los eventos de un control, con un control seleccionado, elija el botón **ControlEvents** en la ventana **propiedades** .

   Cuando un solo control tiene el foco en el cuadro de diálogo, puede hacer clic con el botón derecho y seleccionar **Agregar controlador de eventos**. Esto le permite especificar la clase a la que se agrega el controlador. Para obtener más información, vea [Agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Al elegir el botón **ControlEvents** cuando el cuadro de diálogo tiene el foco, se muestra una lista de todos los controles del cuadro de diálogo, que se pueden expandir para editar los eventos de los controles individuales.

- Para ver los mensajes de un cuadro de diálogo, con el cuadro de diálogo seleccionado, elija el botón **mensajes** en la ventana **propiedades** .

## <a name="accelerator-keys"></a>Teclas de aceleración

A continuación se muestran las teclas de aceleración predeterminadas para los comandos del **Editor de cuadros de diálogo** .  

|Get-Help|Claves|Descripción|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **MAYÚS** + **flecha abajo**|Alinea los bordes inferiores de los controles seleccionados con el control dominante.|
|Format.AlignCenters|**Mayús** + **F9**|Alinea los centros verticales de los controles seleccionados con el control dominante.|
|Format.AlignLefts|**Ctrl** + **MAYÚS** + **flecha izquierda**|Alinea los bordes izquierdos de los controles seleccionados con el control dominante.|
|Format.AlignMiddles|**F9**|Alinea los centros horizontales de los controles seleccionados con el control dominante.|
|Format.AlignRights|**Ctrl** + **MAYÚS** + **flecha derecha**|Alinea los bordes derecho de los controles seleccionados con el control dominante.|
|Format.AlignTops|Tecla **Ctrl** + **MAYÚS** + **flecha arriba**|Alinea los bordes superiores de los controles seleccionados con el control dominante.|
|Format.ButtonBottom|**Ctrl** + **B**|Coloca los botones seleccionados a lo largo del centro del cuadro de diálogo.|
|Format.ButtonRight|**Ctrl** + **R**|Coloca los botones seleccionados en la esquina superior derecha del cuadro de diálogo.|
|Format.CenterHorizontal|**Ctrl** + **MAYÚS** + **F9**|Centra los controles horizontalmente en el cuadro de diálogo.|
|Format.CenterVertical|**Ctrl** + **F9**|Centra los controles verticalmente en el cuadro de diálogo.|
|Format.CheckMnemonics|**Ctrl** + **M**|Comprueba la unicidad de los mnemónicos.|
|Format.SizeToContent|**Shift** + **F7**|Cambia el tamaño de los controles seleccionados para ajustarse al texto de la leyenda.|
|Format.SpaceAcross|**Alt** + **Flecha izquierda**|Espacia de forma uniforme los controles seleccionados horizontalmente.|
|Format.SpaceDown|**Alt** + **flecha abajo**|Espacia uniformemente los controles seleccionados verticalmente.|
|Format.TabOrder|**Ctrl** + **D**|Establece el orden de los controles en el cuadro de diálogo.|
|Format.TestDialog|**Ctrl** + **T**|Ejecuta el cuadro de diálogo para probar la apariencia y el comportamiento.|
|Format.ToggleGuides|**Ctrl** + **G**|Ciclos entre ninguna cuadrícula, instrucciones y cuadrícula para la edición de cuadros de diálogo.|

- Para cambiar las teclas de método abreviado, vaya a **herramientas** de menú > **Opciones**y elija **teclado** en la carpeta **entorno** .

   Para obtener más información, vea [Identificar y personalizar métodos abreviados de teclado](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Para cambiar la configuración, vaya a **herramientas** de menú > **importar y exportar configuraciones**.

   Las opciones disponibles en los cuadros de diálogo y los nombres y las ubicaciones de los comandos de menú que se ven pueden diferir de lo que se describe en la **ayuda** , en función de la edición o configuración activa.  Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Cómo: crear un cuadro de diálogo](../windows/creating-a-new-dialog-box.md)<br/>
[Controles de cuadro de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->
