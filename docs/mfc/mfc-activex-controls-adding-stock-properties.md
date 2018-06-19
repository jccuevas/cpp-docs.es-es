---
title: 'Controles ActiveX MFC: Agregar propiedades estándar | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c51a2efba3c89b4e216fec96459b14c3d0c637d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357564"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Controles ActiveX MFC: Agregar propiedades estándar
Propiedades estándar se diferencian de las propiedades personalizadas en que ya se implementan mediante la clase `COleControl`. `COleControl` contiene funciones miembro predefinidas que admiten propiedades comunes para el control. Algunas propiedades comunes incluyen el título del control y los colores de primer plano y fondo. Para obtener información sobre otras propiedades estándar, vea [propiedades estándar admitidas por el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard) más adelante en este artículo. Las entradas del mapa de envíos para propiedades estándar siempre van precedidas por **DISP_STOCKPROP**.  
  
 En este artículo se describe cómo agregar una propiedad estándar (en este caso, Caption) a un control ActiveX mediante el Asistente para agregar propiedades y explica las modificaciones de código resultante. Entre los temas se incluyen los siguientes:  
  
-   [Usar al Asistente para agregar propiedades para agregar una propiedad estándar](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [Agregue los cambios de propiedad Asistente para propiedades estándar](#_core_classwizard_changes_for_stock_properties)  
  
-   [Propiedades estándar admitidas por el Asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard)  
  
-   [Propiedades estándar y notificación](#_core_stock_properties_and_notification)  
  
-   [Propiedades de color](#_core_color_properties)  
  
    > [!NOTE]
    >  Controles personalizados de Visual Basic suelen tengan propiedades como Top, Left, ancho, alto, alinear, etiqueta, nombre, TabIndex, TabStop y primario. Contenedores de controles ActiveX, sin embargo, son responsables de implementar estas propiedades de control y, por tanto, los controles ActiveX no deben admitir estas propiedades.  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> Mediante el Asistente para agregar propiedades para agregar una propiedad estándar  
 Agregar propiedades estándar requiere menos código que agregar propiedades personalizadas, ya que la compatibilidad con la propiedad controla automáticamente la `COleControl`. El siguiente procedimiento muestra cómo agregar la propiedad Caption estándar a un marco de trabajo de control ActiveX y también puede utilizarse para agregar otras propiedades estándar. Sustituya el nombre de propiedad estándar seleccionado por título.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Para agregar la propiedad de título estándar mediante el Asistente para agregar propiedades  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca del control.  
  
3.  Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.  
  
     Se abrirá la [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).  
  
5.  En el **nombre de la propiedad** cuadro, haga clic en **título**.  
  
6.  Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> Agregar propiedad cambios del Asistente para propiedades estándar  
 Dado que `COleControl` admite propiedades estándar, el Asistente para agregar propiedades no cambia la declaración de clase de ninguna forma, la propiedad agrega al mapa de envíos. El Asistente para agregar propiedades agrega la siguiente línea al mapa de envíos del control, que se encuentra en la implementación (. Archivo CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 La siguiente línea se agrega a la descripción de la interfaz del control (. Este archivo IDL):  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 Esta línea asigna a la propiedad Caption un identificador concreto. Observe que la propiedad es enlazable y solicitará permiso de la base de datos antes de modificar el valor.  
  
 Esto hace que la propiedad Caption estén disponibles para los usuarios del control. Para usar el valor de una propiedad estándar, obtener acceso a una variable de miembro o una función miembro de la `COleControl` clase base. Para obtener más información sobre estas variables de miembro y funciones miembro, vea la siguiente sección, propiedades estándar admitidas por el Asistente para agregar propiedades.  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> Propiedades estándar admitidas por el Asistente para agregar propiedades  
 La `COleControl` clase proporciona nueve propiedades estándar. Puede agregar las propiedades que desee mediante el Asistente para agregar propiedades.  
  
|Property|Entrada del mapa de envíos|Cómo obtener acceso a valor|  
|--------------|------------------------|-------------------------|  
|**Apariencia**|**(DE DISP_STOCKPROP_APPEARANCE)**|Valor accesible como **m_sAppearance**.|  
|`BackColor`|**(DE DISP_STOCKPROP_BACKCOLOR)**|Valor accesible mediante una llamada a `GetBackColor`.|  
|`BorderStyle`|**(DE DISP_STOCKPROP_BORDERSTYLE)**|Valor accesible como **m_sBorderStyle**.|  
|**Título**|**(DE DISP_STOCKPROP_CAPTION)**|Valor accesible mediante una llamada a `InternalGetText`.|  
|**Habilitado**|**(DE DISP_STOCKPROP_ENABLED)**|Valor accesible como **m_bEnabled**.|  
|**Fuente**|**(DE DISP_STOCKPROP_FONT)**|Vea el artículo [controles ActiveX MFC: utilizar fuentes](../mfc/mfc-activex-controls-using-fonts.md) para su uso.|  
|`ForeColor`|**(DE DISP_STOCKPROP_FORECOLOR)**|Valor accesible mediante una llamada a `GetForeColor`.|  
|**hWnd**|**(DE DISP_STOCKPROP_HWND)**|Valor accesible como `m_hWnd`.|  
|**Texto**|**(DE DISP_STOCKPROP_TEXT)**|Valor accesible mediante una llamada a `InternalGetText`. Esta propiedad es igual a **título**, excepto el nombre de propiedad.|  
|**ReadyState**|**DISP_STOCKPROP_READYSTATE()**|Valor accesible como m_lReadyState o `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> Propiedades estándar y notificación  
 La mayoría de propiedades estándar tienen funciones de notificación que se pueden invalidar. Por ejemplo, siempre que el `BackColor` se cambia la propiedad, el `OnBackColorChanged` se llama a la función (una función miembro de la clase de control). La implementación predeterminada (en `COleControl`) llamadas `InvalidateControl`. Si desea realizar acciones adicionales en respuesta a esta situación, reemplace esta función.  
  
##  <a name="_core_color_properties"></a> Propiedades de color  
 Puede usar las existencias `ForeColor` y `BackColor` propiedades o sus propias propiedades de color personalizado, al dibujar el control. Para utilizar una propiedad de color, llame a la [COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) función miembro. Los parámetros de esta función son el valor de la propiedad de color y un identificador de paleta opcional. El valor devuelto es un **COLORREF** funciones de valor que puede pasarse a GDI, como `SetTextColor` y `CreateSolidBrush`.  
  
 Los valores de color para las acciones `ForeColor` y `BackColor` propiedades son accesibles mediante una llamada a la `GetForeColor` o `GetBackColor` funcione, respectivamente.  
  
 En el ejemplo siguiente se muestra cómo utilizar estas dos propiedades de color al dibujar un control. Inicializa un archivo temporal **COLORREF** variable y un `CBrush` objeto con llamadas a `TranslateColor`: uno que use la `ForeColor` de propiedad y el uso de otra el `BackColor` propiedad. Un archivo temporal `CBrush` objeto, a continuación, se usa para pintar el rectángulo del control y el color del texto se establece mediante el `ForeColor` propiedad.  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX de MFC: propiedades](../mfc/mfc-activex-controls-properties.md)   
 [Controles ActiveX de MFC: métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl (clase)](../mfc/reference/colecontrol-class.md)
