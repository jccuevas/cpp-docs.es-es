---
title: "Dise&#241;o din&#225;mico | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
caps.latest.revision: 7
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dise&#241;o din&#225;mico
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con MFC en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] puede crear diálogos cuyo tamaño puede cambiar el usuario y controlar la manera en que el diseño se ajusta al cambio de tamaño.  Por ejemplo, puede adjuntar los botones de la parte inferior de un diálogo al borde inferior para que permanezcan siempre en la parte inferior.  También puede configurar ciertos controles, como cuadros de lista, cuadros de edición y campos de texto, para que se expandan cuando el usuario expanda el diálogo.  
  
## Especificar una configuración de diseño dinámico para un cuadro de diálogo de MFC  
 Cuando el usuario cambia el tamaño de un diálogo, los controles del diálogo pueden cambiar de tamaño o moverse en las direcciones X e Y.  El cambio de tamaño o posición de un control cuando el usuario cambia el tamaño de un diálogo se denomina diseño dinámico.  Por ejemplo, el siguiente es un diálogo antes de que se cambie su tamaño:  
  
 ![Diálogo antes de modificar el tamaño.](../mfc/media/mfcdynamiclayout4.png "MFCDynamicLayout4")  
  
 Después de que se haya cambiado su tamaño, se incrementa el área del cuadro de lista para que se muestren más elementos y los botones se mueven junto con la esquina inferior derecha:  
  
 ![Dialogo tras modificar el tamaño.](../mfc/media/mfcdynamiclayout5.png "MFCDynamicLayout5")  
  
 Puede controlar el diseño dinámico especificando los detalles de cada control en el Editor de recursos del IDE o mediante programación accediendo al objeto CMFCDynamicLayout de un determinado control y configurando sus propiedades.  
  
### Configurar las propiedades de diseño dinámico en el editor de recursos  
 Mediante el editor de recursos puede configurar el comportamiento del diseño dinámico de un cuadro de diálogo sin tener que escribir código alguno.  
  
##### Para configurar las propiedades del diseño dinámico en el editor de recursos  
  
1.  Con un proyecto de MFC abierto, abra el diálogo sobre el que desee trabajar en el editor de diálogos.  
  
     ![Abra el diálogo en el editor de recursos.](../mfc/media/mfcdynamiclayout3.png "MFCDynamicLayout3")  
  
2.  Seleccione un control y en la ventana de propiedades, configure las propiedades del diseño dinámico.  La sección **Diseño dinámico** de la ventana de propiedades contiene las propiedades **Tipo móvil** y **Tipo de ajuste de tamaño** y, en función de los valores que se seleccionen para esas propiedades, también puede contener las propiedades específicas que definen cuánto se mueven los controles o cuánto cambia su tamaño.  **Tipo móvil**  determina cómo se mueve el control cuando se cambia el tamaño del diálogo, mientras que **Tipo de ajuste de tamaño** determina cómo se cambia el tamaño de un control cuando se modifica el tamaño del diálogo.  Los valores de **Tipo móvil** y **Tipo de ajuste de tamaño** pueden ser: **Horizontal**, **Vertical**, **Ambos** o **Ninguno**, según las dimensiones que desee cambiar de forma dinámica.  Horizontal es la dimensión X, mientras que Vertical es la dirección del eje Y.  
  
3.  Si desea que un control, como puede ser un botón, tenga un tamaño fijo y permanezca en la parte inferior derecha, como suele ser el caso de los botones **Aceptar** o **Cancelar**, establezca el valor de **Tipo de ajuste de tamaño** en **Ninguno** y el de **Tipo móvil** en **Ambos**.  Para los valores de **X móvil** e **Y móvil** bajo **Tipo móvil**, establezca el 100% para que el control permanezca a una distancia fija con respecto a la esquina inferior derecha.  
  
     ![Diseño dinámico](../mfc/media/mfcdynamiclayout1.png "MFCDynamicLayout1")  
  
4.  Supongamos que también tiene un control que quiere que se expanda a medida que se expanda el diálogo.  Normalmente los usuarios expanden un diálogo para que se expanda un cuadro de edición de varias líneas y aumentar así el tamaño del área de texto o expanden un control de lista para poder ver más datos.  En este caso, establezca **Tipo de ajuste de tamaño** en Ambos y **Tipo móvil** en Ninguno.  A continuación, establezca los valores de **X de ajuste de tamaño** e **Y de ajuste de tamaño** en 100.  
  
     ![Configuración de diseño dinámico](../mfc/media/mfcdynamiclayout2.png "MFCDynamicLayout2")  
  
5.  Pruebe otros valores que podrían tener sentido para sus controles.  Un diálogo con un cuadro de texto de una línea podría tener la propiedad **Tipo de ajuste de tamaño** establecida únicamente en **Horizontal**, por ejemplo.  
  
### Configurar las propiedades del diseño dinámico mediante programación  
 El procedimiento anterior es útil para configurar las propiedades del diseño dinámico de diálogo en tiempo de diseño, pero si desea controlar el diseño dinámico en tiempo de ejecución, puede configurar las propiedades del diseño dinámico mediante programación.  
  
##### Para configurar las propiedades del diseño dinámico mediante programación  
  
1.  Busque o cree un lugar en el código de implementación de la clase de su diálogo donde desee especificar el diseño dinámico del diálogo.  Por ejemplo, puede que quiera agregar un método `AdjustLayout` en el diálogo y llamarlo desde los lugares donde se deba cambiar el diseño.  Podría llamar primero a este método desde el constructor o después de haber realizado cambios en el diálogo.  
  
2.  Para el diálogo, llame a [GetDynamicLayout](../Topic/CWnd::GetDynamicLayout.md), un método de la clase CWnd.  GetDynamicLayout devuelve un puntero a un objeto CMFCDynamicLayout.  
  
    ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();  
    ```  
  
3.  Para el primer control al que desee agregar el comportamiento dinámico, utilice los métodos estáticos de la clase de diseño dinámico para crear la estructura [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md), que codifica la forma en que el control debe ajustarse.  Para ello, elija en primer lugar el método estático apropiado: [CMFCDynamicLayout::MoveHorizontal](../Topic/CMFCDynamicLayout::MoveHorizontal.md), [CMFCDynamicLayout::MoveVertical](../Topic/CMFCDynamicLayout::MoveVertical.md), [CMFCDynamicLayout::MoveNone](../Topic/CMFCDynamicLayout::MoveNone.md) o [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md).  Se pasa un porcentaje de los aspectos horizontales o verticales del movimiento.  Todos estos métodos estáticos devuelven un objeto MoveSettings recién creado que se puede utilizar para especificar el comportamiento de movimiento de un control.  
  
     Tenga en cuenta que 100 significa que el control se moverá exactamente la misma cantidad que se cambie de tamaño el diálogo, lo que hace que el borde de un control permanezca a una distancia fija del nuevo borde.  
  
    ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);  
    ```  
  
4.  Haga lo mismo para el comportamiento de tamaño, que utiliza el tipo [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md).  Por ejemplo, para especificar que un control no cambie de tamaño cuando lo haga el diálogo, utilice el siguiente código:  
  
    ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();  
    ```  
  
5.  Agregue el control al administrador de diseño dinámico mediante el método [CMFCDynamicLayout::AddItem](../Topic/CMFCDynamicLayout::AddItem.md).  Hay dos sobrecargas para las distintas formas de especificar el control deseado.  Una toma el identificador de ventana del control \(HWND\) y la otra toma el identificador del control.  
  
    ```  
    dynamicLayout->AddItem(hWndControl, moveSettings, sizeSettings);  
    ```  
  
6.  Repita este procedimiento para cada control que se deba mover o cambiar de tamaño.  
  
7.  Si fuese necesario, puede usar el método [CMFCDynamicLayout::HasItem](../Topic/CMFCDynamicLayout::HasItem.md) para determinar si un control ya está incluido en la lista de controles sujetos a cambios de diseño dinámico o el método [CMFCDynamicLayout::IsEmpty](../Topic/CMFCDynamicLayout::IsEmpty.md) para determinar si existe algún control sujeto a cambios.  
  
8.  Para habilitar el diseño del diálogo, llame al método [CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md).  
  
    ```  
    pDialog->EnableDynamicLayout(TRUE);  
    ```  
  
9. La próxima vez que el usuario cambie el tamaño del cuadro de diálogo, se llama al método [CMFCDynamicLayout::Adjust](../Topic/CMFCDynamicLayout::Adjust.md), que aplica realmente los valores.  
  
10. Si desea deshabilitar el diseño dinámico, llame a [CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md) con `FALSE` como valor del parámetro `bEnabled`.  
  
    ```  
    pDialog->EnableDynamicLayout(FALSE);  
    ```  
  
##### Para configurar el diseño dinámico mediante programación desde un archivo de recursos  
  
1.  Utilice el método [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md) para especificar un nombre de recurso en el archivo de script de recursos correspondiente \(archivo .rc\) que especifica la información del diseño dinámico, como se muestra en el siguiente ejemplo:  
  
    ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");  
    ```  
  
     El recurso con nombre debe hacer referencia a un diálogo que contenga información de diseño en forma de una entrada AFX\_DIALOG\_LAYOUT en el archivo de recursos, como se muestra en el siguiente ejemplo:  
  
    ```  
    /////////////////////////////////////////////////////////////////////////////  
    //  
    // AFX_DIALOG_LAYOUT  
    //  
  
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    BEGIN  
        0x0000, 0x6400, 0x0028, 0x643c, 0x0028  
    END  
  
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    BEGIN  
        0x0000, 0x6464, 0x0000, 0x6464, 0x0000, 0x0000, 0x6464, 0x0000, 0x0000  
  
    END  
    ```  
  
## Vea también  
 [Clase CMFCDynamicLayout](../mfc/reference/cmfcdynamiclayout-class.md)   
 [Clases de control](../mfc/control-classes.md)   
 [Clases de cuadro de diálogo](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../mfc/dialog-editor.md)