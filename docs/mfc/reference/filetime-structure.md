---
title: FILETIME (estructura) | Microsoft Docs
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
ms.openlocfilehash: 4377daa0b8a1420e4f1b5afe1f36fa0fd18d581d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384603"
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

*dwLowDateTime*<br/>
Especifica el valor bajo de 32 bits de la hora del archivo.

*FILETIME*<br/>
Especifica el alto de 32 bits de la hora del archivo.

## <a name="requirements"></a>Requisitos

**Encabezado:** windef.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime:: CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

