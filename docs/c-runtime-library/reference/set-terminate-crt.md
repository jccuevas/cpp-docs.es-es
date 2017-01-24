---
title: "set_terminate (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "set_terminate"
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
  - "set_terminate"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "control de excepciones, terminación"
  - "set_terminate (función)"
  - "terminate (función)"
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set_terminate (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Instala poseen la rutina de finalización que se denomine por `terminate`.  
  
## Sintaxis  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### Parámetros  
 `termFunction`  
 Puntero a una función de terminación que escribe.  
  
## Valor devuelto  
 Devuelve un puntero a la función anterior registrada por `set_terminate` para poder restaurar la función anterior más adelante.  Si no se ha establecido ninguna función anterior, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; este valor puede ser NULL.  
  
## Comentarios  
 La función de `set_terminate` instala `termFunction` como la función llamada por `terminate`.  `set_terminate` se utiliza con el control de excepciones de C\+\+ y se puede llamar en cualquier punto del programa antes de que se produzca la excepción.  llamadas `abort` de`terminate` de forma predeterminada.  Puede cambiar este valor predeterminado escribiendo dispone de la función de finalización y llamando `set_terminate` con el nombre de la función como argumento.  `terminate` llama a la función última especificada como argumento a `set_terminate`.  Después de realizar las tareas deseadas de limpieza, `termFunction` debe salir del programa.  Si no sale \(si vuelve a su llamador\), se llama a `abort` .  
  
 En un entorno multiproceso, finalice las funciones se mantienen por separado para cada subproceso.  Cada nuevo subproceso necesita instalar sus propios finaliza la función.  Así, cada subproceso está responsable de su propio control de finalización.  
  
 Define el tipo de `terminate_function` en EH.H como puntero a una función definida por el usuario de finalización, `termFunction` que devuelve `void`.  La función personalizada `termFunction` no puede tomar ningún argumento y no debe volver al llamador.  Si lo hace, se llama `abort` .  Una excepción no puede producirse dentro de `termFunction`.  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  La función de `set_terminate` sólo funciona fuera del depurador.  
  
 Hay solo controlador de `set_terminate` para todos los archivos DLL o EXE dinámicamente vinculados; incluso si llama a `set_terminate` el controlador puede reemplazar por otro, o puede reemplazar un controlador establecido por otra DLL o EXE.  
  
 Esta función no se admite en **\/clr:pure**.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`set_terminate`|\<eh.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [finalice](../../c-runtime-library/reference/terminate-crt.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_get\_terminate](../../c-runtime-library/reference/get-terminate.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)