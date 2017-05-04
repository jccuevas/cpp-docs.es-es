---
title: "Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 15
---
# Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows
Muchas funciones de runtime de C \(CRT\) no están disponibles al compilar las aplicaciones de Plataforma universal de Windows \(UWP\). En algunos casos, hay soluciones alternativas disponibles; por ejemplo, puede usar [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] o las API de Win32. Sin embargo, en otros casos, se han prohibido las funciones de CRT porque las características que les corresponden o las API auxiliares no son aplicables a las aplicaciones UWP.  
  
 En la tabla siguiente se muestran las funciones de CRT que no están disponibles al compilar aplicaciones UWP y se indican las soluciones alternativas que se aplican.  
  
## Funciones CRT no admitidas  
  
||||  
|-|-|-|  
|\_beep \_sleep \_seterrormode|Estas funciones eran obsoletas en las versiones anteriores de CRT. Además, las API de Win32 correspondientes no están disponibles para las aplicaciones UWP.|Ninguna solución alternativa.|  
|chdir \_chdrive getcwd|Estas funciones están obsoletas o no son seguras para subprocesos.|Use \_chdir, \_getcwd y funciones relacionados.|  
|\_cgets \_cgets\_s \_cgetws \_cgetws\_s \_cprintf \_cprintf\_l \_cprintf\_p \_cprintf\_p\_l \_cprintf\_s \_cprintf\_s\_l \_cputs \_cputws \_cscanf \_cscanf\_l \_cscanf\_s \_cscanf\_s\_l \_cwait \_cwprintf \_cwprintf\_l \_cwprintf\_p \_cwprintf\_p\_l \_cwprintf\_s \_cwprintf\_s\_l \_cwscanf \_cwscanf\_l \_cwscanf\_s \_cwscanf\_s\_l \_vcprintf \_vcprintf\_l \_vcprintf\_p \_vcprintf\_p\_l \_vcprintf\_s \_vcprintf\_s\_l \_vcwprintf \_vcwprintf\_l \_vcwprintf\_p \_vcwprintf\_p\_l \_vcwprintf\_s \_vcwprintf\_s\_l \_getch \_getch\_nolock \_getche \_getche\_nolock \_getwch \_getwch\_nolock \_getwche \_getwche\_nolock \_putch \_putch\_nolock \_putwch \_putwch\_nolock \_ungetch \_ungetch\_nolock \_ungetwch \_ungetwch\_nolock \_kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|Estas funciones se usan para leer y escribir directamente en la consola o desde ella. Las aplicaciones UWP son solo GUI; no admiten la consola.|Ninguna solución alternativa.|  
|getpid|Esta función está obsoleta.|Use \_getpid o la API de Win32 `GetCurrentProcessId()`.|  
|\_getdiskfree|No está disponible.|Use la API de Win32 `GetDiskFreeSpaceExW()`.|  
|\_getdrive \_getdrives|La API correspondiente no está disponible para las aplicaciones UWP.|Ninguna solución alternativa.|  
|\_inp \_inpd \_inpw \_outp \_outpd \_outpw inp inpd inpw outp outpd outpw|No se admite la E\/S de puerto en las aplicaciones UWP.|Ninguna solución alternativa.|  
|\_ismbcalnum \_ismbcalnum\_l \_ismbcalpha \_ismbcalpha\_l \_ismbcdigit \_ismbcdigit\_l \_ismbcgraph \_ismbcgraph\_l \_ismbchira \_ismbchira\_l \_ismbckata \_ismbckata\_l \_ismbcl0 \_ismbcl0\_l \_ismbcl1 \_ismbcl1\_l \_ismbcl2 \_ismbcl2\_l \_ismbclegal \_ismbclegal\_l \_ismbclower \_ismbclower\_l \_ismbcprint \_ismbcprint\_l \_ismbcpunct \_ismbcpunct\_l \_ismbcspace \_ismbcspace\_l \_ismbcsymbol \_ismbcsymbol\_l \_ismbcupper \_ismbcupper\_l \_mbbtombc \_mbbtombc\_l \_mbbtype \_mbbtype\_l \_mbccpy \_mbccpy\_l \_mbccpy\_s \_mbccpy\_s\_l \_mbcjistojms \_mbcjistojms\_l \_mbcjmstojis \_mbcjmstojis\_l \_mbclen \_mbclen\_l \_mbctohira \_mbctohira\_l \_mbctokata \_mbctokata\_l \_mbctolower \_mbctolower\_l \_mbctombb \_mbctombb\_l \_mbctoupper \_mbctoupper\_l \_mbsbtype \_mbsbtype\_l \_mbscat \_mbscat\_l \_mbscat\_s \_mbscat\_s\_l \_mbschr \_mbschr\_l \_mbscmp \_mbscmp\_l \_mbscoll \_mbscoll\_l \_mbscpy \_mbscpy\_l \_mbscpy\_s \_mbscpy\_s\_l \_mbscspn \_mbscspn\_l \_mbsdec \_mbsdec\_l \_mbsicmp \_mbsicmp\_l \_mbsicoll \_mbsicoll\_l \_mbsinc \_mbsinc\_l \_mbslen \_mbslen\_l \_mbslwr \_mbslwr\_l \_mbslwr\_s \_mbslwr\_s\_l \_mbsnbcat \_mbsnbcat\_l \_mbsnbcat\_s \_mbsnbcat\_s\_l \_mbsnbcmp \_mbsnbcmp\_l \_mbsnbcnt \_mbsnbcnt\_l \_mbsnbcoll \_mbsnbcoll\_l \_mbsnbcpy \_mbsnbcpy\_l \_mbsnbcpy\_s \_mbsnbcpy\_s\_l \_mbsnbicmp \_mbsnbicmp\_l \_mbsnbicoll \_mbsnbicoll\_l \_mbsnbset \_mbsnbset\_l \_mbsnbset\_s \_mbsnbset\_s\_l \_mbsncat \_mbsncat\_l \_mbsncat\_s \_mbsncat\_s\_l \_mbsnccnt \_mbsnccnt\_l \_mbsncmp \_mbsncmp\_l \_mbsncoll \_mbsncoll\_l \_mbsncpy \_mbsncpy\_l \_mbsncpy\_s \_mbsncpy\_s\_l \_mbsnextc \_mbsnextc\_l \_mbsnicmp \_mbsnicmp\_l \_mbsnicoll \_mbsnicoll\_l \_mbsninc \_mbsninc\_l \_mbsnlen \_mbsnlen\_l \_mbsnset \_mbsnset\_l \_mbsnset\_s \_mbsnset\_s\_l \_mbspbrk \_mbspbrk\_l \_mbsrchr \_mbsrchr\_l \_mbsrev \_mbsrev\_l \_mbsset \_mbsset\_l \_mbsset\_s \_mbsset\_s\_l \_mbsspn \_mbsspn\_l \_mbsspnp \_mbsspnp\_l \_mbsstr \_mbsstr\_l \_mbstok \_mbstok\_l \_mbstok\_s \_mbstok\_s\_l \_mbsupr \_mbsupr\_l \_mbsupr\_s \_mbsupr\_s\_l is\_wctype|Las cadenas de varios bytes no se admiten en las aplicaciones UWP.|Use las cadenas Unicode en su lugar.|  
|\_pclose \_pipe \_popen \_wpopen|La funcionalidad de canalización no está disponible para aplicaciones UWP.|Ninguna solución alternativa.|  
|\_resetstkoflw|Las API de Win32 auxiliares no están disponibles para las aplicaciones UWP.|Ninguna solución alternativa.|  
|\_getsystime \_setsystime|Se trataba de API obsoletas en versiones anteriores de CRT. Además, un usuario no puede establecer la hora del sistema en una aplicación UWP debido a la falta de permisos.|Para obtener solo la hora del sistema, use la API de Win32 `GetSystemTime`. No se puede establecer la hora del sistema.|  
|\_environ \_putenv \_putenv\_s \_searchenv \_searchenv\_s \_dupenv\_s \_wputenv \_wputenv\_s \_wsearchenv getenv getenv\_s putenv \_wdupenv\_s \_wenviron \_wgetenv \_wgetenv\_s \_wsearchenv\_s tzset|Las variables de entorno no están disponibles para aplicaciones UWP.|Ninguna solución alternativa. Para establecer la zona horaria, use \_tzset.|  
|\_loaddll \_getdllprocaddr \_unloaddll|Se trataba de funciones obsoletas en versiones anteriores de CRT. Además, el usuario no puede cargar DLL que no se encuentren en el mismo paquete de aplicación.|Utilice las API de Win32 `LoadPackagedLibrary`, `GetProcAddress` y `FreeLibrary` para cargar y usar DLL empaquetadas.|  
|\_wexecl \_wexecle \_wexeclp \_wexeclpe \_wexecv \_wexecve \_wexecvp \_wexecvpe \_execl \_execle \_execlp \_execlpe \_execv \_execve \_execvp \_execvpe \_spawnl \_spawnle \_spawnlp \_spawnlpe \_spawnv \_spawnve \_spawnvp \_spawnvpe \_wspawnl \_wspawnle \_wspawnlp \_wspawnlpe \_wspawnv \_wspawnve \_wspawnvp \_wspawnvpe \_wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|La funcionalidad no está disponible en aplicaciones UWP. Una aplicación UWP no puede invocar otra aplicación UWP o una aplicación de escritorio.|Ninguna solución alternativa.|  
|\_heapwalk \_heapadd \_heapchk \_heapset \_heapused|Estas funciones se suelen usar para trabajar con el montón. Sin embargo, no se admiten las API de Win32 correspondientes en aplicaciones de UWP. Además, las aplicaciones ya no pueden crear o usar montones privados.|Ninguna solución alternativa. Sin embargo, `_heapwalk` está disponible en el CRT de depuración, solo para fines de depuración. No se pueden usar en aplicaciones que se cargan en la Tienda Windows.|  
  
 Las funciones siguientes están disponibles en el CRT para aplicaciones UWP, pero solo deben usarse cuando no se puede usar las API de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] o Win32 correspondientes, por ejemplo, al portar código base de gran envergadura.  
  
|||  
|-|-|  
|Funciones de cadena de un solo byte, por ejemplo, `strcat`, `strcpy`, `strlwr` y así sucesivamente.|Haga que sus aplicaciones UWP sean estrictamente Unicode porque todas las API de Win32 y las API de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] que se exponen solo usan juegos de caracteres Unicode. Las funciones de un solo byte se han dejado para la portabilidad de código base de gran envergadura, pero deben evitarse de otro modo, y las funciones de carácter ancho correspondientes deben usarse en su lugar, cuando sea posible.|  
|Funciones de E\/S de archivo de nivel bajo y E\/S de secuencias, por ejemplo, `fopen`, `open` y así sucesivamente.|Estas funciones son sincrónicas, lo que no se recomienda para las aplicaciones UWP. En sus aplicaciones UWP, use las API asincrónicas para abrir archivos, leer desde ellos y escribir en ellos para evitar el bloqueo del subproceso de la interfaz de usuario. Ejemplos de estas API son las de la clase `Windows::Storage::FileIO`.|  
  
## Aplicaciones de la Tienda Windows 8.x y aplicaciones de Windows Phone 8.x  
 Además de las API mencionadas anteriormente, las siguientes API no están disponibles en las aplicaciones de la Tienda Windows 8.x y las aplicaciones de Windows Phone 8.x.  
  
||||  
|-|-|-|  
|\_beginthread \_beginthreadex \_endthread \_endthreadex|Las API de Win32 de subprocesos no están disponibles en las aplicaciones de la Tienda Windows 8.x.|Use `Windows Runtime Windows::System::Threading::ThreadPool` o `concurrency::task` en su lugar.|  
|\_chdir \_wchdir \_getcwd \_getdcwd \_wgetcwd \_wgetdcwd|El concepto de un directorio de trabajo no se aplica a aplicaciones de la Tienda Windows 8.x.|Use rutas de acceso completas en su lugar.|  
|\_getpid|Esta función era obsoleta en versiones anteriores de CRT.|Use la API de Win32 `GetCurrentProcessId()`.|  
|\_isleadbyte\_l \_ismbbalnum, \_ismbbalnum\_l, \_ismbbalpha, \_ismbbalpha \_ismbbalpha\_l \_ismbbgraph \_ismbbgraph\_l \_ismbbkalnum \_ismbbkalnum\_l \_ismbbkana \_ismbbkana\_l \_ismbbkprint \_ismbbkprint\_l \_ismbbkpunct \_ismbbkpunct\_l \_ismbblead \_ismbblead\_l \_ismbbprint \_ismbbprint\_l \_ismbbpunct \_ismbbpunct\_l \_ismbbtrail \_ismbbtrail\_l \_ismbslead \_ismbslead\_l \_ismbstrail \_ismbstrail\_l \_mbsdup isleadbyte|Las cadenas de varios bytes no se admiten en las aplicaciones de la Tienda Windows 8.x.|Use las cadenas Unicode en su lugar.|  
|\_tzset|Las variables de entorno no están disponibles para aplicaciones de la Tienda Windows 8.x.|Ninguna solución alternativa.|  
|\_get\_heap\_handle, \_heapmin|No se admiten las API de Win32 correspondientes en aplicaciones de la Tienda Windows 8.x. Además, las aplicaciones ya no pueden crear montones privados.|Ninguna solución alternativa. Sin embargo, `_get_heap_handle` está disponible en el CRT de depuración, solo para fines de depuración.|