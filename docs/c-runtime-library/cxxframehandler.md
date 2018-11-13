---
title: __CxxFrameHandler
ms.date: 11/04/2016
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: d059df597826c68f4f51eb85f592b7eb44ac7d1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432129"
---
# <a name="cxxframehandler"></a>__CxxFrameHandler

Función de CRT interna. CRT la usa para controlar los marcos de excepción estructurados.

## <a name="syntax"></a>Sintaxis

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>Parámetros

*pExcept*<br/>
Registro de excepción que se pasa a las posibles instrucciones `catch`.

*pRN*<br/>
Información dinámica sobre el marco de pila que se usa para controlar la excepción. Para más información, vea ehdata.h.

*pContext*<br/>
Contexto. (No se usa en procesadores Intel).

*pDC*<br/>
Información extra sobre la entrada de la función y el marco de pila.

## <a name="return-value"></a>Valor devuelto

Uno de los valores de *expresión de filtro* usado por la [instrucción try-except](../cpp/try-except-statement.md).

## <a name="remarks"></a>Comentarios

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h, ehdata.h|