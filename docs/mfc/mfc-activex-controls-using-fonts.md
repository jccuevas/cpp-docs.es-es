---
title: 'Controles ActiveX MFC: Usar fuentes | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f5d1475412de736970d0ae36a39540121bfbc01
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930720"
---
# <a name="mfc-activex-controls-using-fonts"></a>Controles ActiveX MFC: Usar fuentes
Si el control ActiveX muestra texto, puede permitir que el usuario del control cambiar la apariencia del texto cambiando una propiedad de fuente. Propiedades de fuente se implementan como objetos de fuente y puede tener uno de dos tipos: estándar o personalizadas. Propiedades de fuente estándar son propiedades de fuente ya implementadas y que se pueden agregar mediante el Asistente para agregar propiedades. Propiedades de fuente personalizados no están implementadas y el desarrollador del control determina el comportamiento y el uso de la propiedad.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Mediante la propiedad Font estándar](#_core_using_the_stock_font_property)  
  
-   [Usar propiedades de fuente personalizado en el Control](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a> Mediante la propiedad Font estándar  
 Propiedades de fuente estándar ya están implementadas por la clase [COleControl](../mfc/reference/colecontrol-class.md). Además, una página de propiedades de fuente estándar también está disponible, lo que permite al usuario cambiar varios atributos del objeto de fuente, como su nombre, el tamaño y el estilo.  
  
 Obtener acceso al objeto de fuente a través de la [GetFont](../mfc/reference/colecontrol-class.md#getfont), [SetFont](../mfc/reference/colecontrol-class.md#setfont), y [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) funciones de `COleControl`. El usuario de control tendrá acceso el objeto de fuente a través de la `GetFont` y `SetFont` las funciones de la misma manera que cualquier otra propiedad Get/Set. Cuando se requiere desde dentro de un control de acceso para el objeto de fuente, utilice el `InternalGetFont` función.  
  
 Como se describe en [controles ActiveX MFC: propiedades](../mfc/mfc-activex-controls-properties.md), agregar propiedades estándar es fácil con el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md). Elija la propiedad de fuente y el Asistente para agregar propiedades inserta automáticamente la entrada de fuente estándar en el mapa de envíos del control.  
  
#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Para agregar la propiedad Font estándar mediante el Asistente para agregar propiedades  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
     Se abrirá al Asistente para agregar propiedades.  
  
5.  En el **nombre de la propiedad** cuadro, haga clic en **fuente**.  
  
6.  Haga clic en **Finalizar**.  
  
 El Asistente para agregar propiedades agrega la siguiente línea al mapa de envíos del control, ubicado en el archivo de implementación de la clase de control:  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]  
  
 Además, el Asistente para agregar propiedades agrega la siguiente línea al control. Este archivo IDL:  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]  
  
 La propiedad estándar Caption es un ejemplo de una propiedad de texto que se puede dibujar con la información de propiedad de fuente estándar. Agregar la propiedad Caption estándar al control usa unos pasos similares a los que se usan para la propiedad Font estándar.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Para agregar la propiedad de título estándar mediante el Asistente para agregar propiedades  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
     Se abrirá al Asistente para agregar propiedades.  
  
5.  En el **nombre de la propiedad** cuadro, haga clic en **título**.  
  
6.  Haga clic en **Finalizar**.  
  
 El Asistente para agregar propiedades agrega la siguiente línea al mapa de envíos del control, ubicado en el archivo de implementación de la clase de control:  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a> Modificar la función OnDraw  
 La implementación predeterminada de `OnDraw` utiliza la fuente de sistema de Windows para todo el texto mostrado en el control. Esto significa que debe modificar el `OnDraw` código seleccionando el objeto de fuente en el contexto de dispositivo. Para ello, llame a [COleControl:: SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) y pase el contexto de dispositivo del control, tal como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]  
  
 Después de la `OnDraw` función se ha modificado para utilizar el objeto de fuente, cualquier texto dentro del control se muestra con las características de la propiedad Font estándar del control.  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a> Usar propiedades de fuente personalizado en el Control  
 Además de la propiedad Font estándar, el control ActiveX puede tener propiedades de fuente personalizados. Para agregar una propiedad de fuente personalizada debe:  
  
