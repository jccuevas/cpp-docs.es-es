---
title: LINGER (Estructura)
ms.date: 11/04/2016
f1_keywords:
- LINGER
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
ms.openlocfilehash: 78f1a5ce993373ea9e477262f0779515c52dbd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495323"
---
# <a name="linger-structure"></a>LINGER (Estructura)

El `LINGER` estructura se usa para manipular las opciones de SO_LINGER y SO_DONTLINGER `CAsyncSocket::GetSockOpt`.

## <a name="syntax"></a>Sintaxis

```
struct linger {
    u_short l_onoff;            // option on/off
    u_short l_linger;           // linger time
};
```

## <a name="remarks"></a>Comentarios

Establecer la opción SO_DONTLINGER evita el bloqueo en una función miembro `Close` mientras se espera que se envíen datos no enviados. Al establecer esta opción es equivalente a establecer SO_LINGER con `l_onoff` establecido en 0.

## <a name="requirements"></a>Requisitos

**Encabezado:** winsock2.h

## <a name="see-also"></a>Vea también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)<br/>
[CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

