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
ms.openlocfilehash: d94f0391c1aebc95b51a1bc94bea28168c445086
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519391"
---
# <a name="handlers-for-message-map-ranges"></a>Controladores para intervalos de mapa de mensajes

En este artículo se explica cómo asignar un intervalo de mensajes a una función de controlador único mensaje (en lugar de asignar un mensaje a solo una función).

Hay veces cuando tiene que procesar más de una notificación de mensaje o control en la misma manera. En estos momentos, es posible que desee asignar todos los mensajes a una función de controlador único. Los intervalos de mapa de mensajes permiten hacer esto para un intervalo contiguo de mensajes:

- Puede asignar intervalos de identificadores de comando para:

  - Una función de controlador de comandos.

  - Una función de controlador de actualización de comandos.

- Puede asignar los mensajes de notificación de control para un intervalo de identificadores de control a una función de controlador de mensaje.

Los temas tratados en este artículo incluyen:

- [Escribir la entrada de mapa de mensajes](#_core_writing_the_message.2d.map_entry)

- [Declarar la función de controlador](#_core_declaring_the_handler_function)

- [Ejemplo de un intervalo de identificadores de comando](#_core_example_for_a_range_of_command_ids)

- [Ejemplo de un intervalo de identificadores de control](#_core_example_for_a_range_of_control_ids)

##  <a name="_core_writing_the_message.2d.map_entry"></a> Escribir la entrada de mapa de mensajes

En. CPP, agregue la entrada de mapa de mensajes, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

La entrada de mapa de mensajes consta de los siguientes elementos:

- La macro de intervalo de mapa de mensajes:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parámetros de la macro:

  Las dos primeras macros toman tres parámetros:

  - El identificador de comando inicial del intervalo

  - El identificador de comando final del intervalo

  - El nombre de la función de controlador de mensaje

  El intervalo de identificadores de comando debe ser contiguo.

  La tercera macro, `ON_CONTROL_RANGE`, toma un parámetro adicional de primera: mensaje de notificación de control, como **EN_CHANGE**.

##  <a name="_core_declaring_the_handler_function"></a> Declarar la función de controlador

Agregue la declaración de función de controlador en el. Archivo de H. El código siguiente muestra cómo se podría hacer, como se muestra a continuación:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Funciones del controlador de comandos individuales normalmente no toman ningún parámetro. A excepción de las funciones de controlador de actualización, las funciones de controlador de intervalos de mapa de mensajes requieren un parámetro adicional, *nID*, del tipo **UINT**. Este parámetro es el primer parámetro. El parámetro adicional adapta el identificador de comando adicional necesario para especificar qué comando seleccionó realmente el usuario.

Para obtener más información sobre los requisitos de parámetros de funciones del controlador de actualización, vea [para un intervalo de identificadores de comando de ejemplo](#_core_example_for_a_range_of_command_ids).

##  <a name="_core_example_for_a_range_of_command_ids"></a> Ejemplo de un intervalo de identificadores de comandos

Es posible que al usar intervalos es un ejemplo en el control de comandos, como el comando de Zoom en el ejemplo MFC [HIERSVR](../visual-cpp-samples.md). Este comando permite variar el tamaño de la vista entre 25 y 300% de su tamaño normal. Clase de vista de HIERSVR utiliza un intervalo para controlar los comandos de Zoom con una entrada de mapa de mensajes parecida a ésta:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Al escribir la entrada de mapa de mensajes, especifica:

- Dos identificadores de comando inicial y final de un intervalo contiguo.

   Aquí están **ID_VIEW_ZOOM25** y **ID_VIEW_ZOOM300**.

- El nombre de la función de controlador para los comandos.

   Aquí tiene `OnZoom`.

La declaración de función podría ser similar a esto:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

El caso de funciones del controlador de actualización es probable que sea más útiles y similares. Es bastante común escribir `ON_UPDATE_COMMAND_UI` controladores para una serie de comandos y descubre que tiene que escribir o copiar, el mismo código una y otra vez. La solución es asignar un intervalo del comando actualizarán de identificadores a una función de controlador mediante la `ON_UPDATE_COMMAND_UI_RANGE` macro. Los identificadores de comando deben formar un intervalo contiguo. Para obtener un ejemplo, vea el `OnUpdateZoom` controlador y su `ON_UPDATE_COMMAND_UI_RANGE` entrada de mapa de mensajes en la clase de vista del ejemplo HIERSVR.

La actualización de las funciones de controlador para comandos únicos normalmente toman un único parámetro, *pCmdUI*, del tipo `CCmdUI*`. A diferencia de las funciones de controlador, las funciones de controlador de actualización para intervalos de mapa de mensajes no requieren un parámetro adicional, *nID*, del tipo **UINT**. El identificador de comando, que es necesarias para especificar que el usuario seleccionó realmente de comandos, se encuentra en la `CCmdUI` objeto.

##  <a name="_core_example_for_a_range_of_control_ids"></a> Ejemplo de un intervalo de identificadores de controles

Otro caso interesante está asignando los mensajes de notificación de control para un intervalo de identificadores de control a un único controlador. Supongamos que el usuario puede pulsar cualquiera de los botones de 10. Para asignar todos los botones de 10 a un controlador, la entrada de mapa de mensajes tendría este aspecto:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Al escribir el `ON_CONTROL_RANGE` macro en el mapa de mensajes, especifica:

- Un mensaje de notificación de control determinado.

   Aquí tiene **BN_CLICKED**.

- Los valores de Id. del control asociados al intervalo contiguo de controles.

   Aquí son **IDC_BUTTON1** y **IDC_BUTTON10**.

- El nombre de la función de controlador de mensajes.

   Aquí tiene `OnButtonClicked`.

Cuando se escribe la función de controlador, especifique el archivo extra **UINT** parámetro, como se muestra en la siguiente:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

El `OnButtonClicked` controlador para un único **BN_CLICKED** mensaje no toma ningún parámetro. El mismo controlador para un intervalo de botones toma uno **UINT**. El parámetro adicional permite identificar el control particular responsable de generar el **BN_CLICKED** mensaje.

El código que se muestra en el ejemplo es típico: convertir el valor pasado a un `int` dentro del intervalo de mensajes y si éste es el caso de la aserción. A continuación, puede realizar diferentes acciones, dependiendo de qué botón se hizo clic.

## <a name="see-also"></a>Vea también

[Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
