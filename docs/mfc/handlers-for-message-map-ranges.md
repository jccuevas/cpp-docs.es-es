---
title: Controladores para intervalos de mapa de mensajes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be596ea38a8d0a3919ed43d9c5478bb0127032d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351727"
---
# <a name="handlers-for-message-map-ranges"></a>Controladores para intervalos de mapa de mensajes
En este artículo se explica cómo asignar un intervalo de mensajes a una función de controlador único mensaje (en lugar de asignar un mensaje a solo una función).  
  
 Hay ocasiones cuando tiene que procesar más de una notificación de mensaje o control en la misma forma. En estos momentos, es posible que quiera todos los mensajes se asignan a una función de controlador único. Rangos de asignación de mensaje le permiten hacer esto para un intervalo contiguo de mensajes:  
  
-   Puede asignar intervalos de identificadores de comando para:  
  
    -   Una función de controlador de comandos.  
  
    -   Una función de controlador de actualización de comandos.  
  
-   Puede asignar los mensajes de notificación de controles para un intervalo de identificadores de control a una función de controlador de mensaje.  
  
 Los temas tratados en este artículo son:  
  
-   [Escribir la entrada de mapa de mensajes](#_core_writing_the_message.2d.map_entry)  
  
-   [Declarar la función de controlador](#_core_declaring_the_handler_function)  
  
-   [Ejemplo para un intervalo de identificadores de comando](#_core_example_for_a_range_of_command_ids)  
  
-   [Ejemplo para un intervalo de identificadores de control](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> Escribir la entrada de mapa de mensajes  
 En. CPP Archivo, agregue la entrada de mapa de mensajes, como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]  
  
 La entrada de mapa de mensajes consta de los siguientes elementos:  
  
-   La macro del intervalo de mapa de mensajes:  
  
    -   [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)  
  
    -   [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)  
  
    -   [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)  
  
-   Parámetros de la macro:  
  
     Las dos primeras macros reciben tres parámetros:  
  
    -   El identificador de comando inicial del intervalo  
  
    -   El identificador de comando final del intervalo  
  
    -   El nombre de la función de controlador de mensaje  
  
     El intervalo de identificadores de comando debe ser contiguo.  
  
     La tercera macro, `ON_CONTROL_RANGE`, toma un parámetro primera adicional: mensaje de notificación de controles, como **EN_CHANGE**.  
  
##  <a name="_core_declaring_the_handler_function"></a> Declarar la función de controlador  
 Agregue la declaración de función de controlador en el. H del proyecto. El código siguiente muestra cómo podría quedar esto, tal y como se muestra a continuación:  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]  
  
 Funciones del controlador de comandos individuales no reciben parámetros normalmente. Con la excepción de las funciones de controlador de actualización, las funciones de controlador de intervalos de mapa de mensajes requieren un parámetro adicional, `nID`, del tipo **UINT**. Este parámetro es el primer parámetro. El parámetro adicional adapta el identificador de comando adicional necesario para especificar qué comando seleccionó realmente el usuario.  
  
 Para obtener más información acerca de los requisitos de parámetro para la actualización de las funciones de controlador, consulte [ejemplo para un intervalo de identificadores de comando](#_core_example_for_a_range_of_command_ids).  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> Ejemplo de un intervalo de identificadores de comandos  
 Cuándo se podrían utilizar intervalos de un ejemplo de control de comandos, como el comando Zoom en el ejemplo MFC [HIERSVR](../visual-cpp-samples.md). Este comando permite acercar la vista, ajuste de escala entre 25% y un 300% de su tamaño normal. Clase de vista de HIERSVR utiliza un intervalo para controlar los comandos de Zoom con una entrada de mapa de mensajes parecida a ésta:  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]  
  
 Al escribir la entrada de mapa de mensajes, puede especificar:  
  
-   Dos identificadores de comando, apertura y cierre de un intervalo contiguo.  
  
     Aquí están `ID_VIEW_ZOOM25` y `ID_VIEW_ZOOM300`.  
  
-   El nombre de la función de controlador para los comandos.  
  
     Aquí tiene `OnZoom`.  
  
 La declaración de función se parecería al siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]  
  
 El caso de funciones del controlador de actualización es similar y es probable que sean más útiles. Es bastante habitual al escribir `ON_UPDATE_COMMAND_UI` controladores para una serie de comandos y descubre que tiene que escribir o copiar, el mismo código una y otra vez. La solución consiste en asignar un intervalo de comando actualizarán de identificadores a una función de controlador mediante la `ON_UPDATE_COMMAND_UI_RANGE` macro. Los identificadores de comando deben formar un intervalo contiguo. Para obtener un ejemplo, vea el **OnUpdateZoom** controlador y sus `ON_UPDATE_COMMAND_UI_RANGE` entrada de mapa de mensajes en la clase de vista del ejemplo HIERSVR.  
  
 Actualizar funciones del controlador de comandos únicas normalmente toman un único parámetro, `pCmdUI`, del tipo **CCmdUI\***. A diferencia de las funciones de controlador, las funciones del controlador de actualización para intervalos de mapa de mensajes no requieren un parámetro adicional, `nID`, del tipo **UINT**. El identificador de comando, que es necesario para especificar qué comando seleccionó realmente el usuario, se encuentra en la `CCmdUI` objeto.  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> Ejemplo de un intervalo de identificadores de controles  
 Otro caso interesante consiste en asignar mensajes de notificación de controles para un intervalo de identificadores de control a un único controlador. Suponga que el usuario puede hacer clic en cualquiera de los botones de 10. Para asignar los 10 botones a un controlador, la entrada de mapa de mensajes sería similar al siguiente:  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]  
  
 Al escribir el `ON_CONTROL_RANGE` macro en el mapa de mensajes, especifique:  
  
-   Un mensaje de notificación de control determinado.  
  
     Aquí tiene **BN_CLICKED**.  
  
-   Los valores de Id. del control asociados al intervalo contiguo de controles.  
  
     Aquí se trata de `IDC_BUTTON1` y `IDC_BUTTON10`.  
  
-   El nombre de la función de controlador de mensaje.  
  
     Aquí tiene `OnButtonClicked`.  
  
 Cuando se escribe la función de controlador, especifique el archivo extra **UINT** parámetro, tal como se muestra a continuación:  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]  
  
 El `OnButtonClicked` controlador para una sola **BN_CLICKED** mensaje no toma ningún parámetro. El mismo controlador para un intervalo de botones toma una **UINT**. El parámetro adicional permite identificar el control particular responsable de generar el **BN_CLICKED** mensaje.  
  
 El código se muestra en el ejemplo es típico: convierte el valor pasado a un `int` dentro del intervalo de mensajes y si éste es el caso de la aserción. A continuación, puede realizar diferentes acciones, dependiendo de qué botón se hizo clic.  
  
## <a name="see-also"></a>Vea también  
 [Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
