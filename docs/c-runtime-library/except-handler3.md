---
title: _except_handler3
ms.date: 11/04/2016
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 144bf25495d803a4db42ab45fcb0b101b09fe7cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613868"
---
# <a name="excepthandler3"></a>_except_handler3

Función de CRT interna. Usada por un marco para encontrar el controlador de excepciones adecuado para procesar la excepción actual.

## <a name="syntax"></a>Sintaxis

```
int _except_handler3(
   PEXCEPTION_RECORD exception_record,
   PEXCEPTION_REGISTRATION registration,
   PCONTEXT context,
   PEXCEPTION_REGISTRATION dispatcher
);
```

#### <a name="parameters"></a>Parámetros

*exception_record*<br/>
[in] Información sobre la excepción específica.

*registration*<br/>
[in] Registro que indica qué tabla de ámbito se debe usar para encontrar el controlador de excepciones.

*context*<br/>
[in] Reservado.

*dispatcher*<br/>
[in] Reservado.

## <a name="return-value"></a>Valor devuelto

En caso de que una excepción deba descartarse, devuelve `DISPOSITION_DISMISS`. Si la excepción debe trasladarse a un nivel superior de controladores de excepciones, devuelve `DISPOSITION_CONTINUE_SEARCH`.

## <a name="remarks"></a>Comentarios

Si se encuentra un controlador de excepciones adecuado con este método, la excepción se pasa a dicho controlador. En este caso, el método no regresa al código que lo llamó y el valor devuelto es irrelevante.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)