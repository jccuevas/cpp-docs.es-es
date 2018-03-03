---
title: "Usar campos de devolución de llamada en un selector de hora y fecha Control | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e5526b0f8826a91eb0b1c5a6eae250abbb02fcf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Usar campos de devolución de llamada en un control de selector de fecha y hora
Además de los caracteres de formato estándar que definen los campos del selector de fecha y hora, puede personalizar la salida mediante la especificación de determinadas partes de una cadena de formato personalizado como campos de devolución de llamada. Para declarar un campo de devolución de llamada, incluya uno o varios caracteres "X" (código ASCII 88) en cualquier lugar en el cuerpo de la cadena de formato. Por ejemplo, la siguiente cadena "' hoy en día es: 'yy' / 'MM' / 'dd' (día 'X')'" hace que el control de selector de fecha y hora mostrar el valor actual como año seguido del mes, fecha y, finalmente, el día del año.  
  
> [!NOTE]
>  El número de x en una devolución de llamada campo no se corresponde con el número de caracteres que se mostrará.  
  
 Puede distinguir entre varios campos de devolución de llamada en una cadena personalizada repitiendo el carácter "X". Por lo tanto, la cadena de formato "XXddddMMMdd', ' yyyXXX" contiene dos campos de devolución de llamada único, "XX" y "XXX".  
  
> [!NOTE]
>  Campos de devolución de llamada se tratan como campos válidos, por lo que su aplicación debe estar preparada para controlar **DTN_WMKEYDOWN** mensajes de notificación.  
  
 Implementación de campos de devolución de llamada en el control de selector de fecha y hora consta de tres partes:  
  
-   Inicializando la cadena de formato personalizado  
  
-   Control de la **DTN_FORMATQUERY** notificación  
  
-   Control de la **DTN_FORMAT** notificación  
  
## <a name="initializing-the-custom-format-string"></a>Inicializando la cadena de formato personalizado  
 Inicialice la cadena personalizada con una llamada a `CDateTimeCtrl::SetFormat`. Para obtener más información, consulte [utilizando cadenas de formato personalizado en un Control Date and Time selector](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Es un lugar común para definir la cadena de formato personalizado en el `OnInitDialog` función de la clase de cuadro de diálogo contenedora o `OnInitialUpdate` función de la clase contenedora de la vista.  
  
## <a name="handling-the-dtnformatquery-notification"></a>Controlar la notificación DTN_FORMATQUERY  
 Cuando el control analiza la cadena de formato y encuentra un campo de devolución de llamada, la aplicación envía **DTN_FORMAT** y **DTN_FORMATQUERY** mensajes de notificación. La cadena del campo de devolución de llamada se incluye con las notificaciones para que pueda determinar qué campo de devolución de llamada que se va a consultar.  
  
 El **DTN_FORMATQUERY** notificación se envía para recuperar el tamaño máximo permitido en píxeles de la cadena que se mostrará en el campo de devolución de llamada actual.  
  
 Para calcular este valor correctamente, debe calcular el alto y ancho de la cadena, que se sustituirá para el campo, utilice la fuente de presentación del control. El cálculo real de la cadena se consigue fácilmente con una llamada a la [función GetTextExtentPoint32](http://msdn.microsoft.com/library/windows/desktop/dd144938) función de Win32. Una vez que se determina el tamaño, pase el valor a la aplicación y salga de la función de controlador.  
  
 El ejemplo siguiente es un método para proporcionar el tamaño de la cadena de devolución de llamada:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]  
  
 Una vez que se ha calculado el tamaño del campo de devolución de llamada actual, debe proporcionar un valor para el campo. Esto se hace en el controlador para el **DTN_FORMAT** notificación.  
  
## <a name="handling-the-dtnformat-notification"></a>Controlar DTN_FORMAT (notificación)  
 El **DTN_FORMAT** notificación se usa la aplicación para solicitar la cadena de caracteres que se sustituirá. En el ejemplo siguiente se muestra un método posible:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]  
  
> [!NOTE]
>  El puntero a la **NMDATETIMEFORMAT** estructura se encuentra al convertir el primer parámetro del controlador de notificación al tipo apropiado.  
  
## <a name="see-also"></a>Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)

