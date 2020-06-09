---
title: 'Controles ActiveX MFC: Usar fuentes'
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
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
ms.openlocfilehash: 58f387ba6f4d7cdffb3ffc1f7be6f9acde8314f4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618165"
---
# <a name="mfc-activex-controls-using-fonts"></a>Controles ActiveX MFC: Usar fuentes

Si el control ActiveX muestra texto, puede permitir que el usuario del control cambie la apariencia del texto cambiando una propiedad de fuente. Las propiedades de fuente se implementan como objetos de fuente y pueden ser de uno de estos dos tipos: estándar o personalizado. Las propiedades de fuente estándar son propiedades de fuente preimplementadas que se pueden agregar mediante el Asistente para agregar propiedades. Las propiedades de fuente personalizadas no están preimplementadas y el desarrollador del control determina el comportamiento y el uso de la propiedad.

En este artículo se tratan los temas siguientes:

- [Usar la propiedad Font estándar](#_core_using_the_stock_font_property)

- [Usar propiedades de fuente personalizadas en el control](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Usar la propiedad Font estándar

Las propiedades de fuente estándar están preimplementadas por la clase [COleControl](reference/colecontrol-class.md). Además, también hay disponible una página de propiedades de fuente estándar, lo que permite al usuario cambiar varios atributos del objeto de fuente, como el nombre, el tamaño y el estilo.

Obtenga acceso al objeto de fuente a través de las funciones [getFont](reference/colecontrol-class.md#getfont), [SetFont](reference/colecontrol-class.md#setfont)y [InternalGetFont](reference/colecontrol-class.md#internalgetfont) de `COleControl` . El usuario del control tendrá acceso al objeto de fuente a través de las `GetFont` `SetFont` funciones y de la misma manera que cualquier otra propiedad Get/Set. Cuando se requiere acceso al objeto de fuente desde dentro de un control, utilice la `InternalGetFont` función.

Como se describe en [controles ActiveX de MFC: propiedades](mfc-activex-controls-properties.md), la adición de propiedades estándar es fácil con el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md). Elija la propiedad Font y el Asistente para agregar propiedades insertará automáticamente la entrada de fuente stock en el mapa de envío del control.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Para agregar la propiedad Font estándar mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

   Se abrirá el Asistente para agregar propiedades.

1. En el cuadro **nombre de propiedad** , haga clic en **fuente**.

1. Haga clic en **Finalizar**

El Asistente para agregar propiedades agrega la línea siguiente al mapa de envío del control, ubicado en el archivo de implementación de clase de control:

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Además, el Asistente para agregar propiedades agrega la siguiente línea al control. Archivo IDL:

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

La propiedad Caption estándar es un ejemplo de una propiedad de texto que se puede dibujar con la información de la propiedad Font estándar. Al agregar la propiedad Caption estándar al control, se usan pasos similares a los que se usan para la propiedad Font estándar.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Para agregar la propiedad Caption estándar mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

   Se abrirá el Asistente para agregar propiedades.

1. En el cuadro **nombre de propiedad** , haga clic en **título**.

1. Haga clic en **Finalizar**

El Asistente para agregar propiedades agrega la línea siguiente al mapa de envío del control, ubicado en el archivo de implementación de clase de control:

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Modificar la función OnDraw

La implementación predeterminada de `OnDraw` utiliza la fuente del sistema de Windows para todo el texto que se muestra en el control. Esto significa que debe modificar el `OnDraw` código seleccionando el objeto de fuente en el contexto del dispositivo. Para ello, llame a [COleControl:: SelectStockFont](reference/colecontrol-class.md#selectstockfont) y pase el contexto de dispositivo del control, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Una vez que la función se ha `OnDraw` modificado para usar el objeto Font, cualquier texto del control se muestra con características de la propiedad Font estándar del control.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Usar propiedades de fuente personalizadas en el control

Además de la propiedad Font estándar, el control ActiveX puede tener propiedades de fuente personalizadas. Para agregar una propiedad de fuente personalizada, debe:

- Use el Asistente para agregar propiedades para implementar la propiedad de fuente personalizada.

- [Procesando notificaciones de fuentes](#_core_processing_font_notifications).

- [Implementar una nueva interfaz de notificación de fuentes](#_core_implementing_a_new_font_notification_interface).

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Implementar una propiedad de fuente personalizada

Para implementar una propiedad de fuente personalizada, use el Asistente para agregar propiedades con el fin de agregar la propiedad y realizar algunas modificaciones en el código. En las secciones siguientes se describe cómo agregar la `HeadingFont` propiedad personalizada al control de ejemplo.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Para agregar la propiedad de fuente personalizada mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

   Se abrirá el Asistente para agregar propiedades.

1. En el cuadro **nombre de propiedad** , escriba un nombre para la propiedad. En este ejemplo, use **HeadingFont**.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. En el cuadro **tipo de propiedad** , seleccione **IDispatch** <strong>\*</strong> en el tipo de la propiedad.

1. Haga clic en **Finalizar**

El Asistente para agregar propiedades crea el código para agregar la `HeadingFont` propiedad personalizada a la `CSampleCtrl` clase y el ejemplo. Archivo IDL. Dado `HeadingFont` que es un tipo de propiedad Get/Set, el Asistente para agregar propiedades modifica el `CSampleCtrl` mapa de envío de la clase para incluir un DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex) entrada de macro:

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

La macro DISP_PROPERTY_EX asocia el `HeadingFont` nombre de la propiedad a sus `CSampleCtrl` métodos GET y set de clase correspondientes, `GetHeadingFont` y `SetHeadingFont` . También se especifica el tipo del valor de la propiedad; en este caso, VT_FONT.

El Asistente para agregar propiedades también agrega una declaración en el archivo de encabezado del control (. H) para las `GetHeadingFont` `SetHeadingFont` funciones y y agrega sus plantillas de función en el archivo de implementación del control (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Por último, el Asistente para agregar propiedades modifica el control. Archivo IDL agregando una entrada para la `HeadingFont` propiedad:

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Modificaciones en el código de control

Ahora que ha agregado la `HeadingFont` propiedad al control, debe realizar algunos cambios en los archivos de encabezado y de implementación del control para admitir totalmente la nueva propiedad.

En el archivo de encabezado del control (. H), agregue la siguiente declaración de una variable miembro protegida:

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

En el archivo de implementación del control (. CPP), haga lo siguiente:

- Inicialice *m_fontHeading* en el constructor del control.

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Declare una estructura FONTDESC estática que contenga los atributos predeterminados de la fuente.

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- En la `DoPropExchange` función miembro del control, agregue una llamada a la `PX_Font` función. Esto proporciona la inicialización y persistencia de la propiedad de fuente personalizada.

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Finalice la implementación de la `GetHeadingFont` función miembro del control.

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Finalice la implementación de la `SetHeadingFont` función miembro del control.

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Modifique la `OnDraw` función miembro del control para definir una variable que contenga la fuente seleccionada anteriormente.

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Modifique la `OnDraw` función miembro del control para seleccionar la fuente personalizada en el contexto del dispositivo agregando la siguiente línea siempre que se use la fuente.

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Modifique la `OnDraw` función miembro del control para volver a seleccionar la fuente anterior en el contexto del dispositivo agregando la línea siguiente después de que se haya utilizado la fuente.

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Una vez implementada la propiedad de fuente personalizada, debe implementarse la página de propiedades de fuente estándar, lo que permite a los usuarios del control cambiar la fuente actual del control. Para agregar el identificador de página de propiedades de la página de propiedades de fuente estándar, inserte la siguiente línea después de la macro BEGIN_PROPPAGEIDS:

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

También debe incrementar el parámetro Count de la macro BEGIN_PROPPAGEIDS en uno. Esto se ilustra en la línea siguiente:

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Una vez realizados estos cambios, recompile todo el proyecto para incorporar la funcionalidad adicional.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Procesamiento de notificaciones de fuentes

En la mayoría de los casos, el control debe saber cuándo se han modificado las características del objeto de fuente. Cada objeto Font es capaz de proporcionar notificaciones cuando cambia llamando a una función miembro de la `IFontNotification` interfaz, implementada por `COleControl` .

Si el control usa la propiedad Font estándar, las notificaciones se administran mediante la `OnFontChanged` función miembro de `COleControl` . Al agregar propiedades de fuente personalizadas, puede hacer que utilicen la misma implementación. En el ejemplo de la sección anterior, esto se logra pasando &*m_xFontNotification* al inicializar la variable miembro de *m_fontHeading* .

![Implementar varias interfaces de objetos de fuente](../mfc/media/vc373q1.gif "Implementar varias interfaces de objetos de fuente") <br/>
Implementar varias interfaces de objetos de fuente

Las líneas sólidas de la ilustración anterior muestran que ambos objetos de fuente usan la misma implementación de `IFontNotification` . Esto podría causar problemas si desea distinguir qué fuente ha cambiado.

Una manera de distinguir entre las notificaciones del objeto Font del control es crear una implementación independiente de la `IFontNotification` interfaz para cada objeto Font del control. Esta técnica permite optimizar el código de dibujo actualizando solo la cadena, o cadenas, que usan la fuente modificada recientemente. En las secciones siguientes se muestran los pasos necesarios para implementar interfaces de notificación independientes para una segunda propiedad de fuente. Se supone que la segunda propiedad de fuente es la `HeadingFont` propiedad que se agregó en la sección anterior.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Implementar una nueva interfaz de notificación de fuentes

Para distinguir entre las notificaciones de dos o más fuentes, se debe implementar una nueva interfaz de notificación para cada fuente utilizada en el control. En las secciones siguientes se describe cómo implementar una nueva interfaz de notificación de fuente modificando los archivos de encabezado y de implementación del control.

### <a name="additions-to-the-header-file"></a>Adiciones al archivo de encabezado

En el archivo de encabezado del control (. H), agregue las líneas siguientes a la declaración de clase:

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Esto crea una implementación de la `IPropertyNotifySink` interfaz denominada `HeadingFontNotify` . Esta nueva interfaz contiene un método denominado `OnChanged` .

### <a name="additions-to-the-implementation-file"></a>Adiciones al archivo de implementación

En el código que inicializa la fuente del encabezado (en el constructor del control), cambie &*m_xFontNotification* a &*m_xHeadingFontNotify*. Después agregue el siguiente código:

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

Los `AddRef` `Release` métodos y de la `IPropertyNotifySink` interfaz realizan un seguimiento del recuento de referencias del objeto de control ActiveX. Cuando el control obtiene acceso al puntero de interfaz, el control llama `AddRef` a para incrementar el recuento de referencias. Cuando el control finaliza con el puntero, llama `Release` a, de forma muy similar `GlobalFree` a como se podría llamar para liberar un bloque de memoria global. Cuando el recuento de referencias de esta interfaz llega a cero, se puede liberar la implementación de la interfaz. En este ejemplo, la `QueryInterface` función devuelve un puntero a una `IPropertyNotifySink` interfaz en un objeto determinado. Esta función permite a un control ActiveX consultar un objeto para determinar qué interfaces admite.

Una vez realizados estos cambios en el proyecto, recompile el proyecto y use el contenedor de prueba para probar la interfaz. Consulte [Probar propiedades y eventos con un contenedor de prueba](testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Usar imágenes en un control ActiveX](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[Controles ActiveX MFC: Usar páginas de propiedades estándar](mfc-activex-controls-using-stock-property-pages.md)
