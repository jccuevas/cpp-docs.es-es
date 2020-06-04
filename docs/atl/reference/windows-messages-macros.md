---
title: Macros de mensajes de Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: a5a6d45c64d6123128ae362c1ef5643392439f41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329407"
---
# <a name="windows-messages-macros"></a>Macros de mensajes de Windows

Esta macro reenvía los mensajes de ventana.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Se utiliza para reenviar un mensaje recibido por una ventana a otra ventana para su procesamiento.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG

Esta macro reenvía un mensaje recibido por una ventana a otra ventana para su procesamiento.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mensaje se ha procesado, cero si no.

### <a name="remarks"></a>Observaciones

Utilice WM_FORWARDMSG para reenviar un mensaje recibido por una ventana a otra ventana para su procesamiento. Los parámetros LPARAM y WPARAM se utilizan de la siguiente manera:

|Parámetro|Uso|
|---------------|-----------|
|Wparam|Datos definidos por el usuario|
|Lparam|Un puntero `MSG` a una estructura que contiene información sobre un mensaje|

### <a name="example"></a>Ejemplo

En el ejemplo `m_hWndOther` siguiente, representa la otra ventana que recibe este mensaje.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
