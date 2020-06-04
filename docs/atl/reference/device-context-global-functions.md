---
title: Funciones globales de contexto de dispositivo
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: e640f310a1976c29a39f0ab7c2575dfd1073c889
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330150"
---
# <a name="device-context-global-functions"></a>Funciones globales de contexto de dispositivo

Esta función crea un contexto de dispositivo para un dispositivo determinado.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Crea un contexto de dispositivo.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a>AtlCreateTargetDC

Crea un contexto de dispositivo para el dispositivo especificado en la estructura [DVTARGETDEVICE.](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parámetros

*Hdc*<br/>
[en] El identificador existente de un contexto de dispositivo o NULL.

*Dpt*<br/>
[en] Puntero a `DVTARGETDEVICE` la estructura que contiene información sobre el dispositivo de destino.

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador a un contexto de `DVTARGETDEVICE`dispositivo para el dispositivo especificado en el archivo . Si no se especifica ningún dispositivo, devuelve el identificador al dispositivo de visualización predeterminado.

### <a name="remarks"></a>Observaciones

Si la estructura es NULL y *hdc* es NULL, crea un contexto de dispositivo para el dispositivo de presentación predeterminado.

Si *hdc* no es NULL y *ptd* es NULL, la función devuelve el *hdc*existente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
