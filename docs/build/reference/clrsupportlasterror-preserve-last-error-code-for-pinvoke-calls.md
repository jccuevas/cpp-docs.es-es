---
title: /CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 64948d81759d415245e741bc6152d56bb35480d2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988351"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)

**/CLRSUPPORTLASTERROR**, que está activada de forma predeterminada, conserva el último código de error de las funciones llamadas a través del mecanismo P/Invoke, que permite llamar a funciones nativas en archivos dll, desde el código compilado con **/CLR**.

## <a name="syntax"></a>Sintaxis

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Notas

Conservar el último código de error implica una disminución del rendimiento.  Si no desea incurrir en el impacto en el rendimiento de conservar el último código de error, vincule con **/CLRSUPPORTLASTERROR: no**.

Puede minimizar el impacto en el rendimiento mediante la vinculación con **/CLRSUPPORTLASTERROR: SYSTEMDLL**, que solo conserva el último código de error para las funciones de los archivos DLL del sistema.  Un archivo DLL del sistema se define como uno de los siguientes:

|||||
|-|-|-|-|
|ACLUI. DLL|ACTIVEDS. DLL|ADPTIF. DLL|ADVAPI32.DLL|
|ASYCFILT. DLL|AUTHZ. DLL|AVICAP32.DLL|AVIFIL32. DLL|
|Archiva. DLL|CLUSAPI. DLL|Comctl32. DLL|COMDLG32. DLL|
|COMSVCS. DLL|CREDUI. DLL|CRYPT32.DLL|CRYPTNET. DLL|
|CRYPTUI.DLL|D3D8THK. DLL|DBGENG. DLL|DBGHELP. DLL|
|DCIMAN32. DLL|DNSAPI. DLL|DSPROP. DLL|DSUIEXT. DLL|
|GDI32. DLL|GLU32. DLL|HLINK. DLL|ICM32.DLL|
|IMAGEHLP. DLL|IMM32. DLL|IPHLPAPI. DLL|IPROP. DLL|
|KERNEL32.DLL|KSUSER. DLL|LOADPERF. DLL|LZ32. DLL|
|MAPI32.DLL|MGMTAPI. DLL|MobSync. DLL|MPR. DLL|
|MPRAPI. DLL|MQRT. DLL|MSACM32.DLL|MSCMS. DLL|
|MS. DLL|MSIMG32. DLL|MSRATING. DLL|MSTASK. DLL|
|MSVFW32.DLL|MSWSOCK. DLL|MTXEX. DLL|NDDEAPI. DLL|
|Netapi32. DLL|NPPTOOLS. DLL|NTDSAPI. DLL|NTDSBCLI. DLL|
|NTMSAPI. DLL|ODBC32.DLL|ODBCBCP. DLL|Ole32. DLL|
|OLEACC. DLL|OLEAUT32.DLL|OLEDLG. DLL|OPENGL32. DLL|
|PDH. DLL|POWRPROF.DLL|QOSNAME. DLL|Misma. DLL|
|RASAPI32.DLL|RASDLG. DLL|RASSAPI. DLL|RESUTILS. DLL|
|Riched20. DLL|RPCNS4. DLL|RPCRT4. DLL|Versión. DLL|
|RTUTILS. DLL|SCARDDLG. DLL|SECUR32.DLL|SENSAPI. DLL|
|SETUPAPI. DLL|SFC. DLL|SHELL32. DLL|SHFOLDER. DLL|
|SHLWAPI. DLL|SISBKUP. DLL|SNMPAPI. DLL|SRCLIENT. DLL|
|Sexual. DLL|TAPI32. DLL|Entrante. DLL|Dirección. DLL|
|URLMON.DLL|User32. DLL|USERENV. DLL|USP10. DLL|
|UXTHEME. DLL|VDMDBG. DLL|Versión. DLL|WINFAX. DLL|
|WinHTTP. DLL|Wininet. DLL|WINMM. DLL|WINSCARD. DLL|
|WINTRUST. DLL|WLDAP32.DLL|WOW32.DLL|WS2_32.DLL|
|WSNMP32.DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP. DLL|

> [!NOTE]
>  No se admite la conservación del último error para las funciones no administradas que utiliza el código CLR, en el mismo módulo.

- Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **Enlazador**.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el cuadro **opciones adicionales** .

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

En el ejemplo siguiente se usa el archivo DLL, que muestra cómo usar **/CLRSUPPORTLASTERROR**.

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

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
