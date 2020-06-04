---
title: Usar cadenas de formato personalizado en un control de selector de fecha y hora
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 8da5ecaf473d6d3c35ddc1b95ac856ce8c12f163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411635"
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
