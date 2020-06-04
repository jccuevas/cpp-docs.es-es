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
ms.openlocfilehash: c336ec6c29b5478655ca8f19f71378a2b446ac64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358268"
---
# <a name="mfc-activex-controls-using-fonts"></a>Controles ActiveX MFC: Usar fuentes

Si el control ActiveX muestra texto, puede permitir que el usuario del control cambie la apariencia del texto cambiando una propiedad de fuente. Las propiedades de fuente se implementan como objetos de fuente y pueden ser uno de dos tipos: stock o custom. Las propiedades de fuente de stock son propiedades de fuente preimplementadas que puede agregar mediante el Asistente para agregar propiedades. Las propiedades de fuente personalizadas no se implementan previamente y el desarrollador del control determina el comportamiento y el uso de la propiedad.

En este artículo se tratan los temas siguientes:

- [Uso de la propiedad Stock Font](#_core_using_the_stock_font_property)

- [Uso de propiedades de fuente personalizadas en el control](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>Uso de la propiedad de fuente de stock

Las propiedades de fuente de stock se implementan previamente mediante la clase [COleControl](../mfc/reference/colecontrol-class.md). Además, también está disponible una página de propiedades Font estándar, lo que permite al usuario cambiar varios atributos del objeto de fuente, como su nombre, tamaño y estilo.

Acceda al objeto font a través de las funciones [GetFont](../mfc/reference/colecontrol-class.md#getfont), [SetFont](../mfc/reference/colecontrol-class.md#setfont)e [InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont) de `COleControl`. El usuario de control tendrá `GetFont` acceso `SetFont` al objeto de fuente a través de las funciones y de la misma manera que cualquier otra propiedad Get/Set. Cuando se requiere acceso al objeto de fuente `InternalGetFont` desde un control, utilice la función.

Como se describe en [Controles ActiveX de MFC: Propiedades](../mfc/mfc-activex-controls-properties.md), agregar propiedades de stock es fácil con el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md). Elija la propiedad Fuente y el Asistente para agregar propiedades inserta automáticamente la entrada de fuente de stock en el mapa de distribución del control.

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>Para agregar la propiedad Font de stock mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el Asistente para agregar propiedades.

1. En el cuadro Nombre de **propiedad** , haga clic en **Fuente**.

1. Haga clic en **Finalizar**

El Asistente para agregar propiedades agrega la línea siguiente al mapa de distribución del control, ubicado en el archivo de implementación de la clase de control:

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

Además, el Asistente para agregar propiedades agrega la siguiente línea al control . Archivo IDL:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

La propiedad stock Caption es un ejemplo de una propiedad text que se puede dibujar utilizando la información de propiedad Font de stock. Agregar el stock Caption propiedad al control utiliza pasos similares a los utilizados para el stock Font propiedad.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Para agregar la propiedad stock Caption mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el Asistente para agregar propiedades.

1. En el cuadro **Nombre** de propiedad , haga clic en **Título**.

1. Haga clic en **Finalizar**

El Asistente para agregar propiedades agrega la línea siguiente al mapa de distribución del control, ubicado en el archivo de implementación de la clase de control:

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>Modificación de la función OnDraw

La implementación `OnDraw` predeterminada de utiliza la fuente del sistema de Windows para todo el texto que se muestra en el control. Esto significa que debe `OnDraw` modificar el código seleccionando el objeto de fuente en el contexto del dispositivo. Para ello, llame a [COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont) y pase el contexto del dispositivo del control, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

Después `OnDraw` de modificar la función para utilizar el objeto de fuente, cualquier texto dentro del control se muestra con características de la propiedad Font de stock del control.

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>Uso de propiedades de fuente personalizadas en el control

Además de la propiedad Font de stock, el control ActiveX puede tener propiedades Font personalizadas. Para agregar una propiedad de fuente personalizada, debe:

- Use el Asistente para agregar propiedades para implementar la propiedad Font personalizada.

- [Procesamiento de notificaciones](#_core_processing_font_notifications)de fuente .

- [Implementación de una nueva interfaz](#_core_implementing_a_new_font_notification_interface)de notificación de fuentes .

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>Implementación de una propiedad de fuente personalizada

Para implementar una propiedad Font personalizada, use el Asistente para agregar propiedades para agregar la propiedad y, a continuación, realice algunas modificaciones en el código. En las secciones siguientes `HeadingFont` se describe cómo agregar la propiedad personalizada a la Sample control.

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>Para agregar la propiedad Font personalizada mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el Asistente para agregar propiedades.

1. En el cuadro Nombre de **propiedad,** escriba un nombre para la propiedad. Para este ejemplo, utilice **HeadingFont**.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. En el cuadro Tipo de **propiedad,** seleccione **IDispatch** <strong>\*</strong> para el tipo de propiedad.

1. Haga clic en **Finalizar**

El Asistente para agregar propiedades `HeadingFont` crea el `CSampleCtrl` código para agregar la propiedad personalizada a la clase y sample. IDL. Dado `HeadingFont` que es un tipo de propiedad Get/Set, el Asistente para agregar propiedades modifica el mapa de distribución de la `CSampleCtrl` clase para incluir una entrada de macro[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex) DISP_PROPERTY_EX_ID:

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

La macro DISP_PROPERTY_EX `HeadingFont` asocia el `CSampleCtrl` nombre de propiedad `GetHeadingFont` con `SetHeadingFont`su clase correspondiente Get y Set métodos y . También se especifica el tipo del valor de propiedad; en este caso, VT_FONT.

El Asistente para agregar propiedades también agrega una declaración en el archivo de encabezado de control (. H) para `GetHeadingFont` `SetHeadingFont` y funciones y agrega sus plantillas de función en el archivo de implementación del control (. CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

Por último, el Asistente para agregar propiedades modifica el control . IDL agregando una entrada `HeadingFont` para la propiedad:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>Modificaciones del Código de Control

Ahora que ha `HeadingFont` agregado la propiedad al control, debe realizar algunos cambios en el encabezado del control y los archivos de implementación para admitir completamente la nueva propiedad.

En el archivo de encabezado de control (. H), agregue la siguiente declaración de una variable miembro protegida:

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

En el archivo de implementación del control (. CPP), haga lo siguiente:

- Inicializar *m_fontHeading* en el constructor de control.

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- Declare una estructura FONTDESC estática que contenga los atributos predeterminados de la fuente.

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- En la `DoPropExchange` función miembro del `PX_Font` control, agregue una llamada a la función. Esto proporciona inicialización y persistencia para la propiedad Font personalizada.

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- Finalice la `GetHeadingFont` implementación de la función miembro de control.

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- Finalice la `SetHeadingFont` implementación de la función miembro de control.

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- Modifique la `OnDraw` función miembro del control para definir una variable que contendrá la fuente seleccionada anteriormente.

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- Modifique la `OnDraw` función miembro del control para seleccionar la fuente personalizada en el contexto del dispositivo agregando la siguiente línea dondequiera que se use la fuente.

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- Modifique la `OnDraw` función miembro del control para volver a seleccionar la fuente anterior en el contexto del dispositivo agregando la siguiente línea después de que se haya utilizado la fuente.

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

Una vez implementada la propiedad Font personalizada, se debe implementar la página de propiedades Font estándar, lo que permite a los usuarios del control cambiar la fuente actual del control. Para agregar el identificador de página de propiedades para la página de propiedades Fuente estándar, inserte la siguiente línea después de la macro BEGIN_PROPPAGEIDS:

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

También debe incrementar el parámetro count de la macro de BEGIN_PROPPAGEIDS en uno. Esto se ilustra en la línea siguiente:

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

Una vez realizados estos cambios, vuelva a generar todo el proyecto para incorporar la funcionalidad adicional.

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>Procesamiento de notificaciones de fuentes

En la mayoría de los casos, el control debe saber cuándo se han modificado las características del objeto de fuente. Cada objeto de fuente es capaz de proporcionar notificaciones `IFontNotification` cuando cambia llamando `COleControl`a una función miembro de la interfaz, implementada por .

Si el control utiliza la propiedad Font de stock, la función `OnFontChanged` miembro de `COleControl`. Al agregar propiedades de fuente personalizadas, puede hacer que usen la misma implementación. En el ejemplo de la sección anterior, esto se logró pasando &*m_xFontNotification* al inicializar la variable miembro *m_fontHeading.*

![Implementación de varias interfaces de objetos de fuente](../mfc/media/vc373q1.gif "Implementar varias interfaces de objetos de fuente") <br/>
Implementar varias interfaces de objetos de fuente

Las líneas sólidas de la figura anterior muestran `IFontNotification`que ambos objetos de fuente utilizan la misma implementación de . Esto podría causar problemas si desea distinguir qué fuente ha cambiado.

Una forma de distinguir entre las notificaciones de objeto de `IFontNotification` fuente del control es crear una implementación independiente de la interfaz para cada objeto de fuente en el control. Esta técnica le permite optimizar el código de dibujo actualizando solo la cadena o cadenas que utilizan la fuente modificada recientemente. En las secciones siguientes se muestran los pasos necesarios para implementar interfaces de notificación independientes para una segunda propiedad Font. Se supone que la segunda `HeadingFont` propiedad de fuente es la propiedad que se agregó en la sección anterior.

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>Implementación de una nueva interfaz de notificación de fuentes

Para distinguir entre las notificaciones de dos o más fuentes, se debe implementar una nueva interfaz de notificación para cada fuente utilizada en el control. En las secciones siguientes se describe cómo implementar una nueva interfaz de notificación de fuentes modificando el encabezado del control y los archivos de implementación.

### <a name="additions-to-the-header-file"></a>Adiciones al archivo de encabezado

En el archivo de encabezado de control (. H), agregue las siguientes líneas a la declaración de clase:

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

Esto crea una `IPropertyNotifySink` implementación `HeadingFontNotify`de la interfaz denominada . Esta nueva interfaz `OnChanged`contiene un método llamado .

### <a name="additions-to-the-implementation-file"></a>Adiciones al archivo de implementación

En el código que inicializa la fuente de encabezado (en el constructor del control), cambie &*m_xFontNotification* a &*m_xHeadingFontNotify*. Después agregue el siguiente código:

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

Los `AddRef` `Release` métodos `IPropertyNotifySink` y de la interfaz realizan un seguimiento del recuento de referencias para el objeto de control ActiveX. Cuando el control obtiene acceso al puntero `AddRef` de interfaz, el control llama para incrementar el recuento de referencias. Cuando el control finaliza con el `Release`puntero, llama a `GlobalFree` , de la misma manera que se puede llamar para liberar un bloque de memoria global. Cuando el recuento de referencias para esta interfaz va a cero, la implementación de la interfaz se puede liberar. En este ejemplo, la `QueryInterface` función `IPropertyNotifySink` devuelve un puntero a una interfaz en un objeto determinado. Esta función permite que un control ActiveX consulte un objeto para determinar qué interfaces admite.

Una vez realizados estos cambios en el proyecto, vuelva a generar el proyecto y use el contenedor de pruebas para probar la interfaz. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Usar imágenes en un control ActiveX](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)
