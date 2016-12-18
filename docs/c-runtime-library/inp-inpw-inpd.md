---
title: "_inp, _inpw, _inpd | Microsoft Docs"
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
  - "_inp"
  - "_inpw"
  - "_inpd"
apilocation: 
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "inpd"
  - "_inp"
  - "_inpw"
  - "_inpd"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_inp (función)"
  - "_inpd (función)"
  - "_inpw (función)"
  - "E/S [CRT], puerto"
  - "inp (función)"
  - "inpd (función)"
  - "inpw (función)"
  - "puertos, E/S (rutinas)"
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _inp, _inpw, _inpd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica, desde un puerto, un byte \(`_inp`\), una palabra \(`_inpw`\) o una palabra doble \(`_inpd`\).  
  
> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### Parámetros  
 `port`  
 Número de puerto de E\/S.  
  
## Valor devuelto  
 Las funciones devuelven el byte, la palabra o la palabra doble leída en `port`. No se devuelve ningún error.  
  
## Comentarios  
 Las funciones `_inp`, `_inpw` y `_inpd` leen un byte, una palabra y una palabra doble, respectivamente, del puerto de conexión especificado. El valor de entrada puede ser cualquier entero corto sin signo del intervalo comprendido entre 0 y 65.535.  
  
 Dado que estas funciones leen directamente desde un puerto de E\/S, no se pueden usar en código de usuario en Windows NT, Windows 2000, Windows XP y Windows Server 2003.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_inp`|\<conio.h\>|  
|`_inpw`|\<conio.h\>|  
|`_inpd`|\<conio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)   
 [\_outp, \_outpw, \_outpd](../c-runtime-library/outp-outpw-outpd.md)