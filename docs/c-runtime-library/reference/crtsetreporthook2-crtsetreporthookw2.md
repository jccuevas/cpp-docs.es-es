---
title: "_CrtSetReportHook2, _CrtSetReportHookW2 | Microsoft Docs"
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
  - "_CrtSetReportHook2"
  - "_CrtSetReportHookW2"
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
  - "CrtSetReportHookW2"
  - "CrtSetReportHook2"
  - "_CrtSetReportHookW2"
  - "_CrtSetReportHook2"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtSetReportHook2 (función)"
  - "_CrtSetReportHook2 (función)"
  - "_CrtSetReportHookW2 (función)"
  - "CrtSetReportHookW2 (función)"
ms.assetid: 12e5f68d-c8a7-4b1a-9a75-72ba4a8592d0
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetReportHook2, _CrtSetReportHookW2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las instalaciones o por una función cliente\- definido de informe enlazandola en el proceso de informe de depuración en tiempo de ejecución de C \(versión de depuración solo\).  
  
## Sintaxis  
  
```  
  
      int _CrtSetReportHook2(  
   int mode,  
   _CRT_REPORT_HOOK pfnNewHook  
);  
int _CrtSetReportHookW2(  
   int mode,  
   _CRT_REPORT_HOOKW pfnNewHook  
);  
```  
  
#### Parámetros  
 `mode`  
 La acción a realizar: `_CRT_RPTHOOK_INSTALL` o `_CRT_RPTHOOK_REMOVE`.  
  
 `pfnNewHook`  
 Seleccione el enlace para instalar o quitar en la versión de estrecho\- carácter de esta función.  
  
 `pfnNewHook`  
 Seleccione el enlace para instalar o quitar en la versión de caracteres anchos de esta función.  
  
## Valor devuelto  
 \-1 si se encontró un error, con `EINVAL` o `ENOMEM` establezca; si no devuelve el recuento de referencias de `pfnNewHook` después de la llamada.  
  
## Comentarios  
 `_CrtSetReportHook2` y `_CrtSetReportHookW2` permiten enlace o zafan una función, mientras que [\_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md) permite solo enlace una función.  
  
 `_CrtSetReportHook2` o `_CrtSetReportHookW2` debe utilizarse en lugar de `_CrtSetReportHook` cuando la llamada de enlace se hace en un archivo DLL y cuando varias DLL pueden cargar y estableciendo su propio enlace funciona.  En esta situación, los archivos DLL se puede descargar en un orden diferente que se cargaron y la función de enlace puede quedarse informar de DLL descargado.  Los bloqueos de la depuración el proceso si las funciones de enlace se agregaron con `_CrtSetReportHook`.  
  
 Cualquier función de enlace agregada con `_CrtSetReportHook` se denomina si no hay funciones de enlace agregadas con `_CrtSetReportHook2` o `_CrtSetReportHookW2` o si todas las funciones de enlace agregadas con `_CrtSetReportHook2` y `_CrtSetReportHookW2` devuelven `FALSE`.  
  
 La versión de caracteres anchos de esta función está disponible.  Las funciones de enlace de informe tienen una cadena cuyo tipo \(caracteres anchos o restringidos\) coincida con la versión de esta función utilizada.  Utilice el siguiente prototipo de función por vínculos de informe utilizados con la versión de caracteres anchos de esta función:  
  
```  
int YourReportHook( int reportType, wchar_t *message, int *returnValue );  
```  
  
 Utilice el siguiente prototipo por vínculos de informe de estrecho\- carácter:  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 Estas funciones validan sus parámetros.  Si `mode` o `pfnNewNook` no es válido, estas funciones se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  
  
> [!NOTE]
>  Si la aplicación se compila con `/clr` y se llama a la función de creación de informes una vez que la aplicación se ha cerrado, CLR inicia una excepción si la función de creación de informes llama a cualquier función de CRT.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_CrtSetReportHook2`|\<crtdbg.h\>|\<errno.h\>|  
|`_CrtSetReportHookW2`|\<crtdbg.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_setreporthook2.c  
#include <windows.h>  
#include <stdio.h>  
#include <crtdbg.h>  
#include <assert.h>  
  
int __cdecl TestHook1(int nReportType, char* szMsg, int* pnRet)  
{  
   int nRet = FALSE;  
  
   printf("CRT report hook 1.\n");  
   printf("CRT report type is \"");  
   switch (nReportType)  
   {  
      case _CRT_ASSERT:  
      {  
         printf("_CRT_ASSERT");  
         // nRet = TRUE;   // Always stop for this type of report  
         break;  
      }  
  
      case _CRT_WARN:  
      {  
         printf("_CRT_WARN");  
         break;  
      }  
  
      case _CRT_ERROR:  
      {  
         printf("_CRT_ERROR");  
         break;  
      }  
  
      default:  
      {  
         printf("???Unknown???");  
         break;  
      }  
   }  
  
   printf("\".\nCRT report message is:\n\t");  
   printf(szMsg);  
  
   if   (pnRet)  
      *pnRet = 0;  
  
   return   nRet;  
}  
  
int __cdecl   TestHook2(int nReportType, char* szMsg, int* pnRet)  
{  
   int   nRet = FALSE;  
  
   printf("CRT report hook 2.\n");  
   printf("CRT report type is \"");  
   switch   (nReportType)  
   {  
      case _CRT_WARN:  
      {  
         printf("_CRT_WARN");  
         break;  
      }  
  
      case _CRT_ERROR:  
      {  
         printf("_CRT_ERROR");  
         break;  
      }  
  
      case _CRT_ASSERT:  
      {  
         printf("_CRT_ASSERT");  
         nRet = TRUE;   // Always stop for this type of report  
         break;  
      }  
  
      default:  
      {  
         printf("???Unknown???");  
         break;  
      }  
   }  
  
   printf("\".\nCRT report message is: \t");  
   printf(szMsg);  
  
   if   (pnRet)  
      *pnRet = 0;  
   // printf("CRT report code is %d.\n", *pnRet);  
   return   nRet;  
}  
  
int   main(int argc, char* argv[])  
{  
   int   nRet = 0;  
  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1)"  
          " returned %d\n", nRet);  
  
   _ASSERT(0);  
  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2)"  
          " returned %d\n", nRet);  
   nRet = _CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1);  
   printf("_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1)"  
          " returned %d\n", nRet);  
  
   return   nRet;  
}  
```  
  
## Resultados  
  
```  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_INSTALL, TestHook1) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook2) returned 0  
_CrtSetReportHook2(_CRT_RPTHOOK_REMOVE, TestHook1) returned 0  
```  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)