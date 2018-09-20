---
title: Usar cadenas de formato personalizado en una fecha y hora selector Control | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8dcfe39a3054d998cf5116ef125a3791d8c4a47
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405052"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Usar cadenas de formato personalizado en un control de selector de fecha y hora

De forma predeterminada, los controles de selector de fecha y hora proporcionan que tres tipos (cada formato corresponde a un estilo único) de formato para mostrar la fecha y hora actuales:

- **DTS_LONGDATEFORMAT** muestra la fecha en formato largo, produciendo resultados como "Miércoles, 3 de enero de 2000".

- **DTS_SHORTDATEFORMAT** muestra la fecha en formato corto, produciendo resultados como "1/3/00".

- **DTS_TIMEFORMAT** muestra la hora en formato largo, produciendo resultados como "5:31:42 P.M.".

Sin embargo, puede personalizar la apariencia de la fecha u hora mediante una cadena de formato personalizado. La cadena personalizada está formada por caracteres de formato existente, caracteres sin formato o una combinación de ambos. Una vez compilada la cadena personalizada, realice una llamada a [CDateTimeCtrl:: SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) pasando la cadena personalizada. El control de selector de fecha y hora, a continuación, mostrará el valor actual utilizando la cadena de formato personalizado.

Ejemplo de código siguiente (donde *m_dtPicker* es la `CDateTimeCtrl` objeto) se muestra una posible solución:

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

Además de las cadenas de formato personalizado de selector de fecha y hora también controles admiten [campos de devolución de llamada](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

## <a name="see-also"></a>Vea también

[Uso de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

