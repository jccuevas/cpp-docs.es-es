---
title: FILETIME (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- FILETIME
dev_langs:
- C++
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0d1128442300d3f6fc153733be8b23b9d69444d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375887"
---
# <a name="filetime-structure"></a>FILETIME (Estructura)
El `FILETIME` estructura es un valor de 64 bits que representa el número de intervalos de 100 nanosegundos desde el 1 de enero de 1601.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _FILETIME {  
    DWORD dwLowDateTime;   /* low 32 bits */  
    DWORD dwHighDateTime;  /* high 32 bits */  
} FILETIME, *PFILETIME, *LPFILETIME;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwLowDateTime*  
 Especifica el valor bajo de 32 bits de la hora de archivo.  
  
 *FILETIME*  
 Especifica el valor alto de 32 bits de la hora de archivo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** windef.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime:: CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

