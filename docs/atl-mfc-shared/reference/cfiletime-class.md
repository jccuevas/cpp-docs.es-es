---
title: "CFileTime Class | Microsoft Docs"
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
  - "ATL::CFileTime"
  - "CFileTime"
  - "ATL.CFileTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileTime class"
  - "shared classes, CFileTime"
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
caps.latest.revision: 18
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFileTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para administrar los valores de fecha y hora asociados a un archivo.  
  
## Sintaxis  
  
```  
  
   class CFileTime :   
public FILETIME  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTime::CFileTime](../Topic/CFileTime::CFileTime.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTime::GetCurrentTime](../Topic/CFileTime::GetCurrentTime.md)|Llame a esta función estática para recuperar un objeto de `CFileTime` que representa la fecha del sistema y la hora actuales.|  
|[CFileTime::GetTime](../Topic/CFileTime::GetTime.md)|Llame a este método para recuperar el tiempo del objeto de `CFileTime` .|  
|[CFileTime::LocalToUTC](../Topic/CFileTime::LocalToUTC.md)|Llame a este método para convertir una hora local del archivo a un tiempo de archivo según la hora universal coordinada \(UTC\) \(UTC\).|  
|[CFileTime::SetTime](../Topic/CFileTime::SetTime.md)|Llame a este método para establecer la fecha y hora almacenada por el objeto de `CFileTime` .|  
|[CFileTime::UTCToLocal](../Topic/CFileTime::UTCToLocal.md)|Llame a este método para convertir el tiempo según la hora universal coordinada \(UTC\) en la hora local del archivo.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTime::operator \-](../Topic/CFileTime::operator%20-.md)|Utilizan este operador para realizar la resta en un objeto de `CFileTime` o de `CFileTimeSpan` .|  
|[CFileTime::operator \!\=](../Topic/CFileTime::operator%20!=.md)|este operador compara dos objetos de `CFileTime` para la desigualdad.|  
|[CFileTime::operator \+](../Topic/CFileTime::operator%20+.md)|Utilizan este operador para realizar la adición de un objeto de `CFileTimeSpan` .|  
|[CFileTime::operator \+\=](../Topic/CFileTime::operator%20+=.md)|Utilizan este operador para realizar la adición de un objeto de `CFileTimeSpan` y asignar el resultado al objeto actual.|  
|[CFileTime::operator \<](../Topic/CFileTime::operator%20%3C.md)|este operador compara dos objetos de `CFileTime` para determinar menos.|  
|[CFileTime::operator \<\=](../Topic/CFileTime::operator%20%3C=.md)|Este operador compara dos objetos de `CFileTime` para determinar la igualdad o menos.|  
|[CFileTime::operator \=](../Topic/CFileTime::operator%20=.md)|el operador de asignación.|  
|[CFileTime::operator \-\=](../Topic/CFileTime::operator%20-=.md)|Utilizan este operador para realizar la resta en un objeto de `CFileTimeSpan` y asignar el resultado al objeto actual.|  
|[CFileTime::operator \=\=](../Topic/CFileTime::operator%20==.md)|Este operador compara dos objetos de `CFileTime` para comprobar la igualdad.|  
|[CFileTime::operator \>](../Topic/CFileTime::operator%20%3E.md)|Este operador compara dos objetos de `CFileTime` para determinar el mayor.|  
|[CFileTime::operator \>\=](../Topic/CFileTime::operator%20%3E=.md)|Este operador compara dos objetos de `CFileTime` para determinar la igualdad o el mayor.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileTime::Day](../Topic/CFileTime::Day.md)|Un miembro de datos estático que almacena el número de 100 intervalos de nanosegundo que constituyen un día.|  
|[CFileTime::Hour](../Topic/CFileTime::Hour.md)|Un miembro de datos estático que almacena el número de 100 intervalos de nanosegundo que constituyen una hora.|  
|[CFileTime::Millisecond](../Topic/CFileTime::Millisecond.md)|Un miembro de datos estático que almacena el número de 100 intervalos de nanosegundo que constituyen un milisegundo.|  
|[CFileTime::Minute](../Topic/CFileTime::Minute.md)|Un miembro de datos estático que almacena el número de 100 intervalos de nanosegundo que constituyen un minuto.|  
|[CFileTime::Second](../Topic/CFileTime::Second.md)|Un miembro de datos estático que almacena el número de 100 intervalos de nanosegundo que constituyen un segundo.|  
|[CFileTime::Week](../Topic/CFileTime::Week.md)|Un miembro de datos estático que almacena el número de 100 intervalos de nanosegundo que constituyen una semana.|  
  
## Comentarios  
 Esta clase proporciona métodos para administrar los valores de fecha y hora asociados a la creación, el acceso y la modificación de archivos.  Los métodos y los datos de esta clase se utilizan con frecuencia junto con los objetos de `CFileTimeSpan` , que se encargan de valores de hora relativos.  
  
 Se almacena el valor de fecha y hora como un valor de 64 bits que representa el número de 100 intervalos de nanosegundo desde el 1 de enero de 1601.  Éste es el formato de la hora universal coordinada \(UTC\).  
  
 Proporcionan las variables miembro estáticas siguientes const para simplificar cálculos:  
  
|Variable miembro|Número de 100 intervalos de nanosegundo|  
|----------------------|---------------------------------------------|  
|Millisecond|10,000|  
|Segundo|Milisegundos \* 1.000|  
|Minuto|En segundo lugar \* 60|  
|Hora|Minuto \* 60|  
|Día|Hora \* 24|  
|Semana|Día \* 7|  
  
 **Note** No todos los sistemas de archivos puede creación de registro y la última hora de acceso y no todos los sistemas de archivos registrarlos de la misma manera.  Por ejemplo, en el sistema de archivos FAT de Windows NT, la hora de creación tiene una resolución de 10 milisegundos, el tiempo de escritura tiene una resolución de 2 segundos, y tiempo de acceso tiene una resolución de 1 día \(fecha de acceso\).  En NTFS, tiempo de acceso tiene una resolución de 1 hora.  Además, tiempos de registros FAT en el disco de la hora local, pero de registros de NTFS en el disco en hora UTC.  Para obtener más información, vea [Tiempos de archivo](http://msdn.microsoft.com/library/windows/desktop/ms724290).  
  
## Jerarquía de herencia  
 `FILETIME`  
  
 `CFileTime`  
  
## Requisitos  
 **encabezado:** atltime.h  
  
## Vea también  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTimeSpan Class](../../atl-mfc-shared/reference/cfiletimespan-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)