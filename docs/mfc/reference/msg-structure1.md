---
title: Estructura de mensaje-1 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: b856ea17e4542bee68d55b22069e559592199939
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="msg-structure1"></a>Estructura de mensaje-1
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
  
 `message`  
 Especifica el número de mensaje.  
  
 `wParam`  
 Especifica información adicional sobre el mensaje. El significado exacto depende del valor de la **mensaje** miembro.  
  
 `lParam`  
 Especifica información adicional sobre el mensaje. El significado exacto depende del valor de la **mensaje** miembro.  
  
 `time`  
 Especifica la hora a la que se expuso el mensaje.  
  
 `pt`  
 Especifica la posición del cursor, en coordenadas de pantalla, cuando se expuso el mensaje.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


