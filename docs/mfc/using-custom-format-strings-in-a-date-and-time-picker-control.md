---
title: Usar cadenas de formato personalizado en un selector de hora y fecha Control | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bfaad06571a8648db24497c46d55cb2eb1ce2157
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Usar cadenas de formato personalizado en un control de selector de fecha y hora
De forma predeterminada, los controles de selector de fecha y hora proporcionan que tres dar formato a tipos (cada formato corresponde a un estilo único) para mostrar la fecha y hora actuales:  
  
-   **DTS_LONGDATEFORMAT** muestra la fecha en formato largo, produciendo resultados como "Miércoles, 3 de enero de 2000".  
  
-   **DTS_SHORTDATEFORMAT** muestra la fecha en formato corto, produciendo resultados como "1/3/00".  
  
-   **DTS_TIMEFORMAT** muestra la hora en formato largo, produciendo resultados como "5:31:42 P.M.".  
  
 Sin embargo, puede personalizar la apariencia de la fecha u hora utilizando una cadena de formato personalizado. La cadena personalizada se compone de los caracteres de formato existente, caracteres sin formato o una combinación de ambos. Una vez generada la cadena personalizada, realice una llamada a [CDateTimeCtrl:: SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) pasando la cadena personalizada. El control de selector de fecha y hora, a continuación, mostrará el valor actual utilizando la cadena de formato personalizado.  
  
 El código de ejemplo siguiente (donde `m_dtPicker` es la `CDateTimeCtrl` objeto) se muestra una posible solución:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 Además de las cadenas de formato personalizado, selector de fecha y hora también controles admiten [campos de devolución de llamada](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Controles](../mfc/controls-mfc.md)

