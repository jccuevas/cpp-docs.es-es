---
title: "Controles ActiveX MFC: Agregar propiedades est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackColor (propiedad)"
  - "ForeColor (propiedad)"
  - "colores de primer plano"
  - "colores de primer plano, controles ActiveX"
  - "controles ActiveX en MFC, propiedades"
  - "propiedades [MFC], agregar estándar"
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controles ActiveX MFC: Agregar propiedades est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las propiedades comunes difieren de las propiedades personalizadas en que se implementan ya por la clase `COleControl`.  `COleControl` contiene el miembro predefinido funciona que las propiedades comunes de compatibilidad para el control.  Algunas propiedades comunes incluyen la leyenda del control y los colores de primer plano y de fondo.  Para obtener información sobre otras propiedades comunes, vea [Propiedades comunes admitidas por el asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard) más adelante en este artículo.  Las entradas del mapa de envío para las propiedades comunes son prefijadas siempre por **DISP\_STOCKPROP**.  
  
 En este artículo se describe cómo agregar una propiedad común \(en este caso, caption\) a un control ActiveX mediante el asistente para agregar propiedades y explica las modificaciones resultantes de código.  Entre los temas se incluyen los siguientes:  
  
-   [Mediante el asistente para agregar propiedades para agregar una propiedad común](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [Agregue los cambios del asistente de las propiedades comunes](#_core_classwizard_changes_for_stock_properties)  
  
-   [Propiedades comunes admitidas por el asistente para agregar propiedades](#_core_stock_properties_supported_by_classwizard)  
  
-   [Propiedades y notificación comunes](#_core_stock_properties_and_notification)  
  
-   [Propiedades de colores](#_core_color_properties)  
  
    > [!NOTE]
    >  Los controles personalizados de Visual Basic tienen normalmente propiedades como top, Left, el ancho, alto, clasificar, etiqueta, nombre, TabIndex, TabStop, y elemento primario.  Contenedores de controles ActiveX, sin embargo, son responsables de implementar estas propiedades de control y por consiguiente los controles ActiveX no deben admitir estas propiedades.  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> Mediante el asistente para agregar propiedades para agregar una propiedad común  
 Agregar propiedades comunes requiere menos código que propiedades personalizadas de suma porque la compatibilidad para la propiedad se encargan automáticamente `COleControl`.  El procedimiento siguiente muestra cómo agregar la propiedad caption común a un marco de control ActiveX y también se puede utilizar para agregar otras propiedades comunes.  Sustituya el nombre de propiedad común seleccionado para la leyenda.  
  
#### Para agregar la propiedad caption habituales mediante el asistente para agregar propiedades  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
     Esto abre [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).  
  
5.  En el cuadro de **Nombre de propiedad** , haga clic en **caption**.  
  
6.  Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> Agregue los cambios del asistente de las propiedades comunes  
 Dado que `COleControl` admite propiedades comunes, el asistente para agregar propiedades no cambia la declaración de clase de ninguna manera; agrega la propiedad a la asignación de envío.  El asistente para agregar agrega la línea siguiente al mapa de envío del control, que se encuentra en el archivo de implementación \(.CPP\):  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 La siguiente línea se agrega al archivo de descripción de la interfaz de control \(.IDL\):  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 Esta línea asigna a propiedad caption un identificador específica  Observe que la propiedad es enlazable y solicitará el permiso de base de datos antes de modificar el valor.  
  
 Esto hace que la propiedad caption a disposición de los usuarios del control.  Para utilizar el valor de una propiedad común, tenga acceso a una función de variable miembro o miembro de la clase base de `COleControl` .  Para obtener más información sobre estas variables miembro y funciones miembro, vea la siguiente sección, propiedades comunes admitidas por el asistente para agregar propiedades.  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> Propiedades comunes admitidas por el asistente para agregar propiedades  
 La clase de `COleControl` proporciona nueve propiedades comunes.  Puede agregar propiedades que desee mediante el asistente para agregar propiedades.  
  
|Propiedad|Entrada de asignación de envío|Cómo tener acceso al valor|  
|---------------|------------------------------------|--------------------------------|  
|**Apariencia**|**DISP\_STOCKPROP\_APPEARANCE \(\)**|Valor accesible como **m\_sAppearance**.|  
|`BackColor`|**DISP\_STOCKPROP\_BACKCOLOR \(\)**|Valor accesible llamando a `GetBackColor`.|  
|`BorderStyle`|**DISP\_STOCKPROP\_BORDERSTYLE \(\)**|Valor accesible como **m\_sBorderStyle**.|  
|**Leyenda**|**DISP\_STOCKPROP\_CAPTION \(\)**|Valor accesible llamando a `InternalGetText`.|  
|**Enabled**|**DISP\_STOCKPROP\_ENABLED \(\)**|Valor accesible como **m\_bEnabled**.|  
|**Fuente**|**DISP\_STOCKPROP\_FONT \(\)**|Vea el artículo [Controles ActiveX de MFC: Utilizar las fuentes](../mfc/mfc-activex-controls-using-fonts.md) para el uso.|  
|`ForeColor`|**DISP\_STOCKPROP\_FORECOLOR \(\)**|Valor accesible llamando a `GetForeColor`.|  
|**hWnd**|**DISP\_STOCKPROP\_HWND \(\)**|Valor accesible como `m_hWnd`.|  
|**Texto**|**DISP\_STOCKPROP\_TEXT \(\)**|Valor accesible llamando a `InternalGetText`.  Esta propiedad es igual que **caption**, salvo el nombre de propiedad.|  
|**ReadyState**|**DISP\_STOCKPROP\_READYSTATE\(\)**|Valor accesible como m\_lReadyState o `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> Propiedades y notificación comunes  
 La mayoría de las propiedades comunes tienen funciones de notificación que se pueden reemplazar.  Por ejemplo, siempre que se cambie la propiedad de `BackColor` , se llama a la función de `OnBackColorChanged` \(una función miembro de clase de control\).  La implementación predeterminada \(en `COleControl`\) llama `InvalidateControl`.  Invalide esta función si desea tomar medidas adicionales en respuesta a esta situación.  
  
##  <a name="_core_color_properties"></a> Propiedades de colores  
 Puede utilizar `ForeColor` y las propiedades comunes de `BackColor` , o dispone de propiedades de los colores personalizadas, al dibujar el control.  Para utilizar una propiedad color, llame a la función miembro de [COleControl::TranslateColor](../Topic/COleControl::TranslateColor.md) .  Los parámetros de esta función es el valor de la propiedad color y un identificador opcional de la paleta.  El valor devuelto es un valor de **COLORREF** que se puede pasar a funciones de GDI, como `SetTextColor` y `CreateSolidBrush`.  
  
 Los valores de color para `ForeColor` y las propiedades comunes de `BackColor` tiene acceso llamando a `GetForeColor` o la función de `GetBackColor` , respectivamente.  
  
 El ejemplo siguiente muestra cómo utilizar estas propiedades bicolores al pintar un control.  Inicializa una variable temporal de **COLORREF** y un objeto de `CBrush` con llamadas a `TranslateColor`: uno utilizando la propiedad de `ForeColor` y mediante la propiedad de `BackColor` .  Un objeto temporal de `CBrush` se utiliza para pintar el rectángulo del control, y el color del texto se establece mediante la propiedad de `ForeColor` .  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)   
 [Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)