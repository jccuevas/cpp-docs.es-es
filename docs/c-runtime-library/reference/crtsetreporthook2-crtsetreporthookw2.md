---
title: _CrtSetReportHook2, _CrtSetReportHookW2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetReportHook2
- _CrtSetReportHookW2
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CrtSetReportHookW2
- CrtSetReportHook2
- _CrtSetReportHookW2
- _CrtSetReportHook2
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportHook2 function
- _CrtSetReportHook2 function
- _CrtSetReportHookW2 function
- CrtSetReportHookW2 function
ms.assetid: 12e5f68d-c8a7-4b1a-9a75-72ba4a8592d0
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4f449a335eebc54fbfaf18ab94c853bb93a87cea
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="crtsetreporthook2-crtsetreporthookw2"></a>_CrtSetReportHook2, _CrtSetReportHookW2
Instala o desinstala una función de generación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `mode`  
 Acción que se va a realizar: `_CRT_RPTHOOK_INSTALL` o `_CRT_RPTHOOK_REMOVE`.  
  
 `pfnNewHook`  
 Enlace de informe que se instala o quita en la versión de caracteres estrechos de esta función.  
  
 `pfnNewHook`  
 Enlace de informe que se instala o quita en la versión de caracteres anchos de esta función.  
  
## <a name="return-value"></a>Valor devuelto  
 -1 si se produce un error, con `EINVAL` o `ENOMEM` establecida; de lo contrario, devuelve el recuento de referencias de `pfnNewHook` después de la llamada.  
  
## <a name="remarks"></a>Comentarios  
 `_CrtSetReportHook2` y `_CrtSetReportHookW2` le permiten enlazar o desenlazar una función, mientras que [_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md) solo permite enlazar una función.  
  
 Deben usarse `_CrtSetReportHook2` o `_CrtSetReportHookW2` en lugar de `_CrtSetReportHook` cuando la llamada al enlace se efectúa en un archivo DLL y cuando es posible que haya varios archivos DLL cargados que establezcan sus propias funciones de enlace. En tales circunstancias, los archivos DLL se pueden descargar en un orden diferente al que se han cargado y la función de enlace puede dejarse apuntando a un archivo DLL descargado. Los resultados de la depuración bloquean el proceso si las funciones de enlace se han agregado con `_CrtSetReportHook`.  
  
 Las funciones de enlace agregadas con `_CrtSetReportHook` se llaman si no se ha agregado ninguna función de enlace con `_CrtSetReportHook2` o `_CrtSetReportHookW2`, o si todas las funciones de enlace que se han agregado con `_CrtSetReportHook2` y `_CrtSetReportHookW2` devuelven `FALSE`.  
  
 Está disponible la versión con caracteres anchos de esta función. Las funciones de enlace de informe toman una cadena cuyo tipo (caracteres anchos o estrechos) debe coincidir con la versión de esta función que se usa. Use el prototipo de función siguiente con los enlaces de informe que se usan con la versión de caracteres anchos de dicha función:  
  
```  
int YourReportHook( int reportType, wchar_t *message, int *returnValue );  
```  
  
 Use el prototipo siguiente con los enlaces de informe de caracteres estrechos:  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 Estas funciones validan sus parámetros. Si `mode` o `pfnNewNook` no es válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven -1.  
  
> [!NOTE]
>  Si la aplicación se compila con `/clr` y se llama a la función de creación de informes una vez que la aplicación se ha cerrado, CLR inicia una excepción si la función de creación de informes llama a cualquier función de CRT.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportHook2`|\<crtdbg.h>|\<errno.h>|  
|`_CrtSetReportHookW2`|\<crtdbg.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="output"></a>Salida  
  
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
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
