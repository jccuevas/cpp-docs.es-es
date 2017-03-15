---
title: "_setmbcp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_setmbcp"
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
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_setmbcp"
  - "setmbcp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setmbcp (función)"
  - "páginas de códigos multibyte"
  - "setmbcp (función)"
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _setmbcp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece una nueva página de códigos multibyte.  
  
## Sintaxis  
  
```  
int _setmbcp(  
   int codepage   
);  
```  
  
#### Parámetros  
 `codepage`  
 Nueva paginación de código para las rutinas multibyte de configuración regional\- independiente.  
  
## Valor devuelto  
 Devuelve 0 si la página de códigos se establece correctamente.  Si un valor no válido de la página de códigos se proporciona para `codepage`, devuelve – 1 y la paginación de código no cambia.  Establece `errno` a `EINVAL` si un error de asignación de memoria aparece.  
  
## Comentarios  
 La función de `_setmbcp` especifica una nueva página de códigos multibyte.  De forma predeterminada, el sistema en tiempo de ejecución establece automáticamente la página de códigos multibyte a la página de códigos ANSI del sistema\- predeterminado.  La paginación de código multibyte afecta a todas las rutinas multibyte que no son dependientes de la configuración regional.  Sin embargo, es posible dar instrucciones `_setmbcp` para utilizar la página de códigos definida para la configuración regional actual \(vea la siguiente lista de constantes de manifiesto y resultados asociados de comportamiento\).  Para obtener una lista de las rutinas multibyte dependientes de la página de códigos de la configuración regional en lugar de la página de códigos multibyte, vea [Interpretación de secuencias de Multibyte\- carácter](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).  
  
 La página de códigos multibyte también afecta al procesamiento de multibyte\- carácter por las rutinas de biblioteca en tiempo de ejecución siguientes:  
  
||||  
|-|-|-|  
|[Funciones \_exec](../../c-runtime-library/exec-wexec-functions.md)|[\_mktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)|[\_stat](../../c-runtime-library/reference/stat-functions.md)|  
|[\_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[Funciones \_spawn](../../c-runtime-library/spawn-wspawn-functions.md)|[\_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[\_makepath](../../c-runtime-library/reference/makepath-wmakepath.md)|[\_splitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)|[tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
  
 Además, todas las rutinas de biblioteca en tiempo de ejecución que reciben el multibyte\- carácter `argv` o argumentos del `envp` como parámetros \(como las familias de `_exec` y de `_spawn` \) procesan estas cadenas según la página de códigos multibyte.  Por tanto, estas rutinas también se ven afectadas por una llamada a `_setmbcp` que cambie la página de códigos multibyte.  
  
 El argumento de `codepage` se puede establecer en cualquiera de los valores siguientes:  
  
-   `_MB_CP_ANSI` Utilice la página de códigos ANSI obtenida del sistema operativo en el inicio del programa.  
  
-   `_MB_CP_LOCALE` Utilice la página de códigos actual de la configuración regional obtenida de una llamada anterior a [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   `_MB_CP_OEM` Utilice la página de códigos OEM obtenida del sistema operativo en el inicio del programa.  
  
-   `_MB_CP_SBCS` Utilice la página de códigos de solo\- byte.  Cuando la página de códigos se establece en `_MB_CP_SBCS`, una rutina como [\_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) siempre devuelve false.  
  
-   Cualquier otro valor válido de la página de códigos, independientemente de si el valor es el ANSI, el OEM, u otra página de códigos funcionamiento\-sistema\- compatible \(excepto UTF\-7 y UTF\-8, que no se admiten\).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_setmbcp`|\<mbctype.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)