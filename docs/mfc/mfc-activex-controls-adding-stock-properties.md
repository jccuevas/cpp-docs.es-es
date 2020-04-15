---
title: 'Controles ActiveX MFC: Agregar propiedades estándar'
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 16bdfddf0c028bc6a312767844b38c58c942d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364659"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Controles ActiveX MFC: Agregar propiedades estándar

Las propiedades de stock difieren de las propiedades `COleControl`personalizadas en que ya están implementadas por la clase. `COleControl`contiene funciones miembro predefinidas que admiten propiedades comunes para el control. Algunas propiedades comunes incluyen el título del control y los colores de primer plano y fondo. Para obtener información sobre otras propiedades de stock, consulte Propiedades de [stock admitidas por el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard) más adelante en este artículo. Las entradas del mapa de distribución para las propiedades de stock siempre están precedidas por DISP_STOCKPROP.

En este artículo se describe cómo agregar una propiedad stock (en este caso, Caption) a un control ActiveX mediante el Asistente para agregar propiedades y se explican las modificaciones de código resultantes. Contenido de los temas:

- [Uso del Asistente para agregar propiedades para agregar una propiedad de stock](#_core_using_classwizard_to_add_a_stock_property)

- [Agregar cambios en el Asistente para propiedades de propiedades de stock](#_core_classwizard_changes_for_stock_properties)

- [Propiedades de stock admitidas por el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard)

- [Propiedades de stock y notificación](#_core_stock_properties_and_notification)

- [Propiedades de color](#_core_color_properties)

    > [!NOTE]
    >  Los controles personalizados de Visual Basic suelen tener propiedades como Superior, Izquierda, Ancho, Alto, Alinear, Etiquetar, Nombre, TabIndex, TabStop y Padre. Los contenedores de controles ActiveX, sin embargo, son responsables de implementar estas propiedades de control y, por lo tanto, los controles ActiveX no deben admitir estas propiedades.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>Uso del Asistente para agregar propiedades para agregar una propiedad de stock

Agregar propiedades de stock requiere menos código que agregar propiedades personalizadas porque la compatibilidad con la propiedad se controla automáticamente mediante `COleControl`. En el siguiente procedimiento se muestra cómo agregar la propiedad stock Caption a un marco de control ActiveX y también se puede usar para agregar otras propiedades de stock. Sustituya el nombre de propiedad de stock seleccionado por Subtítulo.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Para agregar la propiedad stock Caption mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el cuadro **Nombre** de propiedad , haga clic en **Título**.

1. Haga clic en **Finalizar**

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>Agregar cambios en el Asistente para propiedades de propiedades de stock

Dado `COleControl` que admite propiedades de stock, el Asistente para agregar propiedades no cambia la declaración de clase de ninguna manera; agrega la propiedad al mapa de distribución. El Asistente para agregar propiedades agrega la línea siguiente al mapa de distribución del control, que se encuentra en la implementación (. CPP) archivo:

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

La siguiente línea se agrega a la descripción de la interfaz del control (. IDL) archivo:

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Esta línea asigna a la propiedad Caption un identificador específico. Observe que la propiedad es enlazable y solicitará permiso a la base de datos antes de modificar el valor.

Esto hace que la propiedad Caption esté disponible para los usuarios del control. Para utilizar el valor de una propiedad stock, acceda `COleControl` a una variable miembro o función miembro de la clase base. Para obtener más información sobre estas variables miembro y funciones miembro, vea la sección siguiente, Propiedades de stock admitidas por el Asistente para agregar propiedades.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>Propiedades de stock admitidas por el Asistente para agregar propiedades

La `COleControl` clase proporciona nueve propiedades de stock. Puede agregar las propiedades que desee mediante el Asistente para agregar propiedades.

|Propiedad|Entrada de mapa de despacho|Cómo acceder al valor|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|Valor accesible `m_sAppearance`como .|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|Valor accesible `GetBackColor`llamando a .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|Valor accesible `m_sBorderStyle`como .|
|`Caption`|DISP_STOCKPROP_CAPTION( )|Valor accesible `InternalGetText`llamando a .|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|Valor accesible `m_bEnabled`como .|
|`Font`|DISP_STOCKPROP_FONT( )|Consulte el artículo Controles ActiveX de [MFC: Uso](../mfc/mfc-activex-controls-using-fonts.md) de fuentes para su uso.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|Valor accesible `GetForeColor`llamando a .|
|`hWnd`|DISP_STOCKPROP_HWND( )|Valor accesible `m_hWnd`como .|
|`Text`|DISP_STOCKPROP_TEXT( )|Valor accesible `InternalGetText`llamando a . Esta propiedad es `Caption`la misma que , excepto por el nombre de la propiedad.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Valor accesible `m_lReadyState` como o`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>Propiedades y notificación de stock

La mayoría de las propiedades de stock tienen funciones de notificación que se pueden invalidar. Por ejemplo, `BackColor` cada vez que `OnBackColorChanged` se cambia la propiedad, se llama a la función (una función miembro de la clase de control). La implementación `COleControl`predeterminada `InvalidateControl`(en ) llama . Invalide esta función si desea realizar acciones adicionales en respuesta a esta situación.

## <a name="color-properties"></a><a name="_core_color_properties"></a>Propiedades de color

Puede utilizar el `ForeColor` `BackColor` stock y las propiedades, o sus propias propiedades de color personalizadas, al pintar el control. Para usar una propiedad de color, llame a la [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) función miembro. Los parámetros de esta función son el valor de la propiedad color y un identificador de paleta opcional. El valor devuelto es un valor **COLORREF** que se `SetTextColor` puede `CreateSolidBrush`pasar a funciones GDI, como y .

Se tiene acceso `ForeColor` a `BackColor` los valores de `GetForeColor` color `GetBackColor` para el stock y las propiedades llamando a la función o a la función, respectivamente.

En el ejemplo siguiente se muestra el uso de estas dos propiedades de color al pintar un control. Inicializa una variable **COLORREF** temporal `CBrush` y un `TranslateColor`objeto con `ForeColor` llamadas a `BackColor` : uno mediante la propiedad y el otro mediante la propiedad. A `CBrush` continuación, se usa un objeto temporal para pintar el rectángulo `ForeColor` del control y el color del texto se establece mediante la propiedad.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
