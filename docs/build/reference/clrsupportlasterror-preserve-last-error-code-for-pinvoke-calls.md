---
title: /CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 19930591c2d0406c68b1a408622a49c9e8b1d551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322272"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)

**/CLRSUPPORTLASTERROR**, que está activado de forma predeterminada, conserva el último código de error de las funciones a las que se llama a través del mecanismo P/Invoke, que permite llamar a funciones nativas en DLL, desde código compilado con **/clr**.

## <a name="syntax"></a>Sintaxis

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Observaciones

Conservar el último código de error implica una disminución en el rendimiento.  Si no desea incurrir en el impacto en el rendimiento de conservar el último código de error, vincule con **/CLRSUPPORTLASTERROR:NO**.

Puede minimizar el impacto en el rendimiento mediante la vinculación con **/CLRSUPPORTLASTERROR:SYSTEMDLL**, que solo conserva el último código de error para las funciones de los archivos DLL del sistema.  Un archivo DLL del sistema se define como uno de los siguientes:

|||||
|-|-|-|-|
|ACLUI. Dll|ACTIVEDS. Dll|ADPTIF. Dll|ADVAPI32. Dll|
|ASYCFILT. Dll|AUTHZ. Dll|AVICAP32. Dll|AVIFIL32. Dll|
|Gabinete. Dll|CLUSAPI. Dll|Comctl32. Dll|Comdlg32. Dll|
|COMSVCS. Dll|CREDUI. Dll|CRYPT32. Dll|CRYPTNET. Dll|
|CRYPTUI. Dll|D3D8THK. Dll|Dbgeng. Dll|DBGHELP. Dll|
|DCIMAN32. Dll|DNSAPI. Dll|DSPROP. Dll|DSUIEXT. Dll|
|GDI32. Dll|GLU32. Dll|HLINK. Dll|ICM32. Dll|
|IMAGEHLP. Dll|IMM32. Dll|IPHLPAPI. Dll|IPROP. Dll|
|KERNEL32. Dll|KSUSER. Dll|LOADPERF. Dll|LZ32. Dll|
|MAPI32. Dll|MGMTAPI. Dll|Mobsync. Dll|Mpr. Dll|
|MPRAPI. Dll|MQRT. Dll|MSACM32. Dll|MSCMS. Dll|
|Msi. Dll|MSIMG32. Dll|MSRATING. Dll|MSTASK. Dll|
|MSVFW32. Dll|MSWSOCK. Dll|MTXEX. Dll|NDDEAPI. Dll|
|NETAPI32. Dll|NPPTOOLS. Dll|NTDSAPI. Dll|NTDSBCLI. Dll|
|NTMSAPI. Dll|ODBC32. Dll|ODBCBCP. Dll|OLE32. Dll|
|OLEACC. Dll|OLEAUT32. Dll|OLEDLG. Dll|OPENGL32. Dll|
|Pdh. Dll|Powrprof. Dll|QOSNAME. Dll|Consulta. Dll|
|RASAPI32. Dll|RASDLG. Dll|RASSAPI. Dll|RESUTILS. Dll|
|RICHED20. Dll|RPCNS4. Dll|RPCRT4. Dll|Rtm. Dll|
|RTUTILS. Dll|SCARDDLG. Dll|SECUR32. Dll|SENSAPI. Dll|
|SETUPAPI. Dll|Sfc. Dll|SHELL32. Dll|SHFOLDER. Dll|
|Shlwapi. Dll|SISBKUP. Dll|SNMPAPI. Dll|SRCLIENT. Dll|
|Sti. Dll|TAPI32. Dll|Tráfico. Dll|Url. Dll|
|URLMON. Dll|USER32. Dll|USERENV. Dll|USP10. Dll|
|Uxtheme. Dll|VDMDBG. Dll|Versión. Dll|Winfax. Dll|
|WINHTTP. Dll|Wininet. Dll|WINMM. Dll|Winscard. Dll|
|Wintrust. Dll|WLDAP32. Dll|WOW32. Dll|WS2_32.DLL|
|WSNMP32. Dll|WSOCK32.DLL|WTSAPI32. Dll|XOLEHLP. Dll|

> [!NOTE]
> No se admite la conservación del último error para las funciones no administradas que consume el código CLR, en el mismo módulo.

- Para obtener más información, vea [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **Enlazador**.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el cuadro **Opciones adicionales.**

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se define un archivo DLL nativo con una función exportada que modifica el último error.

```cpp
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

En el ejemplo siguiente se consume el archivo DLL, lo que muestra cómo utilizar **/CLRSUPPORTLASTERROR**.

```cpp
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

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones de MSVC Linker](linker-options.md)
