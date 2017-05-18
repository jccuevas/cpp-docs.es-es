---
title: _set_printf_count_output | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: aadbf7d2c6fece48ab29c1b818995464a790c38b
ms.openlocfilehash: 11f0dbe2a4bb67992dd307aea62f79ca8f6b5f73
ms.contentlocale: es-es
ms.lasthandoff: 03/07/2017

---
# <a name="setprintfcountoutput"></a>_set_printf_count_output
Habilite o deshabilite la compatibilidad del formato `%n` en las funciones de las familias [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _set_printf_count_output(  
   int enable  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `enable`  
 Un valor distinto de cero para habilitar el soporte de `%n`; 0 para deshabilitar el soporte de `%n`.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 El estado del soporte de `%n` antes de llamar a esta función: valor distinto de cero si el soporte de `%n` estaba habilitado o 0 si estaba deshabilitado.  
  
## <a name="remarks"></a>Comentarios  
 Por motivos de seguridad, la compatibilidad con el especificador de formato `%n` está deshabilitada de forma predeterminada en `printf` y en todas sus variantes. Si `%n` aparece en una especificación de formato `printf`, el comportamiento predeterminado consiste en invocar al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Al llamar a `_set_printf_count_output` con un argumento distinto de cero provocarán `printf`-familia de funciones para interpretar `%n` tal y como se describe en [sintaxis de especificación de formato: funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_set_printf_count_output`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_set_printf_count_output.c  
#include <stdio.h>  
  
int main()  
{  
   int e;  
   int i;  
   e = _set_printf_count_output( 1 );  
   printf( "%%n support was %sabled.\n",  
        e ? "en" : "dis" );  
   printf( "%%n support is now %sabled.\n",  
        _get_printf_count_output() ? "en" : "dis" );  
   printf( "12345%n6789\n", &i ); // %n format should set i to 5  
   printf( "i = %d\n", i );  
}  
```  
  
```Output  
%n support was disabled.  
%n support is now enabled.  
123456789  
i = 5  
```  
  
## <a name="see-also"></a>Vea también  
 [_get_printf_count_output](../../c-runtime-library/reference/get-printf-count-output.md)
