---
title: _CrtSetReportHook2, _CrtSetReportHookW2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17dc0fc97a46e6ce0b5bda68ec8adc6ef37c4218
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetreporthook2-crtsetreporthookw2"></a>_CrtSetReportHook2, _CrtSetReportHookW2

Instala o desinstala una función de generación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtSetReportHook2(
   int mode,
   _CRT_REPORT_HOOK pfnNewHook
);
int _CrtSetReportHookW2(
   int mode,
   _CRT_REPORT_HOOKW pfnNewHook
);
```

### <a name="parameters"></a>Parámetros

*mode*<br/>
La acción que se realizará: **_CRT_RPTHOOK_INSTALL** o **_CRT_RPTHOOK_REMOVE**.

*pfnNewHook*<br/>
Enlace de informe para instalar o quitar en la versión con caracteres anchos o estrechos caracteres de esta función.

## <a name="return-value"></a>Valor devuelto

-1 si se produce un error, con **EINVAL** o **ENOMEM** establecer; en caso contrario, devuelve el recuento de referencias de *pfnNewHook* después de la llamada.

## <a name="remarks"></a>Comentarios

**_CrtSetReportHook2** y **_CrtSetReportHookW2** permiten enlazar o desenlazar una función, mientras que [_CrtSetReportHook](crtsetreporthook.md) solo permite una función de enlace.

**_CrtSetReportHook2** o **_CrtSetReportHookW2** debe usarse en lugar de **_CrtSetReportHook** cuando se realiza la llamada de enlace en un archivo DLL y cuando se pueden cargar varias DLL y establecer sus propias funciones de enlace. En tales circunstancias, los archivos DLL se pueden descargar en un orden diferente al que se han cargado y la función de enlace puede dejarse apuntando a un archivo DLL descargado. Los resultados de la depuración bloquea el proceso si se han agregado las funciones de enlace con **_CrtSetReportHook**.

Cualquier enlazar las funciones agregadas con **_CrtSetReportHook** se denominan si no hay ningún enlace de funciones de agregan con **_CrtSetReportHook2** o **_CrtSetReportHookW2** o si todos los enlazar funciones de agregado con **_CrtSetReportHook2** y **_CrtSetReportHookW2** devolver **FALSE**.

Está disponible la versión con caracteres anchos de esta función. Las funciones de enlace de informe toman una cadena cuyo tipo (caracteres anchos o estrechos) debe coincidir con la versión de esta función que se usa. Use el prototipo de función siguiente con los enlaces de informe que se usan con la versión de caracteres anchos de dicha función:

```C
int YourReportHook( int reportType, wchar_t *message, int *returnValue );
```

Use el prototipo siguiente con los enlaces de informe de caracteres estrechos:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

Estas funciones validan sus parámetros. Si *modo* o **pfnNewNook** es válida, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devuelven -1.

> [!NOTE]
> Si la aplicación se compila con **/CLR** y la función de creación de informes se llama después de que la aplicación se ha cerrado principal, el CLR iniciará una excepción si la función de creación de informes llama a las funciones de CRT.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_CrtSetReportHook2**|\<crtdbg.h>|\<errno.h>|
|**_CrtSetReportHookW2**|\<crtdbg.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
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

### <a name="output"></a>Salida

```Output
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

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
