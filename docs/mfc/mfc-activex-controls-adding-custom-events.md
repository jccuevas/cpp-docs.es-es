---
title: "Controles ActiveX MFC: Agregar eventos personalizados | Microsoft Docs"
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
  - "Click (evento), eventos personalizados"
  - "ClickIn (evento)"
  - "COleControl (clase), eventos personalizados"
  - "eventos personalizados"
  - "eventos personalizados, agregar a controles ActiveX"
  - "EVENT_CUSTOM (macro)"
  - "EVENT_CUSTOM (prefijo)"
  - "eventos [C++], controles ActiveX"
  - "FireClickIn (evento)"
  - "FireEvent (método), agregar eventos personalizados"
  - "InCircle (método)"
  - "controles ActiveX en MFC, eventos"
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Controles ActiveX MFC: Agregar eventos personalizados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los eventos personalizados difieren de los eventos comunes en que automáticamente no son desencadenados por la clase `COleControl`.  Un evento personalizado reconoce acción, determinado por el programador de controles, como un evento.  Las entradas del mapa de eventos para los eventos personalizados se representan mediante la macro de `EVENT_CUSTOM` .  La sección siguiente implementa un evento personalizado para un proyecto de control ActiveX creado mediante el asistente para controles ActiveX.  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Agregar un evento personalizado con el asistente para agregar eventos  
 El procedimiento siguiente se agrega un evento personalizado específico, ClickIn.  Puede utilizar este procedimiento para agregar otros eventos personalizados.  Sustituya el nombre de evento personalizado y los parámetros para el nombre de evento y los parámetros de ClickIn.  
  
#### Para agregar el evento personalizado de ClickIn mediante el asistente para agregar eventos  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, haga clic con el botón secundario en la clase de control ActiveX para abrir el menú contextual.  
  
3.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar evento**.  
  
     Se abrirá el asistente para agregar eventos.  
  
4.  En el cuadro de **Nombre de evento** , seleccione primero cualquier evento existente, haga clic en el botón de opción de **Custom** , el tipo `ClickIn`.  
  
5.  En el cuadro de **Nombre interno** , escriba el nombre de la función del desencadenamiento del evento.  En este ejemplo, use el valor predeterminado proporcionado por el asistente para agregar eventos \(`FireClickIn`\).  
  
6.  Agregue un parámetro, denominado `xCoord` \(tipo `OLE_XPOS_PIXELS`\), utilizando los controles de **Nombre del parámetro** y de **Tipo de parámetro** .  
  
7.  Agregue un segundo parámetro, denominado `yCoord` \(tipo `OLE_YPOS_PIXELS`\).  
  
8.  Haga clic en **Finalizar** para crear el evento.  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a> Agregue los cambios del asistente de eventos para los eventos personalizados  
 Cuando se agrega un evento personalizado, el asistente para agregar eventos realiza cambios en la clase de control. Archivos de h, de .CPP, y de .IDL.  Los siguientes ejemplos de código son específicos del evento de ClickIn.  
  
 Las líneas siguientes se agregan al encabezado \(. H\) archivo de clase de control:  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_1.h)]  
  
 Este código declara una función inline denominada `FireClickIn` que llame a [COleControl::FireEvent](../Topic/COleControl::FireEvent.md) con los parámetros de ClickIn que definió mediante el asistente para agregar eventos.  
  
 Además, la siguiente línea se agrega al mapa del control, ubicado en el archivo de implementación \(.CPP\) de la clase de control:  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 Este código asigna el evento ClickIn a la función inline `FireClickIn`, pasando los parámetros que definió mediante el asistente para agregar eventos.  
  
 Finalmente, la siguiente línea se agrega al archivo de .IDL de control:  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 Esta línea asigna a eventos de ClickIn el número de identificación concreto, tomado de la posición del evento en la lista de eventos del asistente para agregar eventos.  La entrada de la lista de eventos permite que un contenedor prever el evento.  Por ejemplo, puede proporcionar el código del controlador que se ejecuta cuando se desencadena el evento.  
  
##  <a name="_core_calling_fireclickin"></a> Llamada FireClickIn  
 Ahora que ha agregado el evento personalizado de ClickIn mediante el asistente para agregar eventos, debe decidir cuando este evento se desencadena.  Puede hacerlo llamando a `FireClickIn` cuando la acción correspondiente aparece.  Para este tutorial, el control utiliza la función de `InCircle` dentro de un controlador de mensajes `WM_LBUTTONDOWN` para desencadenar el evento de ClickIn cuando un usuario haga clic dentro de una región circular o elíptico.  El procedimiento siguiente agrega el controlador de `WM_LBUTTONDOWN` .  
  
#### Para agregar un controlador de mensajes con el asistente para agregar eventos  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, seleccione la clase de control ActiveX.  
  
3.  En la ventana Propiedades, haga clic en el botón **Mensajes**.  
  
     La ventana Propiedades muestra una lista de mensajes que se pueden controlar mediante el control ActiveX.  Cualquier mensaje mostrado en negrita ya tiene una función controladora asignada al.  
  
4.  De la ventana Propiedades, seleccione el mensaje que desea controlar.  Para este ejemplo, seleccione `WM_LBUTTONDOWN`.  
  
5.  En el cuadro de lista desplegable a la derecha, seleccione **\<Add\> OnLButtonDown**.  
  
6.  Haga doble clic en la nueva función de controlador en la vista de clases para saltar al código de controlador de mensajes en el archivo de implementación \(.CPP\) del control ActiveX.  
  
 El siguiente ejemplo de código llama a la función de **InCircle** cada vez que el botón primario se hace clic en la ventana de control.  Este ejemplo se puede encontrar en la función de controlador de `WM_LBUTTONDOWN` , `OnLButtonDown`, en el resumen de [Ejemplo de Circ](../top/visual-cpp-samples.md) .  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  Cuando el asistente para agregar eventos crea controladores de mensajes para las acciones del botón del mouse, una llamada al mismo controlador de mensajes de la clase base se agregará automáticamente.  No quite esta llamada.  Si el control utiliza mensajes comunes cualquiera de los del mouse, los controladores de mensajes en la clase base deben llamar para asegurarse de que la captura del mouse está controlada correctamente.  
  
 En el ejemplo siguiente, el evento se activa cuando el clic se produce dentro de un área circular o elíptica dentro del control.  Para lograr este comportamiento, puede colocar la función de `InCircle` en el archivo de implementación del control \(.CPP\):  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 También necesitará agregar la siguiente declaración de función de `InCircle` al encabezado del control \(. H\) archivo:  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a> Eventos personalizados con nombres de acción  
 Puede crear eventos personalizados con el mismo nombre que los eventos comunes, no obstante no puede implementar ambos en el mismo control.  Por ejemplo, puede crear un evento personalizado denominado el clic en que no desencadena cuando haga clic común de evento se activaría normalmente.  A continuación desencadenar el evento Click en cualquier momento llamando a la función bounce.  
  
 El procedimiento siguiente se agrega un evento Click personalizado.  
  
#### Para agregar un evento personalizado que utiliza un nombre de evento común  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, haga clic con el botón secundario en la clase de control ActiveX para abrir el menú contextual.  
  
3.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar evento**.  
  
     Se abrirá el asistente para agregar eventos.  
  
4.  En la lista desplegable de **Nombre de evento** , seleccione un nombre de evento común.  Para este ejemplo, seleccione **Hacer clic en**.  
  
5.  Para **Tipo de evento**, seleccione **Custom**.  
  
6.  Haga clic en **Finalizar** para crear el evento.  
  
7.  Llame a `FireClick` en los lugares adecuados en el código.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)