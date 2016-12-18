---
title: "_getdrives | Microsoft Docs"
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
  - "_getdrives"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "getdrives"
  - "_getdrives"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getdrives (función)"
  - "unidades de disco"
  - "getdrives (función)"
ms.assetid: 869bb51f-4209-4328-846e-3aadebaceb9c
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getdrives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve una máscara de bits que representa las unidades de disco disponibles actualmente.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned long _getdrives( void );  
```  
  
## Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es una máscara de bits que representa las unidades de disco disponibles actualmente.  La posición de bit 0 \(el bit menos significativo\) es la unidad A, la posición de bit 1 es la unidad B, la posición de bit 2 es la unidad C y así sucesivamente.  Si la función no se realiza correctamente, el valor devuelto es cero.  Para obtener información de errores extendida, realice una llamada a `GetLastError`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getdrives`|\<direct.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_getdrives.c  
// This program retrives and lists out  
// all the logical drives that are   
// currently mounted on the machine.  
  
#include <windows.h>  
#include <direct.h>  
#include <stdio.h>  
#include <tchar.h>  
  
TCHAR g_szDrvMsg[] = _T("A:\n");  
  
int main(int argc, char* argv[]) {  
   ULONG uDriveMask = _getdrives();  
  
   if (uDriveMask == 0)  
   {  
      printf( "_getdrives() failed with failure code: %d\n",  
              GetLastError());  
   }  
   else  
   {  
      printf("The following logical drives are being used:\n");  
  
      while (uDriveMask) {  
         if (uDriveMask & 1)  
            printf(g_szDrvMsg);  
  
         ++g_szDrvMsg[0];  
         uDriveMask >>= 1;  
      }  
   }  
}  
```  
  
  **Se utilizan las siguientes unidades lógicas:**  
**R:**  
**C:**  
**D:**  
**E:**   
## Equivalente de .NET Framework  
 No es aplicable.  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)