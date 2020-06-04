---
title: _except_handler3
ms.date: 11/04/2016
api_name:
- _except_handler3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 5e1dbab97e0f193d4ff59c19229d2c00e2cd7d6a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944483"
---
# <a name="_except_handler3"></a>_except_handler3

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
