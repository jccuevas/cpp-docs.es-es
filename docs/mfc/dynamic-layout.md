---
title: Diseño dinámico
ms.date: 09/09/2019
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 1b0d035d3c551fd309d515ccb8b22159218c1b0a
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "70907547"
---
# <a name="dynamic-layout"></a>Diseño dinámico

Con MFC en Visual Studio 2015, puede crear cuadros de diálogo que el usuario puede cambiar de tamaño y puede controlar la manera en que el diseño se ajusta al cambio de tamaño. Por ejemplo, puede adjuntar los botones de la parte inferior de un diálogo al borde inferior para que permanezcan siempre en la parte inferior. También puede configurar ciertos controles, como cuadros de lista, cuadros de edición y campos de texto, para que se expandan cuando el usuario expanda el diálogo.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Especificar una configuración de diseño dinámico para un cuadro de diálogo de MFC

Cuando el usuario cambia el tamaño de un diálogo, los controles del diálogo pueden cambiar de tamaño o moverse en las direcciones X e Y. El cambio de tamaño o posición de un control cuando el usuario cambia el tamaño de un diálogo se denomina diseño dinámico. Por ejemplo, el siguiente es un diálogo antes de que se cambie su tamaño:

![Cuadro de diálogo antes de cambiar el tamaño.](../mfc/media/mfcdynamiclayout4.png "Diálogo antes de modificar el tamaño.")

Después de que se haya cambiado su tamaño, se incrementa el área del cuadro de lista para que se muestren más elementos y los botones se mueven junto con la esquina inferior derecha:

![Cuadro de diálogo después de cambiar el tamaño.](../mfc/media/mfcdynamiclayout5.png "Dialogo tras modificar el tamaño.")

Puede controlar el diseño dinámico especificando los detalles de cada control en el editor de recursos en el IDE, o puede hacerlo mediante programación accediendo al objeto `CMFCDynamicLayout` para un control determinado y estableciendo las propiedades.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Configurar las propiedades de diseño dinámico en el editor de recursos

Mediante el editor de recursos puede configurar el comportamiento del diseño dinámico de un cuadro de diálogo sin tener que escribir código alguno.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Para configurar las propiedades del diseño dinámico en el editor de recursos

1. Con un proyecto de MFC abierto, abra el diálogo sobre el que desee trabajar en el editor de diálogos.

   ![Abra el cuadro de diálogo en el editor de recursos.](../mfc/media/mfcdynamiclayout3.png "Abra el diálogo en el editor de recursos.")

1. Seleccione un control y, en la ventana **propiedades** (en **vista de clases**), establezca sus propiedades de diseño dinámico. La sección **diseño dinámico** de la ventana **propiedades** contiene las propiedades **tipo móvil**, **tipo de ajuste de tamaño**y, dependiendo de los valores seleccionados para esas propiedades, propiedades específicas que definen cuánto se mueven los controles o cambiar tamaño. El **tipo de movimiento** determina cómo se mueve un control a medida que cambia el tamaño del cuadro de diálogo; **Tipo de ajuste** de tamaño determina cómo se cambia el tamaño de un control a medida que cambia el tamaño del cuadro de diálogo. El tipo de **movimiento** y el **tipo de ajuste de tamaño** pueden ser **horizontal**, **vertical**, **ambos**o **ninguno** , según las dimensiones que desee cambiar de forma dinámica. Horizontal es la dimensión X, mientras que Vertical es la dirección del eje Y.

1. Si desea que un control como un botón tenga un tamaño fijo y permanezca en la parte inferior derecha, como es habitual en los botones **Aceptar** o **Cancelar** , establezca el tipo de ajuste de **tamaño** en **ninguno**y establezca el tipo de **movimiento** en **ambos**. Para los valores **X** y **móvil** en movimiento en **tipo móvil**, establezca 100% para que el control permanezca a una distancia fija desde la esquina inferior derecha.

   ![Diseño dinámico](../mfc/media/mfcdynamiclayout1.png "Diseño dinámico")

1. Supongamos que también tiene un control que quiere que se expanda a medida que se expanda el diálogo. Normalmente los usuarios expanden un diálogo para que se expanda un cuadro de edición de varias líneas y aumentar así el tamaño del área de texto o expanden un control de lista para poder ver más datos. En este caso, establezca el **tipo de ajuste de tamaño** en ambos y establezca el **tipo de movimiento** en ninguno. Después, establezca el **ajuste de tamaño** de los valores **y** en 100.

   ![Configuración de diseño dinámico](../mfc/media/mfcdynamiclayout2.png "Configuración de diseño dinámico")

1. Pruebe otros valores que podrían tener sentido para sus controles. Un cuadro de diálogo con un cuadro de texto de una línea podría tener el **tipo de ajuste de tamaño** establecido en solo **horizontal** , por ejemplo.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Configurar las propiedades del diseño dinámico mediante programación

El procedimiento anterior es útil para configurar las propiedades del diseño dinámico de diálogo en tiempo de diseño, pero si desea controlar el diseño dinámico en tiempo de ejecución, puede configurar las propiedades del diseño dinámico mediante programación.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>Para configurar las propiedades del diseño dinámico mediante programación

1. Busque o cree un lugar en el código de implementación de la clase de su diálogo donde desee especificar el diseño dinámico del diálogo. Por ejemplo, puede que quiera agregar un método `AdjustLayout` en el diálogo y llamarlo desde los lugares donde se deba cambiar el diseño. Podría llamar primero a este método desde el constructor o después de haber realizado cambios en el diálogo.

1. En el cuadro de diálogo, llame a [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), un método de la clase `CWnd`. `GetDynamicLayout` devuelve un puntero a un objeto `CMFCDynamicLayout` .

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. Para el primer control al que desea agregar el comportamiento dinámico, use los métodos estáticos de la clase de diseño dinámico para crear la estructura [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) que codifica la manera en que se debe ajustar el control. Para ello, primero debe elegir el método estático adecuado: [CMFCDynamicLayout:: MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout:: MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout:: MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)o [CMFCDynamicLayout:: MoveHorizontalAndVertical ](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Se pasa un porcentaje de los aspectos horizontales o verticales del movimiento. Todos estos métodos estáticos devuelven un objeto MoveSettings recién creado que se puede utilizar para especificar el comportamiento de movimiento de un control.

   Tenga en cuenta que 100 significa que el control se moverá exactamente la misma cantidad que se cambie de tamaño el diálogo, lo que hace que el borde de un control permanezca a una distancia fija del nuevo borde.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. Haga lo mismo para el comportamiento del tamaño, que usa el tipo [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) . Por ejemplo, para especificar que un control no cambie de tamaño cuando lo haga el diálogo, utilice el siguiente código:

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. Agregue el control al administrador de diseño dinámico mediante el método [CMFCDynamicLayout:: AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) . Hay dos sobrecargas para las distintas formas de especificar el control deseado. Una toma el identificador de ventana del control (HWND) y la otra toma el identificador del control.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. Repita este procedimiento para cada control que se deba mover o cambiar de tamaño.

1. Si es necesario, puede usar el método [CMFCDynamicLayout:: HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) para determinar si un control ya está en la lista de controles sometidos a cambios de diseño dinámico o el método [CMFCDynamicLayout:: IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) para determinar si hay controles que están sujetos a cambios.

1. Para habilitar el diseño del cuadro de diálogo, llame al método [CWnd:: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) .

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. La próxima vez que el usuario cambie el tamaño del cuadro de diálogo, se llama al método [CMFCDynamicLayout:: ADJUST](../mfc/reference/cmfcdynamiclayout-class.md#adjust) que realmente aplica la configuración.

1. Si desea deshabilitar el diseño dinámico, llame a [CWnd:: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) con **false** como para el parámetro *bEnabled* .

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Para configurar el diseño dinámico mediante programación desde un archivo de recursos

1. Use el método [CMFCDynamicLayout:: MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) para especificar un nombre de recurso en el archivo de script de recursos (. RC) correspondiente que especifica la información de diseño dinámico, como en el ejemplo siguiente:

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   El recurso con nombre debe hacer referencia a un cuadro de diálogo que contiene información de diseño en forma de una entrada **AFX_DIALOG_LAYOUT** en el archivo de recursos, como en el ejemplo siguiente:

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>Vea también

[CMFCDynamicLayout (clase)](../mfc/reference/cmfcdynamiclayout-class.md)<br/>
[Clases de control](../mfc/control-classes.md)<br/>
[Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)<br/>
[Editor de cuadros de diálogo](../windows/dialog-editor.md)<br/>
[Diseño dinámico de cuadros de diálogo para C++ MFC en Visual 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
