---
title: Funciones de CRT no admitidas en aplicaciones de la plataforma Universal de Windows | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 1550dca016b765278f8f1fe7ed9d95c4bfd3932e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows
Muchas funciones de runtime de C (CRT) no están disponibles al compilar las aplicaciones de Plataforma universal de Windows (UWP). En algunos casos, existen soluciones alternativas:-por ejemplo, puede usar en tiempo de ejecución de Windows o las API de Win32. Sin embargo, en otros casos, se han prohibido las funciones de CRT porque las características que les corresponden o las API auxiliares no son aplicables a las aplicaciones UWP.  
  
 En la tabla siguiente se muestran las funciones de CRT que no están disponibles al compilar aplicaciones UWP y se indican las soluciones alternativas que se aplican.  
  
## <a name="unsupported-crt-functions"></a>Funciones CRT no admitidas  
  
||||  
|-|-|-|  
|_beep _sleep _seterrormode|Estas funciones eran obsoletas en las versiones anteriores de CRT. Además, las API de Win32 correspondientes no están disponibles para las aplicaciones UWP.|Ninguna solución alternativa.|  
|chdir _chdrive getcwd|Estas funciones están obsoletas o no son seguras para subprocesos.|Use _chdir, _getcwd y funciones relacionados.|  
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|Estas funciones se usan para leer y escribir directamente en la consola o desde ella. Las aplicaciones UWP son solo GUI; no admiten la consola.|Ninguna solución alternativa.|  
|getpid|Esta función está obsoleta.|Use _getpid o la API de Win32 `GetCurrentProcessId()`.|  
|_getdiskfree|No está disponible.|Use la API de Win32 `GetDiskFreeSpaceExW()`.|  
|_getdrive _getdrives|La API correspondiente no está disponible para las aplicaciones UWP.|Ninguna solución alternativa.|  
|_inp _inpd _inpw _outp _outpd _outpw inp inpd inpw outp outpd outpw|No se admite la E/S de puerto en las aplicaciones UWP.|Ninguna solución alternativa.|  
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset_l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|Las cadenas de varios bytes no se admiten en las aplicaciones UWP.|Use las cadenas Unicode en su lugar.|  
|_pclose _pipe _popen _wpopen|La funcionalidad de canalización no está disponible para aplicaciones UWP.|Ninguna solución alternativa.|  
|_resetstkoflw|Las API de Win32 auxiliares no están disponibles para las aplicaciones UWP.|Ninguna solución alternativa.|  
|_getsystime _setsystime|Se trataba de API obsoletas en versiones anteriores de CRT. Además, un usuario no puede establecer la hora del sistema en una aplicación UWP debido a la falta de permisos.|Para obtener solo la hora del sistema, use la API de Win32 `GetSystemTime`. No se puede establecer la hora del sistema.|  
|_environ _putenv _putenv_s _searchenv _searchenv_s _dupenv_s _wputenv _wputenv_s _wsearchenv getenv getenv_s putenv _wdupenv_s _wenviron _wgetenv _wgetenv_s _wsearchenv_s tzset|Las variables de entorno no están disponibles para aplicaciones UWP.|Ninguna solución alternativa. Para establecer la zona horaria, use _tzset.|  
|_loaddll _getdllprocaddr _unloaddll|Se trataba de funciones obsoletas en versiones anteriores de CRT. Además, el usuario no puede cargar DLL que no se encuentren en el mismo paquete de aplicación.|Utilice las API de Win32 `LoadPackagedLibrary`, `GetProcAddress`y `FreeLibrary` para cargar y usar DLL empaquetadas.|  
|_wexecl _wexecle _wexeclp _wexeclpe _wexecv _wexecve _wexecvp _wexecvpe _execl _execle _execlp _execlpe _execv _execve _execvp _execvpe _spawnl _spawnle _spawnlp _spawnlpe _spawnv _spawnve _spawnvp _spawnvpe _wspawnl _wspawnle _wspawnlp _wspawnlpe _wspawnv _wspawnve _wspawnvp _wspawnvpe _wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|La funcionalidad no está disponible en aplicaciones UWP. Una aplicación UWP no puede invocar otra aplicación UWP o una aplicación de escritorio.|Ninguna solución alternativa.|  
|_heapwalk _heapadd _heapchk _heapset _heapused|Estas funciones se suelen usar para trabajar con el montón. Sin embargo, no se admiten las API de Win32 correspondientes en aplicaciones de UWP. Además, las aplicaciones ya no pueden crear o usar montones privados.|Ninguna solución alternativa. Sin embargo, `_heapwalk` está disponible en el CRT de depuración, solo para fines de depuración. No se pueden usar en aplicaciones que se cargan en la Tienda Windows.|  
  
 Las funciones siguientes están disponibles en el CRT para aplicaciones UWP, pero debe utilizarse únicamente cuando no se puede usar el Win32 correspondientes o Windows Runtime APIs: por ejemplo, al portar grandes bases de códigos  
  
|||  
|-|-|  
|Funciones de cadena de un solo byte, por ejemplo, `strcat`, `strcpy`, `strlwr`y así sucesivamente.|Asegúrese de sus aplicaciones UWP sean estrictamente Unicode porque todas las API de Win32 y Windows en tiempo de ejecución APIs que se exponen usan solo de juegos de caracteres Unicode.  Las funciones de un solo byte se han dejado para la portabilidad de código base de gran envergadura, pero deben evitarse de otro modo, y las funciones de carácter ancho correspondientes deben usarse en su lugar, cuando sea posible.|  
|Funciones de E/S de archivo de nivel bajo y E/S de secuencias, por ejemplo, `fopen`, `open`y así sucesivamente.|Estas funciones son sincrónicas, lo que no se recomienda para las aplicaciones UWP. En sus aplicaciones UWP, use las API asincrónicas para abrir archivos, leer desde ellos y escribir en ellos para evitar el bloqueo del subproceso de la interfaz de usuario. Ejemplos de estas API son las de la clase `Windows::Storage::FileIO` .|  
  
## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Aplicaciones de la Tienda Windows 8.x y aplicaciones de Windows Phone 8.x  
 Además de las API mencionadas anteriormente, las siguientes API no están disponibles en las aplicaciones de la Tienda Windows 8.x y las aplicaciones de Windows Phone 8.x.  
  
||||  
|-|-|-|  
|_beginthread _beginthreadex _endthread _endthreadex|Las API de Win32 de subprocesos no están disponibles en las aplicaciones de la Tienda Windows 8.x.|Use `Windows Runtime Windows::System::Threading::ThreadPool` o `concurrency::task` en su lugar.|  
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|El concepto de un directorio de trabajo no se aplica a aplicaciones de la Tienda Windows 8.x.|Use rutas de acceso completas en su lugar.|  
|_getpid|Esta función era obsoleta en versiones anteriores de CRT.|Use la API de Win32 `GetCurrentProcessId()`.|  
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ismbblead_l _ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Las cadenas de varios bytes no se admiten en las aplicaciones de la Tienda Windows 8.x.|Use las cadenas Unicode en su lugar.|  
|_tzset|Las variables de entorno no están disponibles para aplicaciones de la Tienda Windows 8.x.|Ninguna solución alternativa.|  
|_get_heap_handle, _heapmin|No se admiten las API de Win32 correspondientes en aplicaciones de la Tienda Windows 8.x. Además, las aplicaciones ya no pueden crear montones privados.|Ninguna solución alternativa. Sin embargo, `_get_heap_handle` está disponible en el CRT de depuración, solo para fines de depuración.|