---
title: "_putch_nolock, _putwch_nolock | Microsoft Docs"
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
  - "_putwch_nolock"
  - "_putch_nolock"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_putch_nolock"
  - "_puttch_nolock"
  - "putch_nolock"
  - "putwch_nolock"
  - "_putwch_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putch_nolock (función)"
  - "_puttch_nolock (función)"
  - "_putwch_nolock (función)"
  - "caracteres, escribir"
  - "consola, escribir caracteres en"
  - "putch_nolock (función)"
  - "puttch_nolock (función)"
  - "putwch_nolock (función)"
ms.assetid: edbc811d-bac6-47fa-a872-fe4f3a1590b0
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putch_nolock, _putwch_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un carácter en la consola sin bloquear el subproceso.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
  
      int _putch_nolock(  
int c   
);  
wint_t _putwch_nolock(  
wchar_t c  
);  
```  
  
#### Parámetros  
 *c*  
 Carácter que se va a generar.  
  
## Valor devuelto  
 Si la operación se realiza correctamente, devuelve *c*.  Si **\_putch\_nolock** produce un error, devuelve **EOF**; si **\_putwch\_nolock** produce un error, devuelve **WEOF**.  
  
## Comentarios  
 **\_putch\_nolock** y **\_putwch\_nolock** son exactamente igual que **\_putch** y **\_putwch**, respectivamente, salvo que no están protegidas contra interferencias de otros subprocesos.  Pueden ser más rápidas porque no incurren en la sobrecarga de bloquear otros subprocesos.  Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|**\_puttch\_nolock**|**\_putch\_nolock**|**\_putch\_nolock**|**\_putwch\_nolock**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**\_putch\_nolock**|\<conio.h\>|  
|**\_putwch\_nolock**|\<conio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [\_getch, \_getwch](../../c-runtime-library/reference/getch-getwch.md)