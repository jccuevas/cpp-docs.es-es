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
ms.openlocfilehash: 940f61c9ce6ccb57843333582455e61c1f7ac73b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289694"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Controles ActiveX MFC: Agregar propiedades estándar

Propiedades estándar se diferencian de las propiedades personalizadas en que ya se implementan mediante la clase `COleControl`. `COleControl` contiene funciones miembro predefinidas que admiten propiedades comunes para el control. Algunas propiedades comunes incluyen el título del control y los colores de primer y segundo plano. Para obtener información sobre otras propiedades estándar, vea [propiedades estándar admitidas por el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard) más adelante en este artículo. Las entradas de asignación de envío para propiedades siempre tienen el prefijo DISP_STOCKPROP de existencias.

En este artículo se describe cómo agregar una propiedad estándar (en este caso, Caption) a un control ActiveX mediante el Asistente para agregar propiedades y explica las modificaciones de código resultante. Entre los temas se incluyen los siguientes:

- [Usar al Asistente para agregar propiedades para agregar una propiedad estándar](#_core_using_classwizard_to_add_a_stock_property)

- [Agregue los cambios del Asistente para la propiedad para propiedades estándar](#_core_classwizard_changes_for_stock_properties)

- [Propiedades estándar compatibles con el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard)

- [Notificación y propiedades estándar](#_core_stock_properties_and_notification)

- [Propiedades de color](#_core_color_properties)

    > [!NOTE]
    >  Controles personalizados de Visual Basic suelen tener propiedades como Top, Left, Width, Height, alinear, etiqueta, nombre, TabIndex, TabStop y primario. Contenedores de controles ActiveX, sin embargo, son responsables de implementar estas propiedades de control y, por tanto, los controles de ActiveX no deben admitir estas propiedades.

##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> Mediante el Asistente para agregar propiedades para agregar una propiedad estándar

Agregar propiedades estándar requiere menos código que agregar propiedades personalizadas, porque la compatibilidad con la propiedad controla automáticamente la `COleControl`. El siguiente procedimiento muestra cómo agregar la propiedad Caption estándar a un control ActiveX y también se puede usar para agregar otras propiedades estándar. Sustituya el nombre de propiedad estándar para el título.

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Para agregar la propiedad de título estándar mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el **nombre de la propiedad** cuadro, haga clic en **título**.

1. Haga clic en **Finalizar**.

##  <a name="_core_classwizard_changes_for_stock_properties"></a> Agregar propiedad cambios del Asistente para propiedades estándar

Dado que `COleControl` admite las propiedades estándar, el Asistente para agregar propiedades no cambia la declaración de clase de cualquier manera, agrega la propiedad al mapa de envíos. El Asistente para agregar propiedades agrega la siguiente línea al mapa de envíos del control, que se encuentra en la implementación (. Archivo CPP):

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

La siguiente línea se agrega a la descripción de la interfaz del control (. Archivo IDL):

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

Esta línea asigna la propiedad Caption un identificador específico. Tenga en cuenta que la propiedad es enlazable y solicitará permiso de la base de datos antes de modificar el valor.

Esto hace que la propiedad Caption disponibles para los usuarios de su control. Para usar el valor de una propiedad estándar, tener acceso a una variable de miembro o una función miembro de la `COleControl` clase base. Para obtener más información sobre estas variables de miembro y funciones miembro, vea la sección siguiente, propiedades estándar admitidas por el Asistente para agregar propiedades.

##  <a name="_core_stock_properties_supported_by_classwizard"></a> Propiedades estándar admitidas por el Asistente para agregar propiedades

La `COleControl` clase proporciona nueve propiedades estándar. Puede agregar las propiedades que desee mediante el Asistente para agregar propiedades.

|Property|Entrada del mapa de envíos|Cómo obtener acceso a valor|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|Valor accesible como `m_sAppearance`.|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|Valor accesible mediante una llamada a `GetBackColor`.|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|Valor accesible como `m_sBorderStyle`.|
|`Caption`|DISP_STOCKPROP_CAPTION( )|Valor accesible mediante una llamada a `InternalGetText`.|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|Valor accesible como `m_bEnabled`.|
|`Font`|DISP_STOCKPROP_FONT( )|Consulte el artículo [controles ActiveX MFC: Usar fuentes](../mfc/mfc-activex-controls-using-fonts.md) para su uso.|
|`ForeColor`|(DE DISP_STOCKPROP_FORECOLOR)|Valor accesible mediante una llamada a `GetForeColor`.|
|`hWnd`|DISP_STOCKPROP_HWND( )|Valor accesible como `m_hWnd`.|
|`Text`|DISP_STOCKPROP_TEXT( )|Valor accesible mediante una llamada a `InternalGetText`. Esta propiedad es igual a `Caption`, excepto el nombre de propiedad.|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Valor accesible como `m_lReadyState` o `GetReadyState`|

##  <a name="_core_stock_properties_and_notification"></a> Notificación y propiedades estándar

La mayoría de propiedades estándar tienen funciones de notificación que se pueden invalidar. Por ejemplo, siempre que el `BackColor` se cambia la propiedad, el `OnBackColorChanged` se llama a la función (una función miembro de la clase de control). La implementación predeterminada (en `COleControl`) llamadas `InvalidateControl`. Si desea realizar acciones adicionales en respuesta a esta situación, reemplace esta función.

##  <a name="_core_color_properties"></a> Propiedades de color

Puede usar las existencias `ForeColor` y `BackColor` propiedades o sus propias propiedades de color personalizado, cuando el dibujo del control. Para utilizar una propiedad de color, llame a la [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) función miembro. Los parámetros de esta función son el valor de la propiedad de color y un identificador de la paleta opcional. El valor devuelto es un **COLORREF** funciones de valor que se puede pasar a GDI, como `SetTextColor` y `CreateSolidBrush`.

Los valores de color para las acciones `ForeColor` y `BackColor` propiedades son accesibles desde llamando el `GetForeColor` o `GetBackColor` funcione, respectivamente.

El ejemplo siguiente se muestra cómo utilizar estas dos propiedades de color al pintar un control. Inicializa un archivo temporal **COLORREF** variable y un `CBrush` objeto con las llamadas a `TranslateColor`: uno con el `ForeColor` propiedad y otra usando la `BackColor` propiedad. Un archivo temporal `CBrush` objeto, a continuación, se usa para pintar el rectángulo del control y el color del texto se establece mediante la `ForeColor` propiedad.

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
