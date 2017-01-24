---
title: "_outp, _outpw, _outpd | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_outpd"
  - "_outp"
  - "_outpw"
apilocation: 
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_outpw"
  - "_outpd"
  - "_outp"
  - "outpd"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_outp (constante)"
  - "_outpd (constante)"
  - "_outpw (constante)"
  - "bytes, escribir en puertos"
  - "palabras dobles"
  - "palabras dobles, escribir en puertos"
  - "outp (función)"
  - "outpd (función)"
  - "outpw (función)"
  - "puertos, escribir bytes en"
  - "palabras"
  - "palabras, escribir en puertos"
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _outp, _outpw, _outpd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera, en un puerto, un byte \(`_outp`\), una palabra \(`_outpw`\) o a una palabra doble \(`_outpd`\).  
  
> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
  
int _outp(unsigned short port,int databyte);unsigned short _outpw(unsigned short port,unsigned short dataword);unsigned long _outpd(unsigned short port,unsigned long dataword);  
```  
  
#### Parámetros  
 *puerto*  
 Número de puerto.  
  
 *databyte, dataword*  
 Valores de salida.  
  
## Valor devuelto  
 Las funciones devuelven el resultado de datos. No se devuelve ningún error.  
  
## Comentarios  
 Las funciones `_outp`, `_outpw` y `_outpd` escriben un byte, una palabra y una palabra doble, respectivamente, en el puerto de salida especificado. El argumento de *port* puede ser cualquier entero sin signo del intervalo comprendido entre 0 y 65.535; *databyte* puede ser cualquier entero del intervalo comprendido entre 0 y 255; y *dataword* puede ser cualquier valor del intervalo de un entero, un entero corto sin signo y un entero largo sin signo.  
  
 Dado que estas funciones escriben directamente en un puerto de E\/S, no se pueden usar en código de usuario en Windows NT, Windows 2000, Windows XP y Windows Server 2003. Para obtener información sobre el uso de puertos de E\/S en estos sistemas operativos, busque “Comunicaciones serie en Win32” en MSDN.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_outp`|\<conio.h\>|  
|`_outpw`|\<conio.h\>|  
|`_outpd`|\<conio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).  
  
## Vea también  
 [E\/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)   
 [\_inp, \_inpw, \_inpd](../c-runtime-library/inp-inpw-inpd.md)