---
title: SYSTEMTIME estructura-1 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 07af222a3d51ff1cc71076d5bbcc3513a3d6cad4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

