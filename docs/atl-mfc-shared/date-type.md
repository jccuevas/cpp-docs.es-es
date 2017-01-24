---
title: "DATE Type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Date (tipo de datos)"
  - "Date (tipo de datos), about Date data type"
  - "Date (tipo de datos), implementar"
  - "DATE type"
  - "hour values representation"
  - "MFC, fecha y hora"
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DATE Type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Implementan el tipo **fecha** mediante un número de punto flotante de 8 bytes.  Los días se representan mediante incrementos del número entero que comienzan con el 30 de diciembre de 1899, medianoche como tiempo cero.  Los valores de hora se expresan como el valor absoluto de la parte fraccionaria del número.  La tabla siguiente se muestran varias fechas junto con su equivalente numérico tipo **fecha** :  
  
|Fecha y hora|Representación|  
|------------------|--------------------|  
|30 de diciembre de 1899, Medianoche|0.00|  
|1 de enero de 1900, Medianoche|2.00|  
|4 de enero de 1900, Medianoche|5.00|  
|4 de enero de 1900, 6..|5.25|  
|4 de enero de 1900, Mediodía|5.50|  
|4 de enero de 1900, 9 P.M...|5.875|  
  
 El tipo de la fecha **fecha** , así como la clase `COleDateTime` , representa las fechas y horas como línea de número clásica.  La clase `COleDateTime` contiene varios métodos para manipular valores de fecha, incluida la conversión a y desde otros formatos de fecha comunes.  
  
 Los puntos siguientes deben ser indicados al trabajar con estos formatos de fecha y hora de automatización:  
  
-   Las fechas se especifican en hora local; la sincronización debe realizar manualmente al trabajar con fechas en zonas horarias diferentes.  
  
-   Los tipos de fecha no explican el horario de verano.  
  
-   La escala de tiempo de fecha se discontinua por valores de fecha menos de 0 \(antes del 30 de diciembre de 1899\).  Esto es porque se tratan como la parte del número entero del valor de fecha como un valor con signo, mientras que tratan a la fracción como sin signo.  Es decir la parte del número entero de valor de fecha puede ser positivo o negativo, mientras que se agregan a la fracción del valor de fecha siempre a la fecha lógica total.  La tabla siguiente se muestran algunos ejemplos:  
  
|Fecha y hora|Representación|  
|------------------|--------------------|  
|27 de diciembre de 1899, Medianoche|\-3.00|  
|28 de diciembre de 1899, Mediodía|\-2.50|  
|28 de diciembre de 1899, Medianoche|\-2.00|  
|29 de diciembre de 1899, Medianoche|\-1.00|  
|30 de diciembre de 1899, 6 De la tarde..|\-0.75|  
|30 de diciembre de 1899, Mediodía|\-0.50|  
|30 de diciembre de 1899, 6..|\-0.25|  
|30 de diciembre de 1899, Medianoche|0.00|  
|30 de diciembre de 1899, 6..|0.25|  
|30 de diciembre de 1899, Mediodía|0.50|  
|30 de diciembre de 1899, 6 De la tarde..|0.75|  
|31 de diciembre de 1899, Medianoche|1.00|  
|1 de enero de 1900, Medianoche|2.00|  
|1 de enero de 1900, Mediodía|2.50|  
|2 de enero de 1900, Medianoche|3.00|  
  
> [!CAUTION]
>  Dado que el 6:00 se representa siempre por un valor fraccionario 0,25 independientemente de si el entero que representa el día es positivo que \(después del 30 de diciembre de 1899\) o negativo \(antes del 30 de diciembre de 1899\), una comparación simple de punto flotante clasificaría erróneamente cualquier **fecha** que representa las 6:00 en un día anterior de 12\/30\/1899 como *más adelante* que **fecha** que representa las 7:00 en ese mismo día.  
  
 Más información sobre los problemas relacionados con los tipos **fecha** y `COleDateTime` se puede encontrar en [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md) y [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md).  
  
## Vea también  
 [Date and Time](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md)