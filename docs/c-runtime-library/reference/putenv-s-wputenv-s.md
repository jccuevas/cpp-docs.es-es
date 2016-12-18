---
title: "_putenv_s, _wputenv_s | Microsoft Docs"
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
  - "_wputenv_s"
  - "_putenv_s"
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
apitype: "DLLExport"
f1_keywords: 
  - "putenv_s"
  - "wputenv_s"
  - "_wputenv_s"
  - "_putenv_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putenv_s (función)"
  - "_wputenv_s (función)"
  - "variables de entorno, crear"
  - "variables de entorno, eliminar"
  - "variables de entorno, modificar"
  - "putenv_s (función)"
  - "wputenv_s (función)"
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putenv_s, _wputenv_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea, modifica o quita variables de entorno.  Se trata de versiones de [\_putenv, \_wputenv](../../c-runtime-library/reference/putenv-wputenv.md) que tienen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/es-es/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t _putenv_s(  
   const char *name,  
   const char *value   
);  
errno_t _wputenv_s(  
   const wchar_t *name,  
   const wchar_t *value  
);  
```  
  
#### Parámetros  
 `name`  
 Nombre de la variable de entorno.  
  
 `value`  
 Valor en el que se establece la variable de entorno.  
  
## Valor devuelto  
 Devuelve 0 si se ejecuta correctamente; de lo contrario, devuelve un código de error.  
  
### Condiciones de error  
  
|`name`|`value`|Valor devuelto|  
|------------|-------------|--------------------|  
|`NULL`|cualquiera|`EINVAL`|  
|cualquiera|`NULL`|`EINVAL`|  
  
 Si se produce una de las condiciones de error estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EINVAL` y establecen `errno` en `EINVAL`.  
  
## Comentarios  
 La función `_putenv_s` agrega nuevas variables de entorno o modifica los valores de las existentes.  Las variables de entorno definen el entorno en el que se ejecuta un proceso \(por ejemplo, la ruta de búsqueda predeterminada para vincular bibliotecas a un programa\).  `_wputenv_s` es una versión con caracteres anchos de `_putenv_s`; el argumento `envstring` para `_wputenv_s` es una cadena de caracteres anchos.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tputenv_s`|`_putenv_s`|`_putenv_s`|`_wputenv_s`|  
  
 `name` es el nombre de la variable de entorno que se va a agregar o modificar y `value` es el valor de la variable.  Si `name` ya forma parte del entorno, su valor se sustituye por `value`; de lo contrario, la nueva variable `name` y su valor `value` se agregan al entorno.  Una variable se puede quitar del entorno especificando una cadena vacía \(es decir, ""\) para `value`.  
  
 `_putenv_s` y `_wputenv_s` solo afectan al entorno que es local en el proceso actual. No se pueden usar para modificar el entorno del nivel de comandos.  Solo funcionan en estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el "segmento" de entorno que el sistema operativo crea para un proceso.  Cuando finaliza el proceso actual, el entorno vuelve al nivel del proceso de llamada, que en la mayoría de los casos es el nivel del sistema operativo.  Sin embargo, el entorno modificado se puede pasar a los nuevos procesos que `_spawn`, `_exec` o `system` crean. Estos nuevos procesos obtienen los nuevos elementos que `_putenv_s` y `_wputenv_s` agregan.  
  
 No cambie directamente una entrada de entorno: en lugar de ello, use `_putenv_s` o `_wputenv_s` para cambiarla.  Especialmente, la liberación directa de elementos de la matriz global `_environ[]` podría dar lugar a que se obtenga acceso a memoria no válida.  
  
 `getenv` y `_putenv_s` usan la variable global `_environ` para obtener acceso a la tabla de entorno. `_wgetenv` y `_wputenv_s` usan `_wenviron`.  `_putenv_s` y `_wputenv_s` pueden cambiar el valor de `_environ` y `_wenviron`, e invalidar así el argumento `envp` para `main` y el argumento `_wenvp` para `wmain`.  Por ello, es más seguro usar `_environ` o `_wenviron` para obtener acceso a la información del entorno.  Para obtener más información sobre la relación de `_putenv_s` y `_wputenv_s` con las variables globales, vea [\_environ, \_wenviron](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  Los grupos de funciones de `_putenv_s` y `_getenv_s` no son seguros para subprocesos.  `_getenv_s` podría devolver un puntero de cadena mientras `_putenv_s` modifica la cadena y, por lo tanto, generarían errores aleatorios.  Asegúrese de que las llamadas a estas funciones están sincronizadas.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_putenv_s`|\<stdlib.h\>|  
|`_wputenv_s`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Para obtener un ejemplo que muestra cómo usar `_putenv_s`, vea [getenv\_s, \_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [getenv, \_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [\_searchenv, \_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)