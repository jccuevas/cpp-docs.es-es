---
title: "Controles ActiveX MFC: Agregar propiedades personalizadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX en MFC, propiedades"
  - "propiedades [MFC], personalizadas"
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Agregar propiedades personalizadas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las propiedades personalizadas difieren de las propiedades comunes en ese propiedades personalizadas no se implementan ya por la clase de `COleControl` .  Una propiedad personalizada se utiliza para exponer algún estado o apariencia de un control ActiveX a un programador mediante el control.  
  
 En este artículo se describe cómo agregar una propiedad personalizada al control ActiveX mediante el asistente para agregar propiedades y explica las modificaciones resultantes de código.  Entre los temas se incluyen los siguientes:  
  
-   [Mediante el asistente para agregar propiedades para agregar una propiedad personalizada](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [Agregue los cambios del asistente de las propiedades personalizadas](#_core_classwizard_changes_for_custom_properties)  
  
 Las propiedades personalizadas proceden de cuatro variedades de implementación: La variable miembro, variable miembro con la notificación, get\/set, y Parametrizada.  
  
-   Implementación de variable miembro  
  
     Esta implementación representa el estado de la propiedad como variable miembro en la clase de control.  Utilice la implementación de variable miembro cuando no es importante saber cuándo cambia el valor de propiedad.  De los tres tipos, esta implementación crea la menor cantidad de código de soporte para la propiedad.  La macro de entrada de asignación de distribución para la implementación de la variable miembro es [DISP\_PROPERTY](../Topic/DISP_PROPERTY.md).  
  
-   Variable miembro con la aplicación de notificación  
  
     Esta implementación se compone de una variable miembro y una función de notificación creada por el asistente para agregar propiedades.  La función de notificación automáticamente a los que llama el marco después de que el valor de propiedad.  Utilice la variable miembro con la aplicación de notificación cuando necesita recibir una notificación cuando un valor de propiedad ha cambiado.  Esta implementación requiere más tiempo porque requiere una llamada de función.  La macro de entrada de asignación de envío para esta implementación es [DISP\_PROPERTY\_NOTIFY](../Topic/DISP_PROPERTY_NOTIFY.md).  
  
-   Get\/set la implementación de los métodos  
  
     Esta implementación se compone de un par de funciones miembro de la clase de control.  La implementación de los métodos get\/set llama automáticamente a la función miembro get cuando funcionan las solicitudes de usuario del control el valor actual de la propiedad y el miembro determinado cuando las solicitudes de usuario del control que la propiedad se cambie.  Utilice esta implementación cuando necesite calcular el valor de una propiedad en tiempo de ejecución, validar un valor pasado por el usuario del control antes de cambiar la propiedad real, o implementar un tipo de propiedad leída o de sólo escritura.  La macro de entrada de asignación de envío para esta implementación es [DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md).  La sección siguiente, [Mediante el asistente para agregar propiedades para agregar una propiedad personalizada](#_core_using_classwizard_to_add_a_custom_property), utiliza la propiedad personalizada de CircleOffset para mostrar esta implementación.  
  
-   Implementación con parámetros  
  
     La implementación con parámetros admitida por el asistente para agregar propiedades.  Una propiedad con parámetros \(denominada en ocasiones una matriz de propiedades\) se puede utilizar para tener acceso a un conjunto de valores a través de una propiedad de control.  La macro de entrada de asignación de envío para esta implementación es `DISP_PROPERTY_PARAM`.  Para obtener más información sobre la implementación de este tipo, vea [Implementar una propiedad de Parametrizada](../mfc/mfc-activex-controls-advanced-topics.md) en Controles ActiveX de caso: Temas avanzados.  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> Mediante el asistente para agregar propiedades para agregar una propiedad personalizada  
 El procedimiento siguiente muestra cómo agregar una propiedad personalizada, CircleOffset, que utiliza la implementación de los métodos get\/set.  La propiedad personalizada de CircleOffset permite al usuario del control del círculo del centro del rectángulo delimitador del control.  El procedimiento para agregar propiedades personalizadas con una implementación distinta de get\/set es muy similar.  
  
 Este mismo procedimiento también se puede utilizar para agregar otras propiedades personalizadas que desee.  Sustituya el nombre de propiedad personalizado para el nombre y los parámetros de CircleOffset.  
  
#### Para agregar la propiedad personalizada de CircleOffset mediante el asistente para agregar propiedades  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, expanda el nodo de biblioteca de controles.  
  
3.  Haga clic con el botón secundario en el nodo de la interfaz del control \(el segundo nodo el nodo de biblioteca\) para abrir el menú contextual.  
  
4.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar propiedad**.  
  
     Esto abre [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).  
  
5.  En el cuadro de **Nombre de propiedad** , `CircleOffset`escrito.  
  
6.  Para **Tipo de implementación**, haga clic en **Get\/Set Methods**.  
  
7.  En el cuadro de **Tipo de propiedad** , seleccione **corto**.  
  
8.  Los nombres únicos de tipos para las funciones get y set, o aceptan los nombres predeterminados.  
  
9. Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a> Agregue los cambios del asistente de las propiedades personalizadas  
 Cuando se agrega una propiedad personalizada de CircleOffset, el asistente para agregar realiza cambios en el encabezado \(. H\) y los archivos de implementación \(.CPP\) de la clase de control.  
  
 Las líneas siguientes se agregan a. El archivo de h para declarar dos funciones denominado `GetCircleOffset` y `SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 La siguiente línea se agrega al archivo de .IDL de control:  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 Esta línea asigna a propiedad de CircleOffset el número de identificación concreto, tomado de la posición de los métodos y la lista de propiedades del asistente para agregar propiedades.  
  
 Además, la siguiente línea se agrega al mapa de envío \(en el archivo de .CPP de la clase de control\) para asignar la propiedad de CircleOffset a las funciones de controlador de control dos:  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 Finalmente, las implementaciones de `GetCircleOffset` y las funciones de `SetCircleOffset` se agregan al final del archivo de .CPP del control.  En la mayoría de los casos, modificará la función get para devolver el valor de la propiedad.  La función determinada contendrá normalmente el código que debe ejecutarse antes o después de que la propiedad cambia.  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 Observe que el asistente para agregar agrega automáticamente una llamada, a [SetModifiedFlag](../Topic/COleControl::SetModifiedFlag.md), el cuerpo de la función determinada.  Llamando a esta función marca el control como modificado.  Si se ha modificado un control, guardar el nuevo estado cuando se guarda el contenedor.  Esta función debe llamar siempre que una propiedad, guardará como parte del estado persistente de control, cambie valor.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)   
 [Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)