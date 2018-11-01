---
title: Macros de mensajes de Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 3ab102ec486af0c7119e8ed28da4898c8beeb293
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582525"
---
# <a name="windows-messages-macros"></a>Macros de mensajes de Windows

Esta macro reenvía los mensajes de ventana.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Usar para reenviar un mensaje recibido en una ventana a otra ventana para su procesamiento.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

Esta macro reenvía un mensaje recibido en una ventana a otra ventana para su procesamiento.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha procesado el mensaje, cero si no.

### <a name="remarks"></a>Comentarios

Usar WM_FORWARDMSG para reenviar un mensaje recibido en una ventana a otra ventana para su procesamiento. Los parámetros LPARAM y WPARAM se usan como sigue:

|Parámetro|Uso|
|---------------|-----------|
|WPARAM|Datos definidos por el usuario|
|LPARAM|Un puntero a un `MSG` estructura que contiene información acerca de un mensaje|

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, `m_hWndOther` representa la otra ventana que recibe este mensaje.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
