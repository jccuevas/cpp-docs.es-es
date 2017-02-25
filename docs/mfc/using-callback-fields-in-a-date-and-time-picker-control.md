---
title: "Usar campos de devoluci&#243;n de llamada en un control de selector de fecha y hora | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTN_FORMATQUERY"
  - "DTN_FORMAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "campos de devolución de llamada de clase CDateTimeCtrl"
  - "CDateTimeCtrl (clase), campos de devolución de llamada"
  - "CDateTimeCtrl (clase), controlar DTN_FORMAT y DTN_FORMATQ"
  - "DateTimePicker (control) [MFC]"
  - "DateTimePicker (control) [MFC], campos de devolución de llamada"
  - "DTN_FORMAT (notificación)"
  - "DTN_FORMATQUERY (notificación)"
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Usar campos de devoluci&#243;n de llamada en un control de selector de fecha y hora
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Además de los caracteres de formato estándar que definen los campos de selector de fecha y hora, puede personalizar la salida especificando determinadas partes de una cadena de formato personalizado como campos de devolución de llamada.  Para declarar un campo de devolución de llamada, incluya uno o más caracteres “X” \(código ASCII 88\) en cualquier parte del cuerpo de la cadena de formato.  Por ejemplo, la siguiente cadena ““Today is: “\/“de” yy\/“MM DD” \(Day “X "\)” “hace que el control de selector de fecha y hora para mostrar el valor actual como el año seguido del mes, fecha y, finalmente el día del año.  
  
> [!NOTE]
>  El número de X en un campo de devolución de llamada no corresponde al número de caracteres que se mostrará.  
  
 Puede distinguir entre varios campos de devolución de llamada en una cadena personalizada repitiendo el carácter “X”.  Así, la cadena de formato “XXddddMMMdd, 'yyyXXX” contiene dos campos únicos de devolución de llamada, “XX” y “XXX”.  
  
> [!NOTE]
>  Los campos de devolución de llamada se tratan como campos válidos, por lo que la aplicación se debe preparar para controlar los mensajes de notificación de **DTN\_WMKEYDOWN** .  
  
 Implementar campos de devolución de llamada en el control selector de fecha y hora consta de tres partes:  
  
-   Inicializar la cadena de formato personalizado  
  
-   Administrar la notificación de **DTN\_FORMATQUERY**  
  
-   Administrar la notificación de **DTN\_FORMAT**  
  
## Inicializar la cadena de formato personalizado  
 Inicializa la cadena personalizada con una llamada a `CDateTimeCtrl::SetFormat`.  Para obtener más información, vea [Usar cadenas de formato personalizadas en un Control del selector de fecha y hora](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md).  Un lugar común para definir la cadena de formato personalizado es la función de `OnInitDialog` de la clase de diálogo o la función de `OnInitialUpdate` que contiene de la clase de vista que contiene.  
  
## Administrar la notificación de DTN\_FORMATQUERY  
 Cuando el control analiza la cadena de formato y encuentra un campo de devolución de llamada, la aplicación envía los mensajes de notificación de **DTN\_FORMAT** y de **DTN\_FORMATQUERY** .  La cadena del campo de devolución de llamada se incluye con las notificaciones para que pueda determinar que el campo de devolución de llamada se está consultando.  
  
 La notificación de **DTN\_FORMATQUERY** se envía para recuperar el tamaño máximo permitido en píxeles de la cadena que se mostrará en el campo actual de devolución de llamada.  
  
 Para calcular correctamente este valor, debe calcular el alto y el ancho de la cadena, se sustituirá para el campo, con la fuente de presentación del control.  El cálculo real de la cadena con facilidad se logra con una llamada a la función de [GetTextExtentPoint32](http://msdn.microsoft.com/library/windows/desktop/dd144938) Win32.  Una vez que se determina el tamaño, devuelva el valor a la aplicación y salga de la función controladora.  
  
 El ejemplo siguiente es un método de proporcionar el tamaño de la cadena de devolución de llamada:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/CPP/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]  
  
 El tamaño del campo actual de devolución de llamada se ha calculado una vez, debe proporcionar un valor para el campo.  Esto se hace en el controlador para la notificación de **DTN\_FORMAT** .  
  
## Administrar la notificación de DTN\_FORMAT  
 La notificación de **DTN\_FORMAT** es utilizada por la aplicación para solicitar la cadena de caracteres que se sustituido.  El ejemplo siguiente muestra un método posible:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/CPP/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]  
  
> [!NOTE]
>  El puntero a la estructura de **NMDATETIMEFORMAT** se con lo que el primer parámetro del controlador de notificación al tipo adecuado.  
  
## Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)