---
title: _set_output_format | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _set_output_format
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- set_output_format
- _set_output_format
dev_langs:
- C++
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d61b17bb597028bec55edb148897929f178392d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="setoutputformat"></a>_set_output_format
Personaliza los formatos de salida que usan las funciones de E/S con formato.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned int _set_output_format(  
   unsigned int format  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `format`  
 Un valor que representa el formato que se utilizará.  
  
## <a name="return-value"></a>Valor devuelto  
 El formato de salida anterior.  
  
## <a name="remarks"></a>Comentarios  
 `_set_output_format` se usa para configurar la salida de funciones de E/S con formato tales como [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). En la actualidad, la única convención de formato que esta función puede cambiar es el número de dígitos que se muestran en los exponentes de la salida de números de punto flotante.  
  
 De forma predeterminada, la salida de números de punto flotante con funciones como `printf_s`, `wprintf_s`y funciones relacionadas de la biblioteca de C estándar de Visual C++ imprime tres dígitos del exponente, incluso aunque no se requieran tres dígitos para representar el valor del exponente. Se utilizan ceros para rellenar el valor hasta los tres dígitos. `_set_output_format` le permite cambiar este comportamiento para que solo se impriman dos dígitos en el exponente, a menos que sea necesario un tercer dígito debido al tamaño del exponente.  
  
 Para habilitar los exponentes de dos dígitos, llame a esta función con el parámetro `_TWO_DIGIT_EXPONENT`, como se muestra en el ejemplo. Para deshabilitar los exponentes de dos dígitos, llame a esta función con un argumento de 0.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_set_output_format`|\<stdio.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_set_output_format.c  
#include <stdio.h>  
  
void printvalues(double x, double y)  
{  
   printf_s("%11.4e %11.4e\n", x, y);  
   printf_s("%11.4E %11.4E\n", x, y);  
   printf_s("%11.4g %11.4g\n", x, y);  
   printf_s("%11.4G %11.4G\n", x, y);  
}  
  
int main()  
{  
   double x = 1.211E-5;  
   double y = 2.3056E-112;  
   unsigned int old_exponent_format;  
  
   // Use the default format  
   printvalues(x, y);  
  
   // Enable two-digit exponent format  
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);  
  
   printvalues(x, y);  
  
   // Disable two-digit exponent format  
   _set_output_format( old_exponent_format );  
  
   printvalues(x, y);  
}  
```  
  
```Output  
1.2110e-005 2.3056e-112  
1.2110E-005 2.3056E-112  
 1.211e-005  2.306e-112  
 1.211E-005  2.306E-112  
 1.2110e-05 2.3056e-112  
 1.2110E-05 2.3056E-112  
  1.211e-05  2.306e-112  
  1.211E-05  2.306E-112  
1.2110e-005 2.3056e-112  
1.2110E-005 2.3056E-112  
 1.211e-005  2.306e-112  
 1.211E-005  2.306E-112  
```  
  
## <a name="see-also"></a>Vea también  
 [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_get_output_format](../c-runtime-library/get-output-format.md)