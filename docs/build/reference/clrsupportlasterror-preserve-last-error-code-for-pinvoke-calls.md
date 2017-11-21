---
title: "-CLRSUPPORTLASTERROR (conservar último código de Error para las llamadas a PInvoke) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRSUPPORTLASTERROR
dev_langs: C++
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23f8215e94139417c6bd098b669904783fb88b36
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)
**/CLRSUPPORTLASTERROR**, que está activado de forma predeterminada, conserva el último código de error de funciones que se llama mediante el mecanismo P/Invoke, que le permite llamar a funciones nativas en archivos DLL, desde el código compilado con **/CLR**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}  
```  
  
## <a name="remarks"></a>Comentarios  
 Conservar el último código de error implica una disminución del rendimiento.  Si no desea incurrir en el impacto de rendimiento de conservar el último código de error, vincule con **/CLRSUPPORTLASTERROR:NO**.  
  
 Puede minimizar el impacto de rendimiento mediante la vinculación con **/CLRSUPPORTLASTERROR:SYSTEMDLL**, que solo conserva el último código de error para las funciones en archivos DLL del sistema.  Una DLL del sistema se define como uno de los siguientes:  
  
|||||  
|-|-|-|-|  
|EL ARCHIVO ACLUI. ARCHIVO DLL|ACTIVEDS. ARCHIVO DLL|ADPTIF. ARCHIVO DLL|ADVAPI32. ARCHIVO DLL|  
|ASYCFILT. ARCHIVO DLL|AUTHZ. ARCHIVO DLL|AVICAP32. ARCHIVO DLL|AVIFIL32. ARCHIVO DLL|  
|ARCHIVO. CAB. ARCHIVO DLL|CLUSAPI. ARCHIVO DLL|COMCTL32. ARCHIVO DLL|ARCHIVO COMDLG32. ARCHIVO DLL|  
|COMSVCS. ARCHIVO DLL|CREDUI. ARCHIVO DLL|CRYPT32. ARCHIVO DLL|CRYPTNET. ARCHIVO DLL|  
|CRYPTUI. ARCHIVO DLL|D3D8THK. ARCHIVO DLL|DBGENG. ARCHIVO DLL|DBGHELP. ARCHIVO DLL|  
|DCIMAN32. ARCHIVO DLL|DNSAPI. ARCHIVO DLL|DSPROP. ARCHIVO DLL|DSUIEXT. ARCHIVO DLL|  
|GDI32. ARCHIVO DLL|GLU32. ARCHIVO DLL|HLINK. ARCHIVO DLL|ICM32. ARCHIVO DLL|  
|IMAGEHLP. ARCHIVO DLL|IMM32. ARCHIVO DLL|IPHLPAPI. ARCHIVO DLL|IPROP. ARCHIVO DLL|  
|KERNEL32. ARCHIVO DLL|KSUSER. ARCHIVO DLL|LOADPERF. ARCHIVO DLL|LZ32. ARCHIVO DLL|  
|MAPI32. ARCHIVO DLL|BIBLIOTECA MGMTAPI. ARCHIVO DLL|MOBSYNC. ARCHIVO DLL|MPR. ARCHIVO DLL|  
|MPRAPI. ARCHIVO DLL|MQRT. ARCHIVO DLL|MSACM32. ARCHIVO DLL|MSCMS. ARCHIVO DLL|  
|MSI. ARCHIVO DLL|MSIMG32. ARCHIVO DLL|MSRATING. ARCHIVO DLL|MSTASK. ARCHIVO DLL|  
|MSVFW32. ARCHIVO DLL|MSWSOCK. ARCHIVO DLL|MTXEX. ARCHIVO DLL|NDDEAPI. ARCHIVO DLL|  
|NETAPI32. ARCHIVO DLL|NPPTOOLS. ARCHIVO DLL|NTDSAPI. ARCHIVO DLL|NTDSBCLI. ARCHIVO DLL|  
|NTMSAPI. ARCHIVO DLL|ODBC32. ARCHIVO DLL|ODBCBCP. ARCHIVO DLL|OLE32. ARCHIVO DLL|  
|OLEACC. ARCHIVO DLL|OLEAUT32. ARCHIVO DLL|OLEDLG. ARCHIVO DLL|OPENGL32. ARCHIVO DLL|  
|PDH. ARCHIVO DLL|POWRPROF. ARCHIVO DLL|QOSNAME. ARCHIVO DLL|CONSULTA. ARCHIVO DLL|  
|RASAPI32. ARCHIVO DLL|RASDLG. ARCHIVO DLL|RASSAPI. ARCHIVO DLL|RESUTILS. ARCHIVO DLL|  
|RICHED20. ARCHIVO DLL|RPCNS4. ARCHIVO DLL|RPCRT4. ARCHIVO DLL|RTM. ARCHIVO DLL|  
|RTUTILS. ARCHIVO DLL|SCARDDLG. ARCHIVO DLL|SECUR32. ARCHIVO DLL|SENSAPI. ARCHIVO DLL|  
|SETUPAPI. ARCHIVO DLL|SFC. ARCHIVO DLL|SHELL32. ARCHIVO DLL|SHFOLDER. ARCHIVO DLL|  
|SHLWAPI. ARCHIVO DLL|SISBKUP. ARCHIVO DLL|SNMPAPI. ARCHIVO DLL|SRCLIENT. ARCHIVO DLL|  
|STI. ARCHIVO DLL|TAPI32. ARCHIVO DLL|TRÁFICO. ARCHIVO DLL|DIRECCIÓN URL. ARCHIVO DLL|  
|URLMON. ARCHIVO DLL|USER32. ARCHIVO DLL|USERENV. ARCHIVO DLL|USP10. ARCHIVO DLL|  
|UXTHEME. ARCHIVO DLL|VDMDBG. ARCHIVO DLL|VERSIÓN. ARCHIVO DLL|WINFAX. ARCHIVO DLL|  
|WINHTTP. ARCHIVO DLL|WININET. ARCHIVO DLL|WINMM. ARCHIVO DLL|WINSCARD. ARCHIVO DLL|  
|WINTRUST. ARCHIVO DLL|WLDAP32. ARCHIVO DLL|WOW32. ARCHIVO DLL|WS2_32.DLL|  
|WSNMP32. ARCHIVO DLL|WSOCK32.DLL|WTSAPI32. ARCHIVO DLL|XOLEHLP. ARCHIVO DLL|  
  
> [!NOTE]
>  Conservar el último error no se admite para las funciones no administradas que son consumidas por código CLR, en el mismo módulo.  
  
-   Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción en la **opciones adicionales** cuadro.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente define un archivo DLL nativo con una función exportada que modifica el último error.  
  
```  
// CLRSUPPORTLASTERROR_dll.cpp  
// compile with: /LD  
#include <windows.h>  
#include <math.h>  
  
