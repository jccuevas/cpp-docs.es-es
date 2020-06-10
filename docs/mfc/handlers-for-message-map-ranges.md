---
title: Controladores para intervalos de mapa de mensajes
ms.date: 11/04/2016
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
ms.openlocfilehash: 0ff9178679792929bbd6eb92bb6148cfa008dcad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621690"
---
# <a name="handlers-for-message-map-ranges"></a>Controladores para intervalos de mapa de mensajes

En este artículo se explica cómo asignar un intervalo de mensajes a una única función de controlador de mensajes (en lugar de asignar un mensaje a una sola función).

Hay ocasiones en las que es necesario procesar más de un mensaje o notificación de control exactamente de la misma manera. En ese momento, es posible que desee asignar todos los mensajes a una única función de controlador. Los intervalos de mapa de mensajes permiten hacer esto para un intervalo de mensajes contiguo:

- Puede asignar intervalos de identificadores de comando a:

  - Función de controlador de comandos.

  - Función de controlador de actualización de comandos.

- Puede asignar mensajes de notificación de control para un intervalo de identificadores de control a una función de controlador de mensajes.

Los temas que se tratan en este artículo son:

- [Escribir la entrada del mapa de mensajes](#_core_writing_the_message.2d.map_entry)

- [Declarar la función de controlador](#_core_declaring_the_handler_function)

- [Ejemplo de un intervalo de identificadores de comando](#_core_example_for_a_range_of_command_ids)

- [Ejemplo de un intervalo de identificadores de control](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Escribir la entrada del mapa de mensajes

En. Archivo CPP, agregue la entrada de mapa de mensajes, tal y como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCMessageHandling#6](codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

La entrada de mapa de mensajes consta de los siguientes elementos:

- La macro de intervalo de mapa de mensajes:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parámetros para la macro:

  Las dos primeras macros toman tres parámetros:

  - El identificador de comando que inicia el intervalo

  - Identificador de comando que finaliza el intervalo.

  - El nombre de la función de controlador de mensajes

  El intervalo de identificadores de comando debe ser contiguo.

  La tercera macro, `ON_CONTROL_RANGE` , toma un primer parámetro adicional: un mensaje de notificación de control, como **EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Declarar la función de controlador

Agregue la declaración de función de controlador en. H archivo. En el código siguiente se muestra el aspecto que podría tener, como se muestra a continuación:

[!code-cpp[NVC_MFCMessageHandling#7](codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Normalmente, las funciones de controlador para comandos individuales no toman ningún parámetro. A excepción de las funciones de controlador de actualización, las funciones de controlador para los intervalos de mapa de mensajes requieren un parámetro adicional, *nID*, de tipo **uint**. Este parámetro es el primer parámetro. El parámetro adicional aloja el identificador de comando adicional necesario para especificar qué comando eligió realmente el usuario.

Para obtener más información sobre los requisitos de parámetros para actualizar las funciones del controlador, vea [ejemplo de un intervalo de identificadores de comandos](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Ejemplo de un intervalo de identificadores de comando

Cuando puede usar intervalos, un ejemplo es en el control de comandos como el comando zoom en el ejemplo [HIERSVR](../overview/visual-cpp-samples.md)de MFC. Este comando amplía la vista y la escala entre el 25% y el 300% del tamaño normal. La clase de vista de HIERSVR usa un intervalo para controlar los comandos de zoom con una entrada de mapa de mensajes similar a la siguiente:

[!code-cpp[NVC_MFCMessageHandling#8](codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Al escribir la entrada del mapa de mensajes, especifique:

- Dos identificadores de comando, que comienzan y finalizan un intervalo contiguo.

   Aquí son **ID_VIEW_ZOOM25** y **ID_VIEW_ZOOM300**.

- Nombre de la función de controlador para los comandos.

   Aquí está `OnZoom` .

La declaración de función sería similar a la siguiente:

[!code-cpp[NVC_MFCMessageHandling#9](codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

El caso de las funciones de controlador de actualización es similar y es probable que sea más útil. Es bastante común escribir `ON_UPDATE_COMMAND_UI` Controladores para una serie de comandos y buscar, o copiar, el mismo código una y otra vez. La solución consiste en asignar un intervalo de identificadores de comando a una función de controlador de actualización mediante la `ON_UPDATE_COMMAND_UI_RANGE` macro. Los identificadores de comando deben formar un intervalo contiguo. Para obtener un ejemplo, vea el `OnUpdateZoom` controlador y su `ON_UPDATE_COMMAND_UI_RANGE` entrada de mapa de mensajes en la clase de vista del ejemplo de HIERSVR.

Las funciones de controlador de actualización para comandos únicos normalmente toman un único parámetro, *pCmdUI*, de tipo `CCmdUI*` . A diferencia de las funciones de controlador, las funciones de controlador de actualización para los intervalos de mapa de mensajes no requieren un parámetro adicional, *nID*, de tipo **uint**. El identificador de comando, que es necesario para especificar el comando que el usuario eligió realmente, se encuentra en el `CCmdUI` objeto.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Ejemplo de un intervalo de identificadores de control

Otro caso interesante es la asignación de mensajes de notificación de control para un intervalo de identificadores de control a un solo controlador. Supongamos que el usuario puede hacer clic en cualquiera de los 10 botones. Para asignar los 10 botones a un controlador, la entrada del mapa de mensajes tendría el siguiente aspecto:

[!code-cpp[NVC_MFCMessageHandling#10](codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Al escribir la `ON_CONTROL_RANGE` macro en el mapa de mensajes, especifique:

- Un mensaje de notificación de control determinado.

   Aquí es **BN_CLICKED**.

- Los valores de identificador de control asociados al intervalo de controles contiguos.

   Estos son **IDC_BUTTON1** y **IDC_BUTTON10**.

- Nombre de la función de controlador de mensajes.

   Aquí está `OnButtonClicked` .

Al escribir la función de controlador, especifique el parámetro **uint** adicional, como se muestra a continuación:

[!code-cpp[NVC_MFCMessageHandling#11](codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

El `OnButtonClicked` controlador de un único mensaje de **BN_CLICKED** no toma ningún parámetro. El mismo controlador para un intervalo de botones toma un **uint**. El parámetro adicional permite identificar el control determinado responsable de generar el mensaje de **BN_CLICKED** .

El código que se muestra en el ejemplo es típico: convertir el valor pasado a un `int` dentro del intervalo de mensajes y declarar que este es el caso. Después, puede realizar alguna acción diferente en función del botón en el que se hizo clic.

## <a name="see-also"></a>Consulte también

[Declarar funciones del controlador de mensajes](declaring-message-handler-functions.md)
