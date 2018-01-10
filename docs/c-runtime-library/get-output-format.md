---
title: _get_output_format | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_output_format
apilocation:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- get_output_format
- _get_output_format
dev_langs: C++
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30ee8de9c39d2b7e1fc6f9cf0a717120c95e92c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="getoutputformat"></a>_get_output_format
Obtiene el valor actual de la marca del formato de salida.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned int _get_output_format();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El valor actual de la marca del formato de salida.  
  
## <a name="remarks"></a>Comentarios  
 La marca del formato de salida controla las características de la E/S con formato. En la actualidad, la marca tiene dos valores posibles: 0 y `_TWO_DIGIT_EXPONENT`. Si se establece `_TWO_DIGIT_EXPONENT` , los números de punto flotante se imprimen solo con dos dígitos en el exponente, a menos el tamaño del exponente requiera un tercer dígito. Si la marca es cero, la salida de punto flotante muestra tres dígitos del exponente, con ceros si es necesario para rellenar el valor hasta los tres dígitos.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_get_output_format`|\<stdio.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
[Sintaxis de especificación de formato: printf y wprintf (funciones)](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)  
 [printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_set_output_format](../c-runtime-library/set-output-format.md)  
