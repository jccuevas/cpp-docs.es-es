---
title: SYSTEMTIME estructura-1 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97a0042adaa223fc5898c057f191f7b750fa230f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="systemtime-structure1"></a>SYSTEMTIME estructura-1
El `SYSTEMTIME` estructura representa una fecha y hora con miembros individuales para el mes, día, año, día de la semana, hora, minuto, segundo y milisegundo.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 *wYear*  
 El año actual.  
  
 *wMonth*  
 El mes en curso; Enero es 1.  
  
 *wDayOfWeek*  
 El día actual de la semana; El domingo es 0, el lunes es 1 y así sucesivamente.  
  
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
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime:: CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

