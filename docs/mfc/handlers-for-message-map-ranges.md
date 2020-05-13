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
ms.openlocfilehash: fc33df6957beab6e4e8de3093dfc00cf2651780e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370508"
---
# <a name="handlers-for-message-map-ranges"></a>Controladores para intervalos de mapa de mensajes

En este artículo se explica cómo asignar un intervalo de mensajes a una sola función de controlador de mensajes (en lugar de asignar un mensaje a una sola función).

Hay ocasiones en las que necesita procesar más de un mensaje o controlar la notificación exactamente de la misma manera. En esos momentos, es posible que desee asignar todos los mensajes a una sola función de controlador. Los intervalos de mapa de mensajes le permiten hacer esto para un rango contiguo de mensajes:

- Puede asignar rangos de ideos de comando a:

  - Una función de controlador de comandos.

  - Una función de controlador de actualización de comandos.

- Puede asignar mensajes de notificación de control para un intervalo de id de control a una función de controlador de mensajes.

Los temas tratados en este artículo incluyen:

- [Escribir la entrada del mapa de mensajes](#_core_writing_the_message.2d.map_entry)

- [Declarar la función de controlador](#_core_declaring_the_handler_function)

- [Ejemplo para un rango de ideos de comando](#_core_example_for_a_range_of_command_ids)

- [Ejemplo para una gama de iDE de control](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Escribir la entrada de mapa de mensajes

En. CPP, agregue la entrada del mapa de mensajes, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

La entrada de mapa de mensajes consta de los siguientes elementos:

- La macro de rango de mapa de mensajes:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parámetros de la macro:

  Las dos primeras macros toman tres parámetros:

  - El identificador de comando que inicia el intervalo

  - El identificador de comando que finaliza el intervalo

  - El nombre de la función de controlador de mensajes

  El intervalo de los ides de comando debe ser contiguo.

  La tercera `ON_CONTROL_RANGE`macro, , toma un primer parámetro adicional: un mensaje de notificación de control, como **EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Declaración de la función de manipulación

Agregue la declaración de función de controlador en el archivo . Archivo H. El código siguiente muestra cómo podría verse esto, como se muestra a continuación:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Las funciones de controlador para comandos individuales normalmente no toman parámetros. Con la excepción de las funciones de controlador de actualización, las funciones de controlador para los intervalos de mapa de mensajes requieren un parámetro adicional, *nID*, de tipo **UINT**. Este parámetro es el primer parámetro. El parámetro adicional acomoda el ID de comando adicional necesario para especificar qué comando eligió realmente el usuario.

Para obtener más información acerca de los requisitos de parámetros para actualizar las funciones de controlador, vea [Ejemplo para un intervalo de id de comando .](#_core_example_for_a_range_of_command_ids)

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Ejemplo para un rango de ideos de comando

When might you use ranges One example is on handling commands like the Zoom command in the MFC sample [HIERSVR](../overview/visual-cpp-samples.md). Este comando amplía la vista, escalando entre el 25% y el 300% de su tamaño normal. La clase de vista de HIERSVR utiliza un rango para manejar los comandos Zoom con una entrada de mapa de mensajes que se asemeja a esto:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Al escribir la entrada de mapa de mensajes, especifique:

- Dos identificaciones de comando, comenzando y terminando un rango contiguo.

   Aquí están **ID_VIEW_ZOOM25** y **ID_VIEW_ZOOM300.**

- El nombre de la función de controlador para los comandos.

   Aquí está `OnZoom`.

La declaración de función se asemejaría a esto:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

El caso de las funciones del controlador de actualización es similar y es probable que sea más útil. Es bastante común escribir `ON_UPDATE_COMMAND_UI` controladores para una serie de comandos y encontrarse escribiendo, o copiando, el mismo código una y otra vez. La solución consiste en asignar un intervalo de elementos `ON_UPDATE_COMMAND_UI_RANGE` de comando a una función de controlador de actualización mediante la macro. Los nombres de comando deben formar un intervalo contiguo. Para obtener un `OnUpdateZoom` ejemplo, `ON_UPDATE_COMMAND_UI_RANGE` vea el controlador y su entrada de mapa de mensajes en la clase de vista del ejemplo HIERSVR.

Las funciones de controlador de actualización para comandos `CCmdUI*`individuales normalmente toman un único parámetro, *pCmdUI*, de tipo . A diferencia de las funciones de controlador, las funciones de controlador de actualización para los intervalos de mapa de mensajes no requieren un parámetro adicional, *nID*, de tipo **UINT**. El identificador de comando, que es necesario para especificar qué `CCmdUI` comando eligió realmente el usuario, se encuentra en el objeto.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Ejemplo para un rango de datos de control

Otro caso interesante es la asignación de mensajes de notificación de control para un intervalo de controladores de control a un único controlador. Supongamos que el usuario puede hacer clic en cualquiera de los 10 botones. Para asignar los 10 botones a un controlador, la entrada del mapa de mensajes tendría este aspecto:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Al escribir `ON_CONTROL_RANGE` la macro en el mapa de mensajes, especifique:

- Un mensaje de notificación de control determinado.

   Aquí está **BN_CLICKED**.

- Los valores de identificador de control asociados con el intervalo contiguo de controles.

   Aquí están **IDC_BUTTON1** y **IDC_BUTTON10**.

- El nombre de la función de controlador de mensajes.

   Aquí está `OnButtonClicked`.

Al escribir la función de controlador, especifique el parámetro **UINT** adicional, como se muestra a continuación:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

El `OnButtonClicked` controlador de un único **mensaje de BN_CLICKED** no toma ningún parámetro. El mismo controlador para un rango de botones toma un **UINT**. El parámetro adicional permite identificar el control determinado responsable de generar el **mensaje BN_CLICKED.**

El código que se muestra en el ejemplo `int` es típico: convertir el valor pasado a un dentro del intervalo de mensajes y afirmar que este es el caso. A continuación, puede realizar alguna acción diferente dependiendo del botón en el que se hizo clic.

## <a name="see-also"></a>Consulte también

[Declarar funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
