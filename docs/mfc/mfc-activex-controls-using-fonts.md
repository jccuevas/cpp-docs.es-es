---
title: "Controles ActiveX MFC: Usar fuentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnFontChanged"
  - "HeadingFont"
  - "InternalFont"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fuentes, controles ActiveX"
  - "GetFont (método)"
  - "HeadingFont (propiedad)"
  - "InternalFont (método)"
  - "IPropertyNotifySink (clase)"
  - "controles ActiveX en MFC, fuentes"
  - "notificaciones, fuentes de los controles ActiveX"
  - "OnDraw (método), controles ActiveX en MFC"
  - "OnFontChanged (método)"
  - "SelectStockFont (método)"
  - "SetFont (método)"
  - "Stock Font (propiedad)"
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Controles ActiveX MFC: Usar fuentes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si el control ActiveX text, puede permitir al usuario del control cambie la apariencia del texto cambiar una propiedad de la fuente.  Las propiedades de fuente se implementan como objetos de fuente y pueden ser de dos tipos: acción o personalizado.  Las propiedades de fuente comunes son las propiedades de fuente preimplemented que puede agregar utilizando el asistente para agregar propiedades.  Las propiedades de fuente personalizadas no preimplemented y el programador de controles determina el comportamiento y el uso de la propiedad.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Mediante la propiedad de fuente común](#_core_using_the_stock_font_property)  
  
-   [Utilizando propiedades de fuente personalizadas en el Control de El](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a> Mediante la propiedad de fuente común  
 Las propiedades de fuente comunes preimplemented por la clase [COleControl](../mfc/reference/colecontrol-class.md).  Además, una página de propiedades de fuente estándar también está disponible, lo que el usuario cambie los distintos atributos de objeto font, como su nombre, tamaño, y estilo.  
  
 Tenga acceso a la fuente con [GetFont](../Topic/COleControl::GetFont.md), [SetFont](../Topic/COleControl::SetFont.md), y las funciones de [InternalGetFont](../Topic/COleControl::InternalGetFont.md) de `COleControl`.  El usuario del control tendrá acceso a la fuente mediante `GetFont` y `SetFont` funciona de la misma forma que cualquier otro obtiene y establece la propiedad.  Cuando el acceso a la fuente se requiere dentro de un control, utilice la función de `InternalGetFont` .  
  
 Como se describe en [Controles ActiveX de MFC: Propiedades](../mfc/mfc-activex-controls-properties.md), agregar propiedades estándar es fácil con [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).  Elija la propiedad font, y el asistente para agregar inserta automáticamente la entrada habitual de la del mapa de envío del control.  
  
#### Para agregar la propiedad de fuente habituales mediante el asistente para agregar propiedades  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
     Se abrirá el asistente para agregar propiedades.  
  
5.  En el cuadro de **Nombre de propiedad** , haga clic en **font**.  
  
6.  Haga clic en **Finalizar**.  
  
 El asistente para agregar agrega la línea siguiente al mapa de envío del control, ubicado en el archivo de implementación de la clase de control:  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_1.cpp)]  
  
 Además, el asistente para agregar agrega la línea siguiente al archivo del control .IDL:  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_2.idl)]  
  
 La propiedad caption común es un ejemplo de una propiedad de texto que se puede dibujar utilizando la información bursátil de la propiedad de la fuente.  Agregar la propiedad caption común al control utiliza los pasos similares a los empleados para la propiedad de fuente común.  
  
#### Para agregar la propiedad caption habituales mediante el asistente para agregar propiedades  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
     Se abrirá el asistente para agregar propiedades.  
  
5.  En el cuadro de **Nombre de propiedad** , haga clic en **caption**.  
  
6.  Haga clic en **Finalizar**.  
  
 El asistente para agregar agrega la línea siguiente al mapa de envío del control, ubicado en el archivo de implementación de la clase de control:  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a> Modificar la función de OnDraw  
 La implementación predeterminada de `OnDraw` utiliza la fuente del sistema de Windows para todo el texto mostrado en el control.  Esto significa que debe modificar el código de `OnDraw` seleccionando el objeto de fuente en el contexto del dispositivo.  Para ello, llame [COleControl::SelectStockFont](../Topic/COleControl::SelectStockFont.md) y pase el contexto de dispositivo de control, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_4.cpp)]  
  
 Después de que la función de `OnDraw` se ha modificado para utilizar el objeto de fuente, cualquier texto dentro del control se muestra con características de la propiedad de la fuente de control.  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a> Utilizando propiedades de fuente personalizadas en el Control de El  
 Además de la propiedad de fuente común, el control ActiveX puede tener propiedades de fuente personalizadas.  Para agregar una propiedad de la fuente personalizada debe:  
  
