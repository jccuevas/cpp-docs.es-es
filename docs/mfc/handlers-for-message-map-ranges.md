---
title: "Controladores para intervalos de mapa de mensajes | Microsoft Docs"
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
  - "control de comandos, controladores de actualización de comandos"
  - "identificadores de comando, asignar mensajes"
  - "enrutamiento de comandos, controladores de actualización de comandos"
  - "controladores de actualización de comandos"
  - "mensajes de notificación de controles"
  - "controles [MFC], notificaciones"
  - "funciones controladoras"
  - "funciones controladoras, declarar"
  - "funciones controladoras, rangos de asignación de mensajes"
  - "controladores"
  - "controladores, rangos de asignación de mensajes"
  - "asignaciones, rangos de mensajes"
  - "controladores de mensajes"
  - "control de mensajes, funciones del controlador de mensajes"
  - "mapas de mensajes, funciones del controlador de mensajes"
  - "mapas de mensajes, intervalos"
  - "rangos de mensajes"
  - "rangos de mensajes, asignar"
  - "rangos de asignación de mensajes"
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controladores para intervalos de mapa de mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo asignar un intervalo de mensajes a una sola función de controlador de mensajes \(en lugar de mensaje de asignación una a una sola función\).  
  
 Hay ocasiones en que necesita procesar más de una notificación de mensaje o control de la misma manera.  En esas ocasiones, puede ser conveniente asignar todos los mensajes a una sola función de controlador.  Los intervalos de Mensaje\- mapa permiten hacerlo para un intervalo contiguo de mensajes:  
  
-   Puede asignar intervalos de los id. de comando:  
  
    -   Una función de controlador de comandos.  
  
    -   Una función de controlador de actualización del comando.  
  
-   Puede asignar los mensajes de la CONTROL\- notificación para un intervalo de los id. de control a una función de controlador de mensajes.  
  
 Temas cubiertos en incluyen de caso:  
  
-   [Escribir la entrada de mensaje\- mapa](#_core_writing_the_message.2d.map_entry)  
  
-   [Declarar la función controladora](#_core_declaring_the_handler_function)  
  
-   [Ejemplo de un intervalo de los id. de comando](#_core_example_for_a_range_of_command_ids)  
  
-   [Ejemplo de un intervalo de los id. de control](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> Escribir la entrada de Mensaje\- mapa  
 En el archivo de .CPP, agregue la entrada de mensaje\- mapa, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_1.cpp)]  
  
 La entrada de mensaje\- mapa se compone de los elementos siguientes:  
  
-   La macro de intervalo de mensaje\- mapa:  
  
    -   [ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md)  
  
    -   [ON\_UPDATE\_COMMAND\_UI\_RANGE](../Topic/ON_UPDATE_COMMAND_UI_RANGE.md)  
  
    -   [ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md)  
  
-   Parámetros a la macro:  
  
     Las primeras dos macros toma tres parámetros:  
  
    -   El identificador de comando que comienza el intervalo  
  
    -   El identificador de comando que finaliza el intervalo  
  
    -   El nombre de la función de controlador de mensajes  
  
     El intervalo de los id. del comando debe ser contiguo.  
  
     La tercera macro, `ON_CONTROL_RANGE`, toma un primer parámetro adicional: un mensaje de la CONTROL\- notificación, como **EN\_CHANGE**.  
  
##  <a name="_core_declaring_the_handler_function"></a> Declarar la función controladora  
 Agregue la declaración de función de controlador en. Archivo de h.  El código siguiente muestra cómo esto puede examinar, como se muestra a continuación:  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_2.h)]  
  
 Las funciones controladoras para los únicos comandos no tienen normalmente ningún parámetro.  Excepto para las funciones de controlador de actualización, las funciones de controlador en intervalos de mensaje\- mapa requieren un parámetro adicional, `nID`, de **UINT**escrito.  Este parámetro es el primer parámetro.  El parámetro adicional aloja el identificador adicional de comando necesario para especificar que el comando el usuario eligió realmente.  
  
 Para obtener más información sobre los requisitos de parámetro para actualizar funciones de controlador, vea [Ejemplo de un intervalo de los id. de comando](#_core_example_for_a_range_of_command_ids).  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> Ejemplo de un intervalo de los id. de comando  
 ¿Cuándo puede ser que utilice intervalos?  Un ejemplo consta de administrar comandos como el comando de zoom en el ejemplo [HIERSVR](../top/visual-cpp-samples.md)MFC.  Este comando sobre la vista, escalandola entre el 25% y el 300% de su tamaño normal.  La clase de la vista de HIERSVR utiliza un intervalo para controlar los comandos de zoom con una entrada de mensaje\- mapa que se parece a lo siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_3.cpp)]  
  
 Cuando escribe la entrada de mensaje\- mapa, especifique:  
  
-   Dos id., principios y finales de comandos un intervalo contiguo.  
  
     Aquí son `ID_VIEW_ZOOM25` y `ID_VIEW_ZOOM300`.  
  
-   El nombre de la función controladora para los comandos.  
  
     Aquí es `OnZoom`.  
  
 La declaración de función se parecería al siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_4.h)]  
  
 El caso de funciones de controlador de actualización es similar, y puede ser más muy útil.  Es muy común escribir controladores de `ON_UPDATE_COMMAND_UI` para varios comandos y encontrarse escritura, o la copia, el mismo código repetidamente.  La solución es asignar un intervalo de los id. de comando a una función de controlador de actualización mediante la macro de `ON_UPDATE_COMMAND_UI_RANGE` .  Los id. de comando deben formar un intervalo contiguo.  Para obtener un ejemplo, vea el controlador de **OnUpdateZoom** y su entrada de mensaje\- mapa de `ON_UPDATE_COMMAND_UI_RANGE` en la clase de la vista del ejemplo HIERSVR.  
  
 Las funciones de controlador de actualización para los únicos comandos tienen normalmente un único parámetro, `pCmdUI`, de **CCmdUI\***escrito.  A diferencia de las funciones de controlador, las funciones de controlador de actualización para los intervalos de mensaje\- mapa no requieren un parámetro adicional, `nID`, de **UINT**escrito.  El identificador de comando, que es necesario especificar que el comando el usuario eligió realmente, se encuentra en el objeto de `CCmdUI` .  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> Ejemplo de un intervalo de los id. de Control  
 Otro caso interesante está asignando los mensajes de la CONTROL\- notificación para un intervalo de los id. del control a un único controlador.  Suponga que el usuario puede hacer clic en cualquier de 10 botones.  Para asignar los 10 botones un controlador, la entrada de mensaje\- mapa se parecería al siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_5.cpp)]  
  
 Cuando escribe la macro de `ON_CONTROL_RANGE` en el mapa de mensajes, se especifica:  
  
-   Un mensaje determinado de la CONTROL\-notificación.  
  
     Aquí es **BN\_CLICKED**.  
  
-   Los valores del identificador de control asociados al intervalo contiguo de controles.  
  
     Aquí son `IDC_BUTTON1` y `IDC_BUTTON10`.  
  
-   El nombre de la función de controlador de mensajes.  
  
     Aquí es `OnButtonClicked`.  
  
 Cuando escribe la función controladora, especifique el parámetro adicional de **UINT** , como se muestra en el siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_6.cpp)]  
  
 El controlador de `OnButtonClicked` para un único mensaje de **BN\_CLICKED** no toma ningún parámetro.  El mismo controlador para un intervalo de botones toma un **UINT**.  El parámetro adicional permite identificar el control determinado responsable de generar el mensaje de **BN\_CLICKED** .  
  
 El código mostrado en el ejemplo es típico: convertir el valor pasado a `int` dentro del mensaje se extienden y la aserción de que éste es el caso.  A continuación puede adoptar ciertas acciones distintas en función de las que se hizo clic en el botón.  
  
## Vea también  
 [Declarar funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)