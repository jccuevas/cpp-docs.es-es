---
title: Diseño dinámico | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e0fcfff6bcca8cb073c337043490d32f8724aad
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930357"
---
# <a name="dynamic-layout"></a>Diseño dinámico
Con MFC en Visual Studio 2015, puede crear cuadros de diálogo que el usuario puede cambiar el tamaño y se puede controlar la manera en que el diseño se ajusta al cambio de tamaño. Por ejemplo, puede adjuntar los botones de la parte inferior de un diálogo al borde inferior para que permanezcan siempre en la parte inferior. También puede configurar ciertos controles, como cuadros de lista, cuadros de edición y campos de texto, para que se expandan cuando el usuario expanda el diálogo.  
  
## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Especificar una configuración de diseño dinámico para un cuadro de diálogo de MFC  
 Cuando el usuario cambia el tamaño de un diálogo, los controles del diálogo pueden cambiar de tamaño o moverse en las direcciones X e Y. El cambio de tamaño o posición de un control cuando el usuario cambia el tamaño de un diálogo se denomina diseño dinámico. Por ejemplo, el siguiente es un diálogo antes de que se cambie su tamaño:  
  
 ![Cuadro de diálogo antes de que se va a cambiar de tamaño. ] (../mfc/media/mfcdynamiclayout4.png "mfcdynamiclayout4")  
  
 Después de que se haya cambiado su tamaño, se incrementa el área del cuadro de lista para que se muestren más elementos y los botones se mueven junto con la esquina inferior derecha:  
  
 ![Cuadro de diálogo después de que se va a cambiar de tamaño. ] (../mfc/media/mfcdynamiclayout5.png "mfcdynamiclayout5")  
  
 Puede controlar el diseño dinámico especificando los detalles de cada control en el Editor de recursos en el IDE, o puede hacer mediante programación mediante el acceso a la `CMFCDynamicLayout` de objeto para un control determinado y estableciendo las propiedades.  
  
### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Configurar las propiedades de diseño dinámico en el editor de recursos  
 Mediante el editor de recursos puede configurar el comportamiento del diseño dinámico de un cuadro de diálogo sin tener que escribir código alguno.  
  
##### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Para configurar las propiedades del diseño dinámico en el editor de recursos  
  
1.  Con un proyecto de MFC abierto, abra el diálogo sobre el que desee trabajar en el editor de diálogos.  
  
     ![Abra el cuadro de diálogo en el editor de recursos. ] (../mfc/media/mfcdynamiclayout3.png "mfcdynamiclayout3")  
  
2.  Seleccione un control y en la ventana de propiedades, configure las propiedades del diseño dinámico. El **diseño dinámico** sección en la ventana Propiedades contiene las propiedades **tipo móvil**, **tipo de ajuste de tamaño**y, dependiendo de los valores seleccionados para las propiedades propiedades específicas que definen cuánto controles mover o cambiar el tamaño. **Tipo móvil** determina cómo se mueve un control como se cambia el tamaño del cuadro de diálogo; **Tipo de ajuste de tamaño** determina cómo se cambia el tamaño de un control como se cambia el tamaño del cuadro de diálogo. **Tipo móvil** y **tipo de ajuste de tamaño** puede ser **Horizontal**, **Vertical**, **ambos**, o **ninguno**según las dimensiones que desea cambiar de forma dinámica. Horizontal es la dimensión X, mientras que Vertical es la dirección del eje Y.  
  
3.  Si desea que un control como un botón en un tamaño fijo y permanece en la parte inferior derecha, como es habitual para los **Aceptar** o **cancelar** botones, establezca la **tipo de ajuste de tamaño** a  **Ninguno**y establezca el **tipo móvil** a **ambos**. Para el **X móvil** y **Y móvil** valores en **tipo móvil**, establezca el 100% para que el control permanezca a una distancia fija desde la parte inferior derecha.  
  
     ![Diseño dinámico](../mfc/media/mfcdynamiclayout1.png "mfcdynamiclayout1")  
  
4.  Supongamos que también tiene un control que quiere que se expanda a medida que se expanda el diálogo. Normalmente los usuarios expanden un diálogo para que se expanda un cuadro de edición de varias líneas y aumentar así el tamaño del área de texto o expanden un control de lista para poder ver más datos. En este caso, establezca el **tipo de ajuste de tamaño** a ambos y establezca el **tipo móvil** en none. A continuación, establezca el **X de ajuste de tamaño** y **Y de ajuste de tamaño** valores a 100.  
  
     ![Configuración de diseño dinámico](../mfc/media/mfcdynamiclayout2.png "mfcdynamiclayout2")  
  
5.  Pruebe otros valores que podrían tener sentido para sus controles. Un cuadro de diálogo con un cuadro de texto de una línea podría tener la **tipo de ajuste de tamaño** establecido en **Horizontal** solamente, por ejemplo.  
  
### <a name="setting-dynamic-layout-properties-programmatically"></a>Configurar las propiedades del diseño dinámico mediante programación  
 El procedimiento anterior es útil para configurar las propiedades del diseño dinámico de diálogo en tiempo de diseño, pero si desea controlar el diseño dinámico en tiempo de ejecución, puede configurar las propiedades del diseño dinámico mediante programación.  
  
##### <a name="to-set-dynamic-layout-properties-programmatically"></a>Para configurar las propiedades del diseño dinámico mediante programación  
  
1.  Busque o cree un lugar en el código de implementación de la clase de su diálogo donde desee especificar el diseño dinámico del diálogo. Por ejemplo, puede que quiera agregar un método `AdjustLayout` en el diálogo y llamarlo desde los lugares donde se deba cambiar el diseño. Podría llamar primero a este método desde el constructor o después de haber realizado cambios en el diálogo.  
  
2.  En el cuadro de diálogo, llame [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), un método de la `CWnd` clase. `GetDynamicLayout` Devuelve un puntero a un `CMFCDynamicLayout` objeto.  
  
 ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();

 ```  
  
3.  Para el primer control al que desea agregar el comportamiento dinámico, utilice los métodos estáticos en la clase de diseño dinámico para crear el [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) estructura que codifica la forma en que el control debe ajustarse. Para ello, elija en primer lugar el método estático apropiado: [CMFCDynamicLayout::MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout::MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout::MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone), o [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Se pasa un porcentaje de los aspectos horizontales o verticales del movimiento. Todos estos métodos estáticos devuelven un objeto MoveSettings recién creado que se puede utilizar para especificar el comportamiento de movimiento de un control.  
  
     Tenga en cuenta que 100 significa que el control se moverá exactamente la misma cantidad que se cambie de tamaño el diálogo, lo que hace que el borde de un control permanezca a una distancia fija del nuevo borde.  
  
 ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);

 ```  
  
4.  Haga lo mismo para el comportamiento de tamaño, que usa el [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) tipo. Por ejemplo, para especificar que un control no cambie de tamaño cuando lo haga el diálogo, utilice el siguiente código:  
  
 ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();

 ```  
  
5.  Agregue el control al administrador de diseño dinámico mediante el [cmfcdynamiclayout:: AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) método. Hay dos sobrecargas para las distintas formas de especificar el control deseado. Una toma el identificador de ventana del control (HWND) y la otra toma el identificador del control.  
  
 ```  
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);

 ```  
  
6.  Repita este procedimiento para cada control que se deba mover o cambiar de tamaño.  
  
7.  Si es necesario, puede usar el [cmfcdynamiclayout:: Hasitem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) método para determinar si un control ya está en la lista de controles sujetos a cambios de diseño dinámico o [cmfcdynamiclayout:: IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) método para determinar si existen todos los controles que están sujetos a cambios.  
  
8.  Para habilitar el diseño del cuadro de diálogo, llame a la [CWnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) método.  
  
 ```  
    pDialog->EnableDynamicLayout(TRUE);

 ```  
  
9. La próxima vez que el usuario cambia el tamaño del cuadro de diálogo, el [cmfcdynamiclayout:: Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust) se llama al método que aplica realmente la configuración.  
  
10. Si desea deshabilitar el diseño dinámico, llame a [CWnd:: Enabledynamiclayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) con **FALSE** como para la *bHabilitado* parámetro.  
  
 ```  
    pDialog->EnableDynamicLayout(FALSE);

 ```  
  
##### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Para configurar el diseño dinámico mediante programación desde un archivo de recursos  
  
1.  Use la [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) método para especificar un nombre de recurso en el archivo de script de recursos correspondiente (archivo .rc) que especifica la información de diseño dinámico, como en el ejemplo siguiente:  
  
 ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");

 ```  
  
     El recurso con nombre debe hacer referencia a un cuadro de diálogo que contiene información de diseño en forma de un **AFX_DIALOG_LAYOUT** entrada en el archivo de recursos, como en el ejemplo siguiente:  
  
 ''' * / / / * / / * / / AFX_DIALOG_LAYOUT * / /  
 
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    EMPEZAR A 0 X 0000, 0X6400, 0 X 0028, 0X643C, 0 X 0028  
    FIN 
 
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    EMPEZAR A 0 X 0000, 0X6464, 0 X 0000, 0X6464, 0 X 0000, 0 X 0000, 0X6464, 0 X 0000, 0 X 0000  
 
    FIN 
 ```  
  
## See Also  
 [CMFCDynamicLayout Class](../mfc/reference/cmfcdynamiclayout-class.md)   
 [Control Classes](../mfc/control-classes.md)   
 [Dialog Box Classes](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../windows/dialog-editor.md)

