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
ms.openlocfilehash: 50350e51b6747d8c010db9d0dcaa9dff2e56e1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366553"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Usar campos de devolución de llamada en un control de selector de fecha y hora

Además de los caracteres de formato estándar que definen los campos de selector de fecha y hora, puede personalizar la salida especificando determinadas partes de una cadena de formato personalizado como campos de devolución de llamada. Para declarar un campo de devolución de llamada, incluya uno o varios caracteres "X" (código ASCII 88) en cualquier parte del cuerpo de la cadena de formato. Por ejemplo, la siguiente cadena "'Today es: 'yy'/'MM'/'dd' (Día 'X')'", hace que el control selector de fecha y hora muestre el valor actual como el año seguido del mes, la fecha y, finalmente, el día del año.

> [!NOTE]
> El número de X en un campo de devolución de llamada no corresponde al número de caracteres que se mostrarán.

Puede distinguir entre varios campos de devolución de llamada en una cadena personalizada repitiendo el carácter "X". Por lo tanto, la cadena de formato "XXddddMMMdd", "yyyXXX" contiene dos campos de devolución de llamada únicos, "XX" y "XXX".

> [!NOTE]
> Los campos de devolución de llamada se tratan como campos válidos, por lo que la aplicación debe estar preparada para controlar DTN_WMKEYDOWN mensajes de notificación.

La implementación de campos de devolución de llamada en el control de selector de fecha y hora consta de tres partes:

- Inicialización de la cadena de formato personalizado

- Manejo de la notificación DTN_FORMATQUERY

- Manejo de la notificación de DTN_FORMAT

## <a name="initializing-the-custom-format-string"></a>Inicialización de la cadena de formato personalizado

Inicializar la cadena personalizada `CDateTimeCtrl::SetFormat`con una llamada a . Para obtener más información, consulte Uso de cadenas de [formato personalizado en un control](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)selector de fecha y hora . Un lugar común para establecer la `OnInitDialog` cadena de formato personalizado `OnInitialUpdate` está en la función de la clase de cuadro de diálogo contenedoro o función de la clase de vista contenedora.

## <a name="handling-the-dtn_formatquery-notification"></a>Manejo de la notificación de DTN_FORMATQUERY

Cuando el control analiza la cadena de formato y encuentra un campo de devolución de llamada, la aplicación envía DTN_FORMAT y DTN_FORMATQUERY mensajes de notificación. La cadena de campo de devolución de llamada se incluye con las notificaciones para que pueda determinar qué campo de devolución de llamada se está consultando.

La notificación DTN_FORMATQUERY se envía para recuperar el tamaño máximo permitido en píxeles de la cadena que se mostrará en el campo de devolución de llamada actual.

Para calcular correctamente este valor, debe calcular el alto y el ancho de la cadena, que se sustituirá por el campo, utilizando la fuente de visualización del control. El cálculo real de la cadena se logra fácilmente con una llamada a la [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) Win32 función. Una vez determinado el tamaño, vuelva a pasar el valor a la aplicación y salga de la función de controlador.

El ejemplo siguiente es un método para proporcionar el tamaño de la cadena de devolución de llamada:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Una vez calculado el tamaño del campo de devolución de llamada actual, debe proporcionar un valor para el campo. Esto se hace en el controlador para la notificación de DTN_FORMAT.

## <a name="handling-the-dtn_format-notification"></a>Manejo de la notificación DTN_FORMAT

La aplicación utiliza la notificación DTN_FORMAT para solicitar la cadena de caracteres que se sustituirá. En el ejemplo siguiente se muestra un método posible:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
> El puntero a la **NMDATETIMEFORMAT** estructura se encuentra mediante la conversión del primer parámetro del controlador de notificaciones al tipo adecuado.

## <a name="see-also"></a>Consulte también

[Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
