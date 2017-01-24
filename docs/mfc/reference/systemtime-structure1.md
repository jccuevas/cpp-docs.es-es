---
title: "SYSTEMTIME (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SYSTEMTIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SYSTEMTIME (estructura)"
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SYSTEMTIME (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura `SYSTEMTIME` representa una fecha y hora mediante miembros individuales para el mes, día, año, día de la semana, hora, minuto, segundo y milisegundo.  
  
## Sintaxis  
  
```  
  
      typedef struct _SYSTEMTIME {  
   WORD wYear;  
   WORD wMonth;  
   WORD wDayOfWeek;  
   WORD wDay;  
   WORD wHour;  
   WORD wMinute;  
   WORD wSecond;  
   WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### Parámetros  
 *wYear*  
 El año actual.  
  
 *wMonth*  
 El mes actual; enero es 1.  
  
 *wDayOfWeek*  
 El día actual de la semana; el domingo es 0, el lunes es 1, etc.  
  
 *wDay*  
 El día actual del mes.  
  
 *wHour*  
 La hora actual.  
  
 *wMinute*  
 El minuto actual.  
  
 *wSecond*  
 El segundo actual.  
  
 *wMilliseconds*  
 El milisegundo actual.  
  
## Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/CPP/systemtime-structure1_1.cpp)]  
  
## Requisitos  
 **Encabezado:** winbase.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../Topic/CTime::CTime.md)