---
title: _get_printf_count_output | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_printf_count_output
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
- get_printf_count_output
- _get_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 4373fc075e46110cbcef411b283b8566bf74508c
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="getprintfcountoutput"></a>_get_printf_count_output
Indica si la familia de funciones [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) admite el formato `%n`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _get_printf_count_output();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se admite `%n`, 0 si no se admite `%n`.  
  
## <a name="remarks"></a>Comentarios  
 Si `%n` no se admite (valor predeterminado), al encontrar `%n` en la cadena de formato de cualquiera de las funciones `printf` se invocará al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si `%n` compatibilidad está habilitada (vea [_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)), a continuación, `%n` se comportarán como se describe en [sintaxis de especificación de formato: funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_get_printf_count_output`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md).  
  
## <a name="see-also"></a>Vea también  
[_set_printf_count_output](../../c-runtime-library/reference/set-printf-count-output.md)  