-   Usar al Asistente para agregar propiedades para implementar la propiedad Font personalizada.  
  
-   [Procesar notificaciones de fuente](#_core_processing_font_notifications).  
  
-   [Implementar una nueva interfaz de notificación de fuente](#_core_implementing_a_new_font_notification_interface).  
  
###  <a name="_core_implementing_a_custom_font_property"></a> Implementar una propiedad de fuente personalizada  
 Para implementar una propiedad Font personalizada, usa al Asistente para agregar propiedades para agregar la propiedad y, a continuación, realizar algunas modificaciones en el código. Las secciones siguientes describen cómo agregar personalizado `HeadingFont` propiedad para el control de ejemplo.  
  
##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Para agregar la propiedad Font personalizada mediante el Asistente para agregar propiedades  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
     Se abrirá al Asistente para agregar propiedades.  
  
5.  En el **nombre de la propiedad** , escriba un nombre para la propiedad. En este ejemplo, utilice **HeadingFont**.  
  
6.  Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.  
  
7.  En el **tipo de propiedad** cuadro, seleccione **IDispatch\***  para el tipo de propiedad.  
  
8.  Haga clic en **Finalizar**.  
  
 El Asistente para agregar propiedades crea el código para agregar el `HeadingFont` propiedad personalizada a la `CSampleCtrl` clase y el ejemplo. Este archivo IDL. Dado que `HeadingFont` es un tipo de propiedad Get/Set, el Asistente para agregar propiedades modifica el `CSampleCtrl` mapa de envíos de la clase para incluir un DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) entrada de macro:  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]  
  
 La macro DISP_PROPERTY_EX asocia el `HeadingFont` nombre de la propiedad con el correspondiente `CSampleCtrl` clase métodos Get y Set, `GetHeadingFont` y `SetHeadingFont`. También se especifica el tipo del valor de propiedad; en este caso, VT_FONT.  
  
 El Asistente para agregar propiedades también agrega una declaración en el archivo de encabezado (. (H) para la `GetHeadingFont` y `SetHeadingFont` las funciones y los agrega sus plantillas de función en el archivo de implementación (. CPP):  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]  
  
 Por último, el Asistente para agregar propiedades modifica el control. Este archivo IDL agregando una entrada para el `HeadingFont` propiedad:  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]  
  
### <a name="modifications-to-the-control-code"></a>Modificaciones en el código de Control  
 Ahora que ha agregado el `HeadingFont` propiedad al control, debe realizar algunos cambios en los archivos de encabezado e implementación del control para poder admitir la nueva propiedad.  
  
 En el archivo de encabezado (. (H), agregue la siguiente declaración de una variable de miembro protegido:  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]  
  
 En el archivo de implementación (. (CPP), haga lo siguiente:  
  
-   Inicializar *m_fontHeading* en el constructor del control.  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   Declarar una estructura estática FONTDESC que contenga atributos predeterminados de la fuente.  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   En el control `DoPropExchange` miembro de función, agregue una llamada a la `PX_Font` (función). Esto proporciona inicialización y persistencia de la propiedad personalizada de la fuente.  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   Termine de implementar el control `GetHeadingFont` función miembro.  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   Termine de implementar el control `SetHeadingFont` función miembro.  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   Modificar el control `OnDraw` función de miembro para definir una variable para que contenga la fuente previamente seleccionada.  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   Modificar el control `OnDraw` función de miembro para seleccionar la fuente personalizada en el contexto de dispositivo agregando la siguiente línea siempre que la fuente que se usará.  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   Modificar el control `OnDraw` función de miembro para seleccionar la fuente anterior en el contexto de dispositivo agregando la siguiente línea después de que se ha utilizado la fuente.  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]  
  
 Después de haber implementado la propiedad Font personalizada, se debe implementar la página de propiedades de fuente estándar, permitiendo a los usuarios de control cambiar la fuente del control actual. Para agregar el identificador de página de propiedades para la página de propiedades de fuente estándar, inserte la siguiente línea después de la macro BEGIN_PROPPAGEIDS:  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]  
  
 También debe incrementar el parámetro de recuento de la macro BEGIN_PROPPAGEIDS en uno. Esto se ilustra en la línea siguiente:  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]  
  
 Una vez realizados estos cambios, vuelva a generar todo el proyecto para incorporar la funcionalidad adicional.  
  
###  <a name="_core_processing_font_notifications"></a> Procesar notificaciones de fuente  
 En la mayoría de los casos, el control necesita saber cuándo se han modificado las características del objeto font. Cada objeto de fuente es capaz de proporcionar notificaciones cuando el estado cambia mediante una llamada a una función miembro de la `IFontNotification` interfaz, implementada por `COleControl`.  
  
 Si el control utiliza la propiedad Font estándar, sus notificaciones se administran mediante el `OnFontChanged` función miembro de `COleControl`. Al agregar propiedades de fuente personalizada, puede hacer que utilicen la misma implementación. En el ejemplo en la sección anterior, esto se lograba haciendo pasar &*m_xFontNotification* al inicializar el *m_fontHeading* variable miembro.  
  
 ![Implementar varias interfaces del objeto de fuente](../mfc/media/vc373q1.gif "vc373q1")  
Implementar varias interfaces de objetos de fuente  
  
 Las líneas sólidas en la ilustración anterior muestran que ambos objetos fuente utilizan la misma implementación de `IFontNotification`. Esto podría producir problemas si quisiera distinguir qué fuente ha cambiado.  
  
 Una manera de distinguir entre notificaciones de objetos de fuente del control consiste en crear una implementación independiente de la `IFontNotification` interfaz para cada objeto de fuente del control. Esta técnica permite optimizar el código de dibujo actualizando sólo la cadena, o cadenas, que utilizan la fuente recién modificada. Las secciones siguientes muestran los pasos necesarios para implementar interfaces de notificación independientes para una segunda propiedad de fuente. La segunda propiedad de fuente se supone que el `HeadingFont` propiedad que se agregó en la sección anterior.  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a> Implementar una nueva interfaz de notificación de fuente  
 Para distinguir entre las notificaciones de dos o más fuentes, se debe implementar una nueva interfaz de notificación para cada fuente utilizada en el control. Las secciones siguientes describen cómo implementar una nueva interfaz de notificación de fuente modificando los archivos de encabezado e implementación del control.  
  
### <a name="additions-to-the-header-file"></a>Adiciones al archivo de encabezado  
 En el archivo de encabezado (. (H), agregue las siguientes líneas a la declaración de clase:  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]  
  
 Esto crea una implementación de la `IPropertyNotifySink` interfaz denominada `HeadingFontNotify`. Esta nueva interfaz contiene un método denominado `OnChanged`.  
  
### <a name="additions-to-the-implementation-file"></a>Adiciones al archivo de implementación  
 En el código que inicializa la fuente del título (en el constructor del control), cambie &*m_xFontNotification* a &*m_xHeadingFontNotify*. A continuación, agregue el código siguiente:  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]  
  
 El `AddRef` y `Release` métodos en el `IPropertyNotifySink` interfaz realizar un seguimiento del recuento de referencias para el objeto de control ActiveX. Cuando el control obtiene acceso al puntero de interfaz, el control llama a `AddRef` para incrementar el recuento de referencias. Cuando el control está finalizando con el puntero, llama al método `Release`, de igual forma en que `GlobalFree` podría denominarse para liberar un bloque de memoria global. Cuando el recuento de referencias para esta interfaz llega a cero, se puede liberar la implementación de interfaz. En este ejemplo, el `QueryInterface` función devuelve un puntero a un `IPropertyNotifySink` interfaz en un objeto determinado. Esta función permite que un control ActiveX consultar un objeto para determinar qué interfaces admite.  
  
 Una vez realizados estos cambios a su proyecto, recompile el proyecto y utilice Test Container para probar la interfaz. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Utilizar imágenes en un Control ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)

