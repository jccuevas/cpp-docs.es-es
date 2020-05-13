---
title: _seh_filter_dll, _seh_filter_exe
ms.date: 4/2/2020
api_name:
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- _o__seh_filter_dll
- _o__seh_filter_exe
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- XcptFilter
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- corecrt_startup/_seh_filter_exe
- corecrt_startup/_seh_filter_dll
helpviewer_keywords:
- XcptFilter function
- _XcptFilter function
- _seh_filter_dll function
- _seh_filter_exe function
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
ms.openlocfilehash: ddfab11b149fc6919fb0b8d461b914a0470d9dc9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913200"
---
# <a name="_seh_filter_dll-_seh_filter_exe"></a>_seh_filter_dll, _seh_filter_exe

Identifica la excepción y la acción relacionada que se debe realizar.

## <a name="syntax"></a>Sintaxis

```C
int __cdecl _seh_filter_dll(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
int __cdecl _seh_filter_exe(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
```

### <a name="parameters"></a>Parámetros

*_ExceptionNum*<br/>
El identificador de la excepción.

*_ExceptionPtr*<br/>
Puntero a la información de la excepción.

## <a name="return-value"></a>Valor devuelto

Un entero que indica la acción que se realizará, según el resultado del procesamiento de la excepción.

## <a name="remarks"></a>Observaciones

Estos métodos son invocados por la expresión de filtro de excepción de la [try-except Statement](../../cpp/try-except-statement.md). El método consulta una tabla interna constante para identificar la excepción y determinar la acción correspondiente, tal como se muestra a continuación. Los números de excepción se definen en winnt.h y los números de señal se definen en signal.h.

|Número de excepción (largo sin signo)|Número de señal|
|----------------------------------------|-------------------|
|STATUS_ACCESS_VIOLATION|SIGSEGV|
|STATUS_ILLEGAL_INSTRUCTION|SIGILL|
|STATUS_PRIVILEGED_INSTRUCTION|SIGILL|
|STATUS_FLOAT_DENORMAL_OPERAND|SIGFPE|
|STATUS_FLOAT_DIVIDE_BY_ZERO|SIGFPE|
|STATUS_FLOAT_INEXACT_RESULT|SIGFPE|
|STATUS_FLOAT_INVALID_OPERATION|SIGFPE|
|STATUS_FLOAT_OVERFLOW|SIGFPE|
|STATUS_FLOAT_STACK_CHECK|SIGFPE|
|STATUS_FLOAT_UNDERFLOW|SIGFPE|

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** corecrt_startup.h

## <a name="see-also"></a>Consulta también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
