---
title: "_putch, _putwch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putwch"
  - "_putch"
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
  - "_putch"
  - "putwch"
  - "_putwch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_putch (función)"
  - "_putwch (función)"
  - "caracteres, escribir"
  - "consola, escribir caracteres en"
  - "putch (función)"
  - "putwch (función)"
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _putch, _putwch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un carácter en la consola.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
  
      int _putch(  
int c   
);  
wint_t _putwch(  
   wchar_t c  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a generar.  
  
## Valor devuelto  
 Si la operación se realiza correctamente, devuelve `c`.  Si `_putch` produce un error, devuelve `EOF`; si **\_putwch** produce un error, devuelve **WEOF**.  
  
## Comentarios  
 Estas funciones escriben el carácter `c` directamente en la consola, sin almacenarlo en búfer.  En Windows NT, **\_putwch** escribe caracteres Unicode mediante la configuración regional actual de la consola.  
  
 Las versiones con el sufijo de **\_nolock** son idénticas, salvo que no están protegidas contra interferencias de otros subprocesos.  Para obtener más información, vea `_putch_nolock`, `_putwch_nolock`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|**\_puttch**|`_putch`|`_putch`|**\_putwch**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_putch`|\<conio.h\>|  
|**\_putwch**|\<conio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Vea el ejemplo de [\_getch](../../c-runtime-library/reference/getch-getwch.md).  
  
## Vea también  
 [E\/S de consola y de puerto](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [\_getch, \_getwch](../../c-runtime-library/reference/getch-getwch.md)