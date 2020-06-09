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
ms.openlocfilehash: 13e8af5ddb3dd5130c864e42383e3bb9ff23b87b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625423"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Controles ActiveX MFC: Agregar propiedades estándar

Las propiedades estándar se diferencian de las propiedades personalizadas en que ya están implementadas por la clase `COleControl` . `COleControl`contiene funciones miembro predefinidas que admiten las propiedades comunes del control. Algunas propiedades comunes incluyen el título del control y los colores de primer plano y de fondo. Para obtener información sobre otras propiedades estándar, consulte [las propiedades estándar que admite el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard) , más adelante en este artículo. Las entradas de mapa de envío para propiedades estándar siempre tienen el prefijo DISP_STOCKPROP.

En este artículo se describe cómo agregar una propiedad estándar (en este caso, Caption) a un control ActiveX mediante el Asistente para agregar propiedades y se explican las modificaciones de código resultantes. Contenido de los temas:

- [Usar el Asistente para agregar propiedades para agregar una propiedad estándar](#_core_using_classwizard_to_add_a_stock_property)

- [Cambios del Asistente para agregar propiedades para las propiedades estándar](#_core_classwizard_changes_for_stock_properties)

- [Propiedades estándar admitidas por el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard)

- [Propiedades estándar y notificación](#_core_stock_properties_and_notification)

- [Propiedades de color](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic controles personalizados suelen tener propiedades como Top, Left, width, height, align, Tag, Name, TabIndex, TabStop y Parent. Sin embargo, los contenedores de controles ActiveX son responsables de implementar estas propiedades de control y, por lo tanto, los controles ActiveX no deben admitir estas propiedades.

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>Usar el Asistente para agregar propiedades para agregar una propiedad estándar

Agregar propiedades estándar requiere menos código que agregar propiedades personalizadas, ya que la compatibilidad con la propiedad se administra automáticamente mediante `COleControl` . En el procedimiento siguiente se muestra cómo agregar la propiedad Caption estándar a un marco de control ActiveX y también se puede usar para agregar otras propiedades estándar. Sustituya el nombre de la propiedad estándar seleccionada por título.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Para agregar la propiedad Caption estándar mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el cuadro **nombre de propiedad** , haga clic en **título**.

1. Haga clic en **Finalizar**

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>Cambios del Asistente para agregar propiedades para las propiedades estándar

Dado que `COleControl` admite las propiedades estándar, el Asistente para agregar propiedades no cambia la declaración de clase de ningún modo; agrega la propiedad al mapa de envío. El Asistente para agregar propiedades agrega la línea siguiente al mapa de envío del control, que se encuentra en la implementación de (. CPP):

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

La línea siguiente se agrega a la descripción de la interfaz del control (. IDL):

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Esta línea asigna a la propiedad de título un identificador específico. Tenga en cuenta que la propiedad es enlazable y solicitará permiso de la base de datos antes de modificar el valor.

Esto hace que la propiedad Caption esté disponible para los usuarios del control. Para usar el valor de una propiedad estándar, obtenga acceso a una variable miembro o a una función miembro de la `COleControl` clase base. Para obtener más información sobre estas variables miembro y funciones miembro, vea la siguiente sección, propiedades estándar admitidas por el Asistente para agregar propiedades.

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>Propiedades estándar admitidas por el Asistente para agregar propiedades

La `COleControl` clase proporciona nueve propiedades estándar. Puede Agregar las propiedades que desee mediante el Asistente para agregar propiedades.

|Propiedad|Entrada de mapa de envío|Cómo obtener acceso al valor|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE ()|Valor accesible como `m_sAppearance` .|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR ()|Valor accesible mediante una llamada a `GetBackColor` .|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE ()|Valor accesible como `m_sBorderStyle` .|
|`Caption`|DISP_STOCKPROP_CAPTION ()|Valor accesible mediante una llamada a `InternalGetText` .|
|`Enabled`|DISP_STOCKPROP_ENABLED ()|Valor accesible como `m_bEnabled` .|
|`Font`|DISP_STOCKPROP_FONT ()|Vea el artículo [controles ActiveX de MFC: usar fuentes](mfc-activex-controls-using-fonts.md) para el uso.|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR ()|Valor accesible mediante una llamada a `GetForeColor` .|
|`hWnd`|DISP_STOCKPROP_HWND ()|Valor accesible como `m_hWnd` .|
|`Text`|DISP_STOCKPROP_TEXT ()|Valor accesible mediante una llamada a `InternalGetText` . Esta propiedad es igual que `Caption` , excepto el nombre de la propiedad.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE ()|Valor accesible como `m_lReadyState` o`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>Propiedades estándar y notificación

La mayoría de las propiedades estándar tienen funciones de notificación que se pueden invalidar. Por ejemplo, cada vez que `BackColor` se cambia la propiedad, `OnBackColorChanged` se llama a la función (una función miembro de la clase de control). La implementación predeterminada (en `COleControl` ) llama a `InvalidateControl` . Invalide esta función si desea realizar acciones adicionales en respuesta a esta situación.

## <a name="color-properties"></a><a name="_core_color_properties"></a>Propiedades de color

Puede usar las acciones `ForeColor` y las `BackColor` propiedades, o sus propias propiedades de color personalizadas, al pintar el control. Para usar una propiedad de color, llame a la función miembro [COleControl:: TranslateColor](reference/colecontrol-class.md#translatecolor) . Los parámetros de esta función son el valor de la propiedad color y un identificador de paleta opcional. El valor devuelto es un valor **COLORREF** que se puede pasar a las funciones GDI, como `SetTextColor` y `CreateSolidBrush` .

Se obtiene acceso a los valores de color para las acciones `ForeColor` y `BackColor` propiedades mediante una llamada a la `GetForeColor` `GetBackColor` función o, respectivamente.

En el ejemplo siguiente se muestra cómo utilizar estas dos propiedades de color al pintar un control. Inicializa una variable temporal **COLORREF** y un `CBrush` objeto con llamadas a `TranslateColor` : una mediante la `ForeColor` propiedad y la otra mediante la `BackColor` propiedad. A `CBrush` continuación, se utiliza un objeto temporal para pintar el rectángulo del control y el color del texto se establece mediante la `ForeColor` propiedad.

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](reference/colecontrol-class.md)