#pragma unmanaged  
__declspec(dllexport) double MySqrt(__int64 n) {  
   SetLastError(DWORD(-1));  
   return sqrt(double(n));  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente utiliza el archivo DLL, que muestra cómo usar **/CLRSUPPORTLASTERROR**.  
  
```  
// CLRSUPPORTLASTERROR_client.cpp  
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll  
// processor: x86  
#include <windows.h>  
#include <wininet.h>  
#include <stdio.h>  
#include <math.h>  
  
#pragma comment(lib, "wininet.lib")  
  
double MySqrt(__int64 n);  
  
#pragma managed  
int main() {  
   double   d = 0.0;  
   __int64 n = 65;  
   HANDLE  hGroup = NULL;  
   GROUPID groupID;  
   DWORD   dwSet = 127, dwGet = 37;  
  
   SetLastError(dwSet);  
   d = MySqrt(n);  
   dwGet = GetLastError();  
  
   if (dwGet == DWORD(-1))  
      printf_s("GetLastError for application call succeeded (%d).\n",  
             dwGet);  
   else  
      printf_s("GetLastError for application call failed (%d).\n",  
             dwGet);  
  
   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,  
                           0, 0, &groupID, 0);  
   dwGet = GetLastError();  
   if (dwGet == 183)  
      printf_s("GetLastError for system call succeeded (%d).\n",  
             dwGet);  
   else  
      printf_s("GetLastError for system call failed (%d).\n",  
             dwGet);  
}  
```  
  
```Output  
GetLastError for application call failed (127).  
GetLastError for system call succeeded (183).  
```  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)