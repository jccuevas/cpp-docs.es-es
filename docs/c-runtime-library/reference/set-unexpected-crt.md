---
title: "set_unexpected (CRT) | Microsoft Docs"
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
  - "set_unexpected"
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
  - "set_unexpected"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "control de excepciones, terminación"
  - "set_unexpected (función)"
  - "función inesperada"
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set_unexpected (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Instala por la función de finalización que se denomine por `unexpected`.  
  
## Sintaxis  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### Parámetros  
 `unexpFunction`  
 Puntero a una función que se escribe para reemplazar la función de `unexpected` .  
  
## Valor devuelto  
 Devuelve un puntero a la función anterior de finalización registrada por `_set_unexpected` para poder restaurar la función anterior más adelante.  Si no se ha establecido ninguna función anterior, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; este valor puede ser NULL.  
  
## Comentarios  
 La función de `set_unexpected` instala `unexpFunction` como la función llamada por `unexpected`.  `unexpected` no se utiliza en la implementación actual del control de excepciones de C\+\+.  Define el tipo de `unexpected_function` en EH.H como puntero a una función inesperada definido por el usuario, `unexpFunction` que devuelve `void`.  La función personalizada de `unexpFunction` no debe volver al llamador.  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 De forma predeterminada, llamadas `terminate`de `unexpected` .  Puede cambiar este comportamiento predeterminado escribiendo dispone de la función de finalización y llamando `set_unexpected` con el nombre de la función como argumento.  `unexpected` llama a la función última especificada como argumento a `set_unexpected`.  
  
 A diferencia de la función personalizada de finalización instalada por una llamada a `set_terminate`, una excepción puede producirse dentro de `unexpFunction`.  
  
 En un entorno multiproceso, funciones inesperadas se mantienen por separado para cada subproceso.  Cada nuevo subproceso necesita instalar su propia función inesperada.  Así, cada subproceso está responsable de su propia administración inesperado.  
  
 En la implementación de Microsoft actual del control de excepciones de C\+\+, `unexpected` llama `terminate` de forma predeterminada y nunca llama la biblioteca en tiempo de ejecución excepción\- que administra.  No hay ninguna ventaja concreta a `unexpected` en lugar de `terminate`.  
  
 Hay solo controlador de `set_unexpected` para todos los archivos DLL o EXE dinámicamente vinculados; incluso si llama a `set_unexpected` el controlador puede reemplazar por otro o que se está reemplazando un controlador establecido por otra DLL o EXE.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`set_unexpected`|\<eh.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_get\_unexpected](../../c-runtime-library/reference/get-unexpected.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)