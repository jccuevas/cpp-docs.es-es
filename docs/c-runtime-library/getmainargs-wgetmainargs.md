---
title: "__getmainargs, __wgetmainargs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__wgetmainargs"
  - "__getmainargs"
apilocation: 
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__wgetmainargs"
  - "__getmainargs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__wgetmainargs"
  - "__getmainargs"
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# __getmainargs, __wgetmainargs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Invoca el análisis de la línea de comandos y copia los argumentos a la reproducción de `main()` a través de los punteros pasados.  
  
## Sintaxis  
  
```cpp  
int __getmainargs(  
    int * _Argc,   
   char *** _Argv,   
   char *** _Env,   
   int _DoWildCard,  
_startupinfo * _StartInfo);  
  
 int __wgetmainargs (  
   int *_Argc,  
   wchar_t ***_Argv,  
   wchar_t ***_Env,  
   int _DoWildCard,  
   _startupinfo * _StartInfo)  
  
```  
  
#### Parámetros  
 `_Argc`  
 Un entero que contiene el número de argumentos que hay en `argv`.  El parámetro `argc` es siempre mayor o igual que 1.  
  
 `_Argv`  
 Una matriz de cadenas terminadas en null que representan los argumentos de la línea de comandos especificados por el usuario del programa.  Por convención, `argv[0]` es el comando al que se invoca el programa, argv \[1\] es el primer argumento de la línea de comandos, etc., hasta el argv \[argc\], que siempre es NULL.  El primer argumento de la línea de comandos es siempre `argv[1]` y el último es `argv[argc – 1]`.  
  
 `_Env`  
 Una matriz de cadenas que representan las variables establecidas en el entorno de usuario.  Esta matriz termina con una entrada NULL.  
  
 `_DoWildCard`  
 Un entero que si el conjunto a 1 caracteres comodín en los argumentos de la línea de comandos, o si se establece en 0 no hace nada.  
  
 `_StartInfo`  
 Otra información que se va a pasar al archivo DLL de CRT.  
  
## Valor devuelto  
 0 si correctamente; un valor negativo si no.  
  
## Comentarios  
 Utilice `__getmainargs` en plataformas no\- anchas de caracteres, y `__wgetmainargs` en plataformas de caracteres anchos \(Unicode\).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_getmainargs|internal.h|  
|\_\_wgetmainargs|internal.h|