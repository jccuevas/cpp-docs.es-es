---
title: Funciones globales de contexto de dispositivo
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: aeebec65def9364e56156f6bb323815da012e11f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276567"
---
# <a name="device-context-global-functions"></a>Funciones globales de contexto de dispositivo

Esta función crea un contexto de dispositivo para un dispositivo determinado.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crea un contexto de dispositivo.|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

Crea un contexto de dispositivo para el dispositivo especificado en el [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) estructura.

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parámetros

*hdc*<br/>
[in] El identificador existente de un contexto de dispositivo, o NULL.

*ptd*<br/>
[in] Un puntero a la `DVTARGETDEVICE` estructura que contiene información sobre el dispositivo de destino.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de contexto de dispositivo para el dispositivo especificado en el `DVTARGETDEVICE`. Si no se especifica ningún dispositivo, devuelve el identificador para el dispositivo de pantalla de forma predeterminada.

### <a name="remarks"></a>Comentarios

Si la estructura es NULL y *hdc* es NULL, se crea un contexto de dispositivo de la pantalla de forma predeterminada.

Si *hdc* no es NULL y *ptd* es NULL, la función devuelve existente *hdc*.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
