---
title: MSG (Structure1) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe629c2f279b6b258f4824229490f7b72b4ce4d
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338817"
---
# <a name="msg-structure1"></a>MSG (Structure1)
El `MSG` estructura contiene información del mensaje de cola de mensajes de un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagMSG {     // msg    
    HWND hwnd;  
    UINT message;  
    WPARAM wParam;  
    LPARAM lParam;  
    DWORD time;  
    POINT pt;  
} MSG;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *HWND*  
 Identifica la ventana cuyo procedimiento de ventana recibe el mensaje.  
  
 *message*  
 Especifica el número de mensaje.  
  
 *wParam*  
 Especifica información adicional sobre el mensaje. El significado exacto depende del valor de la `message` miembro.  
  
 *lParam*  
 Especifica información adicional sobre el mensaje. El significado exacto depende del valor de la `message` miembro.  
  
 *time*  
 Especifica la hora a la que se expuso el mensaje.  
  
 *PT*  
 Especifica la posición del cursor, en coordenadas de pantalla, cuando se expuso el mensaje.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

