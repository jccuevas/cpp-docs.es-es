---
title: "Tipos de datos de SBCS y MBCS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MBCS"
  - "SBCS"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tipos de datos de SBCS y MBCS"
  - "tipos de datos [C], MBCS y SBCS"
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tipos de datos de SBCS y MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cualquier rutina de biblioteca en tiempo de ejecución de Microsoft `MBCS` que controle sólo un carácter multibyte o un byte de un carácter multibyte cuenta con un argumento de `unsigned``int` \(donde 0x00 \<\= valor \<de carácter \= 0xFFFF y valor \<\<de 0x00 \= de bytes \= 0xFF\).  Una rutina de `MBCS` que controla bytes o caracteres multibyte en un contexto de cadena que espera una cadena de multibyte\- carácter se representa como un puntero de `unsigned``char` .  
  
> [!CAUTION]
>  Cada byte de un carácter multibyte se puede representar en `char`de 8 bits.  Sin embargo, `SBCS` o un carácter de solo\- byte de `MBCS` de `char` escrito con un valor mayor que 0x7F es negativo.  Cuando este tipo de carácter se convierte directamente a `int` o a `long`, el resultado signo\- se extiende por el compilador y por lo que puede producir resultados inesperados.  
  
 Por consiguiente es mejor representar un byte de un carácter multibyte como `unsigned char`de 8 bits.  O, evitar negativamente, convertir simplemente un carácter de solo\- byte de `char` tipo a `unsigned char` antes de convertirlo a `int` o a `long`.  
  
 Dado que algunos `SBCS` cadena\- que administra funciones toma los parámetros \(con signo\) de `char*` , una advertencia del compilador de no coincidencia de tipos se producirá cuando se define `_MBCS` .  Hay tres formas de evitar esta advertencia, enumerada en orden de eficacia:  
  
1.  Utilice las funciones inline “tipo\- seguras” en TCHAR.H.  Éste es el comportamiento predeterminado.  
  
2.  Utilice “y” macros en TCHAR.H definiendo `_MB_MAP_DIRECT` en la línea de comandos.  Si lo hace, deberá hacer coincidir los tipos manualmente.  Este es el método más rápido pero no es tipo\- seguro.  
  
3.  Utilice las funciones de biblioteca vinculadas estáticamente “tipo\- seguras” en TCHAR.H.  Para ello, defina la constante `_NO_INLINING` en la línea de comandos.  Este es el método más lento, pero garantiza prácticamente la seguridad de tipos.  
  
## Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)