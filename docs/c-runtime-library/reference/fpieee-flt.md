---
title: _fpieee_flt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fpieee_flt
apilocation:
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
apitype: DLLExport
f1_keywords:
- fpieee_flt
- _fpieee_flt
dev_langs:
- C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88d05d4d8c7f403cc2702c5a0ec3b2af840bd320
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fpieeeflt"></a>_fpieee_flt
Invoca un controlador de interceptaciones definido por el usuario para las excepciones de punto flotante del IEEE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _fpieee_flt(   
   unsigned long excCode,  
   struct _EXCEPTION_POINTERS *excInfo,  
   int handler(_FPIEEE_RECORD *)   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `excCode`  
 Código de la excepción.  
  
 `excInfo`  
 Puntero a la estructura de información de excepción de Windows NT.  
  
 `handler`  
 Puntero a la rutina del controlador de interceptaciones del IEEE del usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor devuelto de `_fpieee_flt` es el valor devuelto por `handler`. Por tanto, la rutina de filtro del IEEE podría usarse en la cláusula de excepción de un mecanismo de control de excepciones estructurado (SEH).  
  
## <a name="remarks"></a>Comentarios  
 La función `_fpieee_flt` invoca un controlador de interceptaciones definido por el usuario para las excepciones de punto flotante del IEEE y le proporciona toda la información pertinente. Esta rutina actúa como filtro de excepciones en el mecanismo de SEH, que invoca el controlador de excepciones del IEEE propio cuando es necesario.  
  
 La estructura `_FPIEEE_RECORD`, definida en Fpieee.h, contiene información relativa a una excepción de punto flotante del IEEE. `_fpieee_flt` pasa esta estructura al controlador de interceptaciones definido por el usuario.  
  
|campo _FPIEEE_RECORD|Descripción|  
|----------------------------|-----------------|  
|`unsigned int RoundingMode`, `unsigned int Precision`|Estos campos contienen información sobre el entorno de punto flotante en el momento que se produjo la excepción.|  
|`unsigned int Operation`|Indica el tipo de operación que produjo la interceptación. Si el tipo es una comparación (`_FpCodeCompare`), puede proporcionar uno de los valores especiales de `_FPIEEE_COMPARE_RESULT` (definidos en Fpieee.h) en el campo `Result.Value`. El tipo de conversión (`_FpCodeConvert`) indica que la interceptación se produjo durante una operación de conversión de punto flotante. Puede consultar los tipos `Operand1` y `Result` para determinar el tipo de conversión que se intenta realizar.|  
|`_FPIEEE_VALUE Operand1`, `_FPIEEE_VALUE Operand2`, `_FPIEEE_VALUE Result`|Estas estructuras indican los tipos y valores del resultado y los operandos propuestos:<br /><br /> `OperandValid` Marca que indica si el valor de respuesta es válido.<br /><br /> `Format` Tipo de datos del valor correspondiente. El tipo de formato se podría devolver incluso si el valor correspondiente no es válido.<br /><br /> `Value` Valor de los datos del resultado o el operando.|  
|`_FPIEEE_EXCEPTION_FLAGS Cause`, `_FPIEEE_EXCEPTION_FLAGS Enable`, `_FPIEEE_EXCEPTION_FLAGS Status`|_FPIEEE_EXCEPTION_FLAGS contiene un campo de bits por cada tipo de excepción de punto flotante.<br /><br /> Hay una correspondencia entre estos campos y los argumentos usados para enmascarar las excepciones que se proporcionan en [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md).<br /><br /> El significado exacto de cada bit depende de contexto:<br /><br /> `Cause` Cada bit establecido indica la excepción concreta que se ha generado.<br /><br /> `Enable` Cada bit establecido indica que la excepción concreta no está enmascarada en este momento.<br /><br /> `Status` Cada bit establecido indica que la excepción concreta está pendiente en este momento. Se incluyen las excepciones que no se hayan producido porque `_controlfp` la había aplicado una máscara.|  
  
 Las excepciones pendientes que están deshabilitadas se producen cuando se habilitan. Esto podría producir un comportamiento indefinido si se usa `_fpieee_flt` como filtro de excepción. Llame siempre a [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md) antes de habilitar excepciones de punto flotante.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fpieee_flt`|\<fpieee.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)