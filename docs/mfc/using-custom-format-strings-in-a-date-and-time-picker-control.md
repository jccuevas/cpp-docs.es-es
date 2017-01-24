---
title: "Usar cadenas de formato personalizado en un control de selector de fecha y hora | Microsoft Docs"
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
  - "CDateTimeCtrl (clase), estilos de presentación"
  - "DateTimePicker (control) [MFC]"
  - "DateTimePicker (control) [MFC], estilos de presentación"
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar cadenas de formato personalizado en un control de selector de fecha y hora
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, los controles de selector de fecha y hora proporcionan tres tipos de formato \(cada formato correspondiente a un estilo único\) para mostrar la fecha u hora actuales:  
  
-   **DTS\_LONGDATEFORMAT** muestra la fecha en formato largo, generar generó como “miércoles 3 de enero de 2000”.  
  
-   **DTS\_SHORTDATEFORMAT** muestra la fecha en formato corto, generar generó como “1\/3\/00 ".  
  
-   **DTS\_TIMEFORMAT** muestra la hora en el formato largo, generar generó como “5:31: 42 P.M.”.  
  
 Sin embargo, puede personalizar la apariencia de la fecha o la hora mediante una cadena de formato personalizado.  Esta cadena personalizada se compone de caracteres de formato existentes, caracteres de nonformat, o una combinación de ambos.  Una vez generada la cadena personalizada, haga una llamada a [CDateTimeCtrl::SetFormat](../Topic/CDateTimeCtrl::SetFormat.md) que pasa en la cadena personalizada.  El control selector de fecha y hora a continuación mostrará el valor actual utilizando la cadena de formato personalizado.  
  
 El código de ejemplo siguiente \(donde es el objeto `m_dtPicker` de `CDateTimeCtrl` \) muestra una posible solución:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/CPP/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 Además de las cadenas de formato personalizado, controles también [campos de devolución de llamada](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)admiten el selector de fecha y hora.  
  
## Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)