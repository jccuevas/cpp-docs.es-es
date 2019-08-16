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
ms.openlocfilehash: 5d08c349253e62c15553cfa0452cee930b1a1876
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513509"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Usar campos de devolución de llamada en un control de selector de fecha y hora

Además de los caracteres de formato estándar que definen los campos de selector de fecha y hora, puede personalizar la salida especificando ciertas partes de una cadena de formato personalizado como campos de devolución de llamada. Para declarar un campo de devolución de llamada, incluya uno o más caracteres "X" (código ASCII 88) en cualquier lugar del cuerpo de la cadena de formato. Por ejemplo, la siguiente cadena "' es: ' YY '/' MM '/' dd ' (día ' X ') '" hace que el control de selector de fecha y hora muestre el valor actual como el año seguido del mes, la fecha y, por último, el día del año.

> [!NOTE]
>  El número de X de un campo de devolución de llamada no se corresponde con el número de caracteres que se mostrarán.

Puede distinguir entre varios campos de devolución de llamada en una cadena personalizada repitiendo el carácter "X". Por lo tanto, la cadena de formato "XXddddMMMdd", "yyyXXX" contiene dos campos de devolución de llamada únicos: "XX" y "XXX".

> [!NOTE]
>  Los campos de devolución de llamada se tratan como campos válidos, por lo que la aplicación debe estar preparada para controlar los mensajes de notificación de DTN_WMKEYDOWN.

La implementación de campos de devolución de llamada en el control de selector de fecha y hora consta de tres partes:

- Inicializar la cadena de formato personalizado

- Controlar la notificación de DTN_FORMATQUERY

- Controlar la notificación de DTN_FORMAT

## <a name="initializing-the-custom-format-string"></a>Inicializar la cadena de formato personalizado

Inicialice la cadena personalizada con una llamada a `CDateTimeCtrl::SetFormat`. Para obtener más información, vea [usar cadenas de formato personalizado en un control de selector de fecha y hora](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Un lugar común para establecer la cadena de formato personalizado es la `OnInitDialog` función de la clase de cuadro de `OnInitialUpdate` diálogo contenedora o función de la clase de vista contenedora.

## <a name="handling-the-dtn_formatquery-notification"></a>Controlar la notificación de DTN_FORMATQUERY

Cuando el control analiza la cadena de formato y encuentra un campo de devolución de llamada, la aplicación envía mensajes de notificación DTN_FORMAT y DTN_FORMATQUERY. La cadena de campo de devolución de llamada se incluye con las notificaciones para que pueda determinar qué campo de devolución de llamada se está consultando.

La notificación DTN_FORMATQUERY se envía para recuperar el tamaño máximo permitido en píxeles de la cadena que se mostrará en el campo de devolución de llamada actual.

Para calcular este valor correctamente, debe calcular el alto y el ancho de la cadena, que se sustituirá por el campo con la fuente de presentación del control. El cálculo real de la cadena se consigue fácilmente con una llamada a la función [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) de Win32. Una vez determinado el tamaño, vuelva a pasar el valor a la aplicación y salga de la función de controlador.

El ejemplo siguiente es un método para proporcionar el tamaño de la cadena de devolución de llamada:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Una vez que se ha calculado el tamaño del campo de devolución de llamada actual, debe proporcionar un valor para el campo. Esto se hace en el controlador de la notificación DTN_FORMAT.

## <a name="handling-the-dtn_format-notification"></a>Controlar la notificación de DTN_FORMAT

La aplicación usa la notificación DTN_FORMAT para solicitar la cadena de caracteres que se va a sustituir. En el ejemplo siguiente se muestra un método posible:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  El puntero a la estructura **NMDATETIMEFORMAT** se encuentra convirtiendo el primer parámetro del controlador de notificación en el tipo adecuado.

## <a name="see-also"></a>Vea también

[Uso de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
