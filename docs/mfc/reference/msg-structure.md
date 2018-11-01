---
title: Estructura MSG | Microsoft Docs
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
ms.openlocfilehash: 2b2f58af3bcf3eef524b95d25579e5bc233f9108
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334564"
---
# <a name="msg-structure"></a>MSG (Estructura)

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

*HWND*<br/>
Identifica la ventana cuyo procedimiento de ventana recibe el mensaje.

*message*<br/>
Especifica el número de mensaje.

*wParam*<br/>
Especifica información adicional sobre el mensaje. El significado exacto depende del valor de la `message` miembro.

*lParam*<br/>
Especifica información adicional sobre el mensaje. El significado exacto depende del valor de la `message` miembro.

*time*<br/>
Especifica la hora a la que se expuso el mensaje.

*PT*<br/>
Especifica la posición del cursor, en coordenadas de pantalla, cuando se expuso el mensaje.

## <a name="requirements"></a>Requisitos

**Encabezado:** winuser.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

