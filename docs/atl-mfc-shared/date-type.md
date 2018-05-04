---
title: DATE (tipo) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DATE
dev_langs:
- C++
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aafed046fa5724442e30014aa5634542de0f4aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="date-type"></a>DATE (tipo)
El **fecha** tipo se implementa mediante un número de punto flotante de 8 bytes. Los días se representan mediante incrementos de números enteros, comenzando por el 30 de diciembre de 1899, medianoche como hora cero. Los valores de hora se expresan como el valor absoluto de la parte fraccionaria del número. En la tabla siguiente se muestra varias fechas junto con sus **fecha** equivalente numérico del tipo:  
  
|Fecha y hora|Representación en forma de|  
|-------------------|--------------------|  
|30 de diciembre de 1899, medianoche|0.00|  
|1 de enero de 1900, medianoche|2.00|  
|4 de enero de 1900, medianoche|5.00|  
|4 de enero de 1900, 6 A.M.|5.25|  
|4 de enero de 1900, mediodía|5.50|  
|4 de enero de 1900, 9 P.M.|5.875|  
  
 El **fecha** fecha tipo, así como el `COleDateTime` clase representa fechas y horas como una línea numérica clásica. La `COleDateTime` clase contiene varios métodos para manipular los valores de fecha, incluida la conversión a y desde otros formatos de fecha habituales.  
  
 Cuando se trabaja con los siguientes formatos de fecha y hora en la automatización, deben tener en cuenta los siguientes puntos:  
  
-   Las fechas se especifican en hora local; sincronización debe realizarse manualmente cuando se trabaja con fechas en zonas horarias diferentes.  
  
-   Los tipos de fecha no tiene en cuenta al horario de verano.  
  
-   La escala de tiempo de fecha se convierte en discontinuo para valores de fecha menor que 0 (antes del 30 de diciembre de 1899). Esto es porque la parte de número entero del valor de fecha se trata como iniciado, mientras que la parte fraccionaria se trata como valores sin signo. En otras palabras, la parte de número entero del valor date puede ser positivo o negativo, mientras que la parte fraccionaria del valor de fecha siempre se agrega a la fecha lógica global. En la tabla siguiente se muestra algunos ejemplos:  
  
|Fecha y hora|Representación en forma de|  
|-------------------|--------------------|  
|27 de diciembre de 1899, medianoche|-3.00|  
|28 de diciembre de 1899, mediodía|-2.50|  
|28 de diciembre de 1899, medianoche|-2.00|  
|29 de diciembre de 1899, medianoche|-1.00|  
|30 de diciembre de 1899, 6 P.M.|-0.75|  
|30 de diciembre de 1899, mediodía|-0.50|  
|30 de diciembre de 1899, 6 A.M.|-0.25|  
|30 de diciembre de 1899, medianoche|0.00|  
|30 de diciembre de 1899, 6 A.M.|0.25|  
|30 de diciembre de 1899, mediodía|0.50|  
|30 de diciembre de 1899, 6 P.M.|0.75|  
|31 de diciembre de 1899, medianoche|1.00|  
|1 de enero de 1900, medianoche|2.00|  
|1 de enero de 1900, mediodía|2.50|  
|2 de enero de 1900, medianoche|3.00|  
  
> [!CAUTION]
>  Tenga en cuenta que, debido a 6:00 A.M. siempre se representa mediante un valor fraccionario 0,25 independientemente de si el entero que representa el día es positivo (después del 30 de diciembre de 1899) o negativo (antes del 30 de diciembre de 1899), una simple comparación de punto flotante erróneamente ordenar cualquier **fecha** que representa 6:00 A.M. en un día anterior a 12/30/1899 como *más adelante* a una **fecha** que representa 7:00 A.M. en ese mismo día.  
  
 Más información sobre los problemas relacionados con el **fecha** y `COleDateTime` tipos pueden encontrarse en [clase COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) y [fecha y hora: compatibilidad de automatización de](../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="see-also"></a>Vea también  
 [Fecha y hora](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime (clase)](../atl-mfc-shared/reference/coledatetime-class.md)

