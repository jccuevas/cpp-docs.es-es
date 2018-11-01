---
title: Usar campos de devolución de llamada en un control de selector de fecha y hora
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 82dd4bac53b419b531f512aff859510d6603d462
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564247"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Usar campos de devolución de llamada en un control de selector de fecha y hora

Además de los caracteres de formato estándar que definen los campos del selector de fecha y hora, puede personalizar la salida mediante la especificación de determinadas partes de una cadena de formato personalizado como campos de devolución de llamada. Para declarar un campo de devolución de llamada, incluya uno o varios caracteres "X" (código ASCII 88) en cualquier lugar en el cuerpo de la cadena de formato. Por ejemplo, la siguiente cadena "' hoy en día es: 'yy' / 'MM' / 'dd' (día 'X')'" hace que el control de selector de fecha y hora mostrar el valor actual como el año seguido del mes, fecha y, por último, el día del año.

> [!NOTE]
>  El número de x en una devolución de llamada campo no se corresponde con el número de caracteres que se mostrará.

Se puede distinguir entre varios campos de devolución de llamada en una cadena personalizada repitiendo el carácter "X". Por lo tanto, la cadena de formato "XXddddMMMdd', ' yyyXXX" contiene dos campos de devolución de llamada única, "XX" y "XXX".

> [!NOTE]
>  Campos de devolución de llamada se tratan como campos válidos, por lo que su aplicación debe estar preparada para controlar los mensajes de notificación DTN_WMKEYDOWN.

Implementación de los campos de devolución de llamada en el control de selector de fecha y hora consta de tres partes:

- Inicializando la cadena de formato personalizado

- Control DTN_FORMATQUERY (notificación)

- Controlar DTN_FORMAT (notificación)

## <a name="initializing-the-custom-format-string"></a>Inicializando la cadena de formato personalizado

Inicialice la cadena personalizada con una llamada a `CDateTimeCtrl::SetFormat`. Para obtener más información, consulte [utilizando cadenas de formato personalizado en un Control Selector de hora de fecha y](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Es un lugar común para establecer la cadena de formato personalizado en el `OnInitDialog` función de su clase contenedora del cuadro de diálogo o `OnInitialUpdate` función de su clase contenedora de la vista.

## <a name="handling-the-dtnformatquery-notification"></a>Control DTN_FORMATQUERY (notificación)

Cuando el control analiza la cadena de formato y encuentra un campo de devolución de llamada, la aplicación envía mensajes de notificación DTN_FORMAT y DTN_FORMATQUERY. La cadena del campo de devolución de llamada se incluye con las notificaciones para que pueda determinar qué campo de devolución de llamada se está consultando.

DTN_FORMATQUERY (notificación) se envía para recuperar el tamaño máximo permitido de píxeles de la cadena que se mostrará en el campo de devolución de llamada actual.

Para calcular este valor correctamente, debe calcular el alto y ancho de la cadena, que se sustituirá para el campo, utilizando la fuente del control para mostrar. El cálculo real de la cadena se consigue fácilmente con una llamada a la [función GetTextExtentPoint32](/windows/desktop/api/wingdi/nf-wingdi-gettextextentpoint32a) función de Win32. Una vez que se determina el tamaño, pase el valor a la aplicación y salga de la función de controlador.

El ejemplo siguiente es un método para proporcionar el tamaño de la cadena de devolución de llamada:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Una vez que se ha calculado el tamaño del campo de devolución de llamada actual, debe proporcionar un valor para el campo. Esto se realiza en el controlador para DTN_FORMAT (notificación).

## <a name="handling-the-dtnformat-notification"></a>Controlar DTN_FORMAT (notificación)

DTN_FORMAT (notificación) sirve para solicitar la cadena de caracteres que será sustituida por la aplicación. El ejemplo siguiente muestra un posible método:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  El puntero a la **NMDATETIMEFORMAT** estructura se encuentra al convertir el primer parámetro del controlador de notificación al tipo apropiado.

## <a name="see-also"></a>Vea también

[Uso de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

