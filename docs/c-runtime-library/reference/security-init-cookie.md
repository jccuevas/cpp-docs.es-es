---
title: __security_init_cookie | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __security_init_cookie
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
apitype: DLLExport
f1_keywords:
- security_init_cookie
- __security_init_cookie
dev_langs: C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee0657393ec8322889b527c21a36c13b9e032325
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="securityinitcookie"></a>__security_init_cookie
Inicializa la cookie de seguridad global.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __security_init_cookie(void);  
```  
  
## <a name="remarks"></a>Comentarios  
 La cookie de seguridad global se usa para la protección de saturación del búfer en el código compilado con [/GS (Comprobación de seguridad del búfer)](../../build/reference/gs-buffer-security-check.md) y en el código que usa el control de excepciones. En la entrada a una función con protección de saturación, la cookie se coloca en la pila y, en la salida, el valor de la pila se compara con la cookie global. Cualquier diferencia en la comparación indica que se ha producido una saturación del búfer y da lugar a la finalización inmediata del programa.  
  
 Normalmente, el CRT llama a `__security_init_cookie` al inicializarse. Si se omite la inicialización de CRT (por ejemplo, si usa [/ENTRY](../../build/reference/entry-entry-point-symbol.md) para especificar un punto de entrada), deberá llamar a `__security_init_cookie`. Si no se llama a `__security_init_cookie`, la cookie de seguridad global se configura en un valor predeterminado y se pone en peligro la protección de saturación del búfer Dado que un atacante puede aprovechar este valor de cookie predeterminado para invalidar las comprobaciones de saturación del búfer, se recomienda que llame siempre a `__security_init_cookie` al definir su propio punto de entrada.  
  
 La llamada a `__security_init_cookie` se debe hacer antes de especificar ninguna función de protección contra saturación, ya que de lo contrario se detecta una saturación del búfer falsa. Para obtener más información, vea [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) (Error de tiempo de ejecución de C R6035).  
  
## <a name="example"></a>Ejemplo  
 Vea los ejemplos de [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) (Error de tiempo de ejecución de C R6035).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`__security_init_cookie`|\<process.h>|  
  
 `__security_init_cookie` es una extensión de Microsoft de la biblioteca estándar en tiempo de ejecución de C. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Comprobación de seguridad exhaustiva del compilador](http://go.microsoft.com/fwlink/p/?linkid=7260)