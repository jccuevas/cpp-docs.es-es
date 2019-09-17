---
title: __CxxFrameHandler
ms.date: 11/04/2016
api_name:
- __CxxFrameHandler
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: 4cb5ae10d4281c4a7167db7adf4ea6788ad3e3c0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944511"
---
# <a name="__cxxframehandler"></a>__CxxFrameHandler

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