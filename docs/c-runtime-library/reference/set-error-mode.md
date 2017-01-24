---
title: "_set_error_mode | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_error_mode"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "set_error_mode"
  - "_set_error_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_error_mode (función)"
  - "set_error_mode (función)"
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_error_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Modifica `__error_mode` para determinar una ubicación no predeterminada en donde el tiempo de ejecución de C escribe un mensaje de error si hay un error que podría finalizar el programa.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _set_error_mode(  
   int modeval   
);  
```  
  
#### Parámetros  
 `modeval`  
 Destino de los mensajes de error.  
  
## Valor devuelto  
 Devuelve el valor anterior o \-1 si se produce un error.  
  
## Comentarios  
 Controla el receptor de salida de error estableciendo el valor de `__error_mode`.  Por ejemplo, puede dirigir la salida a un error estándar o utilizar La API de `MessageBox`.  
  
 El parámetro `modeval` puede establecerse en uno de los valores siguientes:  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_OUT_TO_DEFAULT`|El receptor de errores viene determinado por `__app_type`.|  
|`_OUT_TO_STDERR`|El receptor de errores es un error estándar.|  
|`_OUT_TO_MSGBOX`|El receptor de errores es un cuadro de mensaje.|  
|`_REPORT_ERRMODE`|Notifica el valor actual de `__error_mode`.|  
  
 Si se pasa un valor distinto de los de la lista, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_set_error_mode` establece `errno` en `EINVAL` y devuelve \-1.  
  
 Cuando se usa con un [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md), `_set_error_mode` muestra la instrucción con errores en el cuadro de diálogo y ofrece la posibilidad de elegir el botón `Ignore` para que se pueda seguir ejecutando el programa.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_error_mode`|\<stdlib.h\>|  
  
## Ejemplo  
  
```  
// crt_set_error_mode.c  
// compile with: /c  
#include <stdlib.h>  
#include <assert.h>  
  
int main()  
{  
   _set_error_mode(_OUT_TO_STDERR);  
   assert(2+2==5);  
}  
```  
  
  **Error de aserción: 2\+2\=\=5, crt\_set\_error\_mode.c de archivo, línea 8**  
**Esta aplicación solicitó la finalización del tiempo de ejecución de modo no habitual.  Póngase en contacto con el equipo de asistencia técnica de la aplicación para obtener más información.**    
## Vea también  
 [assert \(macro\), \_assert, \_wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)