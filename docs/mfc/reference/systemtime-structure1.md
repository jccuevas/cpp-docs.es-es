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
- SYSTEMTIME structure
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 298b2673a3eb05525683f8269fcd415d5be1c80a
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
 El mes actual; Enero es 1.  
  
 *wDayOfWeek*  
 El día de la semana; El domingo es 0, el lunes es 1 y así sucesivamente.  
  
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
 [!code-cpp[NVC_MFC_Utilities&#39;](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime:: CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)


