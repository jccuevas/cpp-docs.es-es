---
title: _fpieee_flt
ms.date: 04/05/2018
api_name:
- _fpieee_flt
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 8835a3184300f1c56f1123a09aa48cd34a387c87
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957026"
---
# <a name="_fpieee_flt"></a>_fpieee_flt

Invoca un controlador de interceptaciones definido por el usuario para las excepciones de punto flotante del IEEE.

## <a name="syntax"></a>Sintaxis

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>Parámetros

*excCode*<br/>
Código de la excepción.

*excInfo*<br/>
Puntero a la estructura de información de excepción de Windows NT.

*handler*<br/>
Puntero a la rutina del controlador de interceptaciones del IEEE del usuario.

## <a name="return-value"></a>Valor devuelto

El valor devuelto de **_fpieee_flt** es el valor devuelto por el *controlador*. Por tanto, la rutina de filtro del IEEE podría usarse en la cláusula de excepción de un mecanismo de control de excepciones estructurado (SEH).

## <a name="remarks"></a>Comentarios

La función **_fpieee_flt** invoca un controlador de interceptaciones definido por el usuario para las excepciones de punto flotante de IEEE y le proporciona toda la información pertinente. Esta rutina actúa como filtro de excepciones en el mecanismo de SEH, que invoca el controlador de excepciones del IEEE propio cuando es necesario.

La estructura **_FPIEEE_RECORD** , definida en FPIEEE. h, contiene información relativa a una excepción de punto flotante de IEEE. **_Fpieee_flt**pasa esta estructura al controlador de interceptaciones definido por el usuario.

|campo _FPIEEE_RECORD|DESCRIPCIÓN|
|----------------------------|-----------------|
|**RoundingMode**<br/>**Precisión**|Estos campos **int** **sin signo** contienen información sobre el entorno de punto flotante en el momento en que se produjo la excepción.|
|**Sesión**|Este campo **int** **sin signo** indica el tipo de operación que provocó la captura. Si el tipo es una comparación ( **_FpCodeCompare**), puede proporcionar uno de los valores especiales de **_FPIEEE_COMPARE_RESULT** (tal y como se define en FPIEEE. h) en el campo **result. Value** . El tipo de conversión ( **_FpCodeConvert**) indica que la captura se produjo durante una operación de conversión de punto flotante. Puede examinar los tipos **Operand1** y **result** para determinar el tipo de conversión que se está intentando.|
|**Operand1**<br/>**Operand2**<br/>**Resultado**|Estas estructuras **_FPIEEE_VALUE** indican los tipos y valores del resultado propuesto y los operandos. Cada estructura contiene estos campos:<br /><br /> **OperandValid** : marca que indica si el valor de respuesta es válido.<br />**Formato** : tipo de datos del valor correspondiente. El tipo de formato se podría devolver incluso si el valor correspondiente no es válido.<br />**Valor:** resultado o valor de datos de operando.|
|**Causa**<br/>**Enable**<br/>**Estado**|**_FPIEEE_EXCEPTION_FLAGS** contiene un campo de bits por cada tipo de excepción de punto flotante. Hay una correspondencia entre estos campos y los argumentos usados para enmascarar las excepciones que se proporcionan en [_controlfp](control87-controlfp-control87-2.md). El significado exacto de cada bit depende de contexto:<br /><br /> **Causa** : cada bit establecido indica la excepción concreta que se ha producido.<br />**Enable** : cada bit establecido indica que la excepción concreta no está enmascarada actualmente.<br />**Estado** : cada bit establecido indica que la excepción determinada está pendiente actualmente. Esto incluye las excepciones que no se han producido porque se han enmascarado mediante _ **controlfp**.|

Las excepciones pendientes que están deshabilitadas se producen cuando se habilitan. Esto puede dar lugar a un comportamiento indefinido al usar **_fpieee_flt** como filtro de excepciones. Llame siempre a [_clearfp](clear87-clearfp.md) antes de habilitar excepciones de punto flotante.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