-   Utilice el asistente para agregar propiedades para implementar la propiedad de la fuente personalizada.  
  
-   [Notificaciones de la fuente de procesamiento](#_core_processing_font_notifications).  
  
-   [Implementar una nueva interfaz de notificación de fuente](#_core_implementing_a_new_font_notification_interface).  
  
###  <a name="_core_implementing_a_custom_font_property"></a> Implementar una propiedad de la fuente personalizada  
 Para implementar una propiedad de la fuente personalizada, se utiliza el asistente para agregar propiedades para agregar propiedades y después para crear algunas modificaciones al código.  Las secciones siguientes se describe cómo agregar la propiedad personalizada de `HeadingFont` al control de ejemplo.  
  
##### Para agregar la propiedad de la fuente personalizada mediante el asistente para agregar propiedades  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
     Se abrirá el asistente para agregar propiedades.  
  
5.  En el cuadro de **Nombre de propiedad** , escriba un nombre para la propiedad.  Para este ejemplo, utilice **HeadingFont**.  
  
6.  Para **Tipo de implementación**, haga clic en **Get\/Set Methods**.  
  
7.  En el cuadro de **Tipo de propiedad** , seleccione **IDispatch\*** para el tipo de propiedad.  
  
8.  Haga clic en **Finalizar**.  
  
 El asistente para agregar crea código para agregar la propiedad personalizada de `HeadingFont` a la clase de `CSampleCtrl` y archivo de SAMPLE.IDL.  Dado que `HeadingFont` es un tipo de propiedad get\/set, el asistente para agregar modifica el mapa del envío de la clase de `CSampleCtrl` para incluir una entrada de macro de `DISP_PROPERTY_EX_ID`[DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md) :  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_5.cpp)]  
  
 La macro de `DISP_PROPERTY_EX` asocia el nombre de propiedad de `HeadingFont` a su clase correspondiente de `CSampleCtrl` get y set, `GetHeadingFont` y `SetHeadingFont`.  Especifique el tipo de valor de propiedad también; en este caso, **VT\_FONT**.  
  
 El asistente para agregar también agrega una declaración en el archivo de encabezado del control \(. H\) para `GetHeadingFont` y `SetHeadingFont` funciona y agrega sus plantillas de función en el archivo de implementación del control \(.CPP\):  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_6.cpp)]  
  
 Finalmente, el asistente para agregar modifica el archivo del control .IDL agregando una entrada para la propiedad de `HeadingFont` :  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_7.idl)]  
  
### Modificaciones al código de control  
 Ahora que ha agregado la propiedad de `HeadingFont` al control, debe realizar algunos cambios en el encabezado del control y los archivos de implementación para permitir totalmente la nueva propiedad.  
  
 En el archivo de encabezado del control \(. H\), agregue la siguiente declaración de una variable miembro protegida:  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_8.h)]  
  
 En el archivo de implementación del control \(.CPP\), haga lo siguiente:  
  
-   Inicializa `m_fontHeading` en el constructor del control.  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   Declare una estructura estática de **FONTDESC** que contiene los atributos predeterminados de la fuente.  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   En la función miembro de `DoPropExchange` de control, agregue una llamada a la función de `PX_Font` .  Esto proporciona la inicialización y la persistencia para la propiedad de la fuente personalizada.  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   Final que implementa la función miembro de `GetHeadingFont` del control.  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   Final que implementa la función miembro de `SetHeadingFont` del control.  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   Modifique la función miembro de `OnDraw` de control para definir una variable para contener la fuente seleccionada anteriormente.  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   Modifique la función miembro de `OnDraw` de control para seleccionar la fuente personalizada en el contexto de dispositivo agregando la siguiente línea donde la fuente debe utilizarse.  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   Modifique la función miembro de `OnDraw` de control para seleccionar la fuente anterior de vuelta en el contexto de dispositivo agregando la siguiente línea después de haber utilizado para la fuente.  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_16.cpp)]  
  
 Después de implementar la propiedad de la fuente personalizada, la página de propiedades de fuente estándar se debe implementar, permitiendo a los usuarios del control para cambiar la fuente del control actual.  Para agregar el identificador de la página de propiedades de la página de propiedades de fuente estándar, inserte la línea siguiente después de la macro de `BEGIN_PROPPAGEIDS` :  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_17.cpp)]  
  
 Se debe aumentar el parámetro count de la macro de `BEGIN_PROPPAGEIDS` por una.  La siguiente línea muestra esto:  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_18.cpp)]  
  
 Después de que se hayan realizado estos cambios, recompile el proyecto completo de incorporar la funcionalidad adicional.  
  
###  <a name="_core_processing_font_notifications"></a> Notificaciones de la fuente de procesamiento  
 En la mayoría de los casos el control debe saber cuándo las características de objeto de fuente se han modificado.  Cada objeto de fuente es capaz de proporcionar notificaciones cuando cambia llamando a una función miembro de interfaz de **IFontNotification** , implementado por `COleControl`.  
  
 Si el control utiliza la propiedad de fuente común, las notificaciones se controlan mediante la función miembro de `OnFontChanged` de `COleControl`.  Cuando agrega propiedades de fuente personalizadas, puede hacer que utilicen la misma implementación.  En el ejemplo de la sección anterior, se ha conseguido pasando &**m\_xFontNotification** al inicializar la variable miembro de **m\_fontHeading** .  
  
 ![Implementar varias interfaces de objetos de fuente](../mfc/media/vc373q1.png "vc373Q1")  
Implementar varias interfaces de objetos de fuente  
  
 Las líneas continuas en la ilustración anterior muestran que ambos objetos de fuente utilizan la misma implementación de **IFontNotification**.  Esto podría producir problemas si desea distinguir que la fuente modificado.  
  
 Una manera de distinguir entre las notificaciones del objeto de la fuente del control es crear una implementación distinta de la interfaz de **IFontNotification** para cada objeto de fuente en el control.  Esta técnica le permite optimizar código de dibujo actualizando sólo la cadena, o cadenas, que usan la fuente recién modificada.  Las secciones siguientes muestran los pasos necesarios para implementar las interfaces independientes de notificación para una segunda propiedad de fuente.  La segunda propiedad de fuente se supone que la propiedad de `HeadingFont` que se agregó en la sección anterior.  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a> Implementar una interfaz de notificación de fuente New  
 Para diferenciar las notificaciones de dos o más fuentes, una nueva interfaz de notificación se debe implementar para cada fuente utilizada en el control.  Las secciones siguientes describen cómo implementar una nueva interfaz de notificación de fuente modificando el encabezado del control y los archivos de implementación.  
  
### Adiciones al archivo de encabezado  
 En el archivo de encabezado del control \(. H\), agregue las siguientes líneas a la declaración de clase:  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_19.h)]  
  
 Esto crea una implementación de la interfaz de `IPropertyNotifySink` denominada `HeadingFontNotify`.  Esta nueva interfaz contiene un método denominado `OnChanged`.  
  
### Adiciones al archivo de implementación  
 En el código que inicializa la fuente del encabezado \(en el constructor del control\), cambie `&m_xFontNotification` a `&m_xHeadingFontNotify`.  A continuación agregue el código siguiente:  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_20.cpp)]  
  
 Los métodos de `AddRef` y de `Release` en la interfaz de `IPropertyNotifySink` no realizan un seguimiento del recuento de referencias para el objeto de control ActiveX.  Cuando el control obtiene acceso al puntero de interfaz, el control llama a `AddRef` para incrementar el recuento de referencias.  Cuando el control se finalice el puntero, llama a `Release`, casi de la misma manera que **GlobalFree** se puede llamar para liberar un bloque de memoria global.  Cuando el recuento de referencias para esta interfaz va a cero, la implementación de interfaz puede ser liberado.  En este ejemplo, la función de `QueryInterface` devuelve un puntero a una interfaz de `IPropertyNotifySink` de un objeto concreto.  Esta función permite que un control ActiveX vea un objeto para determinar qué interfaces admite.  
  
 Después de que estos cambios se han realizado en el proyecto, recompile el contenedor de prueba del uso de probar la interfaz.  Vea [Probar propiedades y eventos con Test Container](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo tener acceso a Test Container.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Utilizar imágenes en un control ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)