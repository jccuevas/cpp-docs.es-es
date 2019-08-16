---
title: Funciones globales de contexto de dispositivo
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d225bd0cd996fd908479b5a93aad81ea0428900b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496100"
---
# <a name="device-context-global-functions"></a>Funciones globales de contexto de dispositivo

Esta función crea un contexto de dispositivo para un dispositivo determinado.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crea un contexto de dispositivo.|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

Crea un contexto de dispositivo para el dispositivo especificado en la estructura [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) .

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parámetros

*hdc*<br/>
de Identificador existente de un contexto de dispositivo o NULL.

*ptd*<br/>
de Puntero a la `DVTARGETDEVICE` estructura que contiene información sobre el dispositivo de destino.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de un contexto de dispositivo para el dispositivo especificado en `DVTARGETDEVICE`. Si no se especifica ningún dispositivo, devuelve el identificador del dispositivo de pantalla predeterminado.

### <a name="remarks"></a>Comentarios

Si la estructura es NULL y *HDC* es null, crea un contexto de dispositivo para el dispositivo de pantalla predeterminado.

Si *HDC* no es NULL y *PTD* es null, la función devuelve la *HDC*existente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
