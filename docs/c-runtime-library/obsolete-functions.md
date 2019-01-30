---
title: Funciones obsoletas
ms.date: 11/04/2016
f1_keywords:
- is_wctype
- _loaddll
- _unloaddll
- _getdllprocaddr
- _seterrormode
- _beep
- _sleep
- _getsystime
- corecrt_wctype/is_wctype
- process/_loaddll
- process/_unloaddll
- process/_getdllprocaddr
- stdlib/_seterrormode
- stdlib/_beep
- stdlib/_sleep
- time/_getsystime
- time/_setsystime
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
ms.openlocfilehash: 2f42593620c3457694bd57ccdc5a90216b3a28f1
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893891"
---
# <a name="obsolete-functions"></a>Funciones obsoletas

Algunas funciones de biblioteca son obsoletas y tienen equivalentes más recientes. Se recomienda que las cambie a las versiones actualizadas. Otras funciones obsoletas se han quitado de CRT. En este tema se muestran las funciones desusadas como obsoletas y las funciones quitadas de una versión concreta de Visual Studio.

## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>En desuso como obsoleta en Visual Studio 2015

|Función obsoleta|Alternativa|
|-----------------------|-----------------|
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|
|`_loaddll`|[LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya), [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)o [LoadPackagedLibrary](/windows/desktop/api/winbase/nf-winbase-loadpackagedlibrary)|
|`_unloaddll`|[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)|
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|
|`_seterrormode`|[SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621)|
|`_beep`|[Beep](/windows/desktop/api/utilapiset/nf-utilapiset-beep)|
|`_sleep`|[Sleep](/windows/desktop/api/synchapi/nf-synchapi-sleep)|
|`_getsystime`|[GetLocalTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getlocaltime)|
|`_setsystime`|[SetLocalTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-setlocaltime)|

## <a name="removed-from-the-crt-in-visual-studio-2015"></a>Se ha quitado de CRT en Visual Studio 2015

|Función obsoleta|Alternativa|
|-----------------------|-----------------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|
|[gets, _getws](../c-runtime-library/gets-getws.md)|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|
|[_get_output_format](../c-runtime-library/get-output-format.md)|Ninguna|
|[_heapadd](../c-runtime-library/heapadd.md)|Ninguna|
|[_heapset](../c-runtime-library/heapset.md)|Ninguna|
|[inp, inpw](../c-runtime-library/inp-inpw.md)|Ninguna|
|[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)|Ninguna|
|[outp, outpw](../c-runtime-library/outp-outpw.md)|Ninguna|
|[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)|Ninguna|
|[_set_output_format](../c-runtime-library/set-output-format.md)|Ninguna|

## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>Se ha quitado de CRT en versiones anteriores de Visual Studio

[_lock](../c-runtime-library/lock.md)

[_unlock](../c-runtime-library/unlock.md)