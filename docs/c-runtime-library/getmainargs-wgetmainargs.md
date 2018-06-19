---
title: __getmainargs, __wgetmainargs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
dev_langs:
- C++
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13707791b78de2c000535d60ed3f298046e4576c
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451291"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs
Invoca al análisis de línea de comandos y vuelve a copiar los argumentos en `main()` mediante los punteros que se pasan.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `_Argc`  
 Un entero que contiene el número de argumentos que aparecen detrás de `argv`. El parámetro `argc` es siempre mayor o igual que 1.  
  
 `_Argv`  
 Una matriz de cadenas terminadas en null que representan los argumentos de la línea de comandos especificados por el usuario del programa. Por convención, `argv[0]` es el comando con el que se invoca el programa, argv[1] es el primer argumento de la línea de comandos, y así sucesivamente, hasta argv[argc], que siempre es **NULL**. El primer argumento de la línea de comandos siempre es `argv[1]` y el último es `argv[argc - 1]`.  
  
 `_Env`  
 Una matriz de cadenas que representan las variables establecidas en el entorno del usuario. Esta matriz termina con una entrada **NULL**.  
  
 `_DoWildCard`  
 Un entero que si se establece en 1 expande los caracteres comodín en los argumentos de línea de comandos y si se establece en 0 no hace nada.  
  
 `_StartInfo`  
 Otra información que se pasa al archivo DLL de CRT.  
  
## <a name="return-value"></a>Valor devuelto  
 0 si es correcto; un valor negativo si no lo es.  
  
## <a name="remarks"></a>Comentarios  
 Use `__getmainargs` en plataformas de caracteres no anchos y `__wgetmainargs` en plataformas de caracteres anchos (Unicode).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|__getmainargs|internal.h|  
|__wgetmainargs|internal.h|