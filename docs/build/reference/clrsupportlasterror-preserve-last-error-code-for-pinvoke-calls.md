---
title: /CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 5e4a5c86e53d74c8b704ee3780991d496fc1802a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807681"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Conservar el último código de error para las llamadas a PInvoke)

**/ CLRSUPPORTLASTERROR**, que está activada de forma predeterminada, conserva el último código de error de las funciones que se llama mediante el mecanismo P/Invoke, lo que permite llamar a funciones nativas en archivos DLL, desde el código compilado con **/CLR**.

## <a name="syntax"></a>Sintaxis

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Comentarios

Conservar el último código de error implica una disminución del rendimiento.  Si no desea incurrir en el impacto de rendimiento de conservar el último código de error, vincule con **/CLRSUPPORTLASTERROR:NO**.

Puede minimizar el impacto del rendimiento mediante la vinculación con **/CLRSUPPORTLASTERROR:SYSTEMDLL**, que solo conserva el último código de error para las funciones en archivos DLL del sistema.  Un archivo DLL del sistema se define como uno de los siguientes:

|||||
|-|-|-|-|
|ACLUI.DLL|ACTIVEDS. ARCHIVO DLL|ADPTIF. ARCHIVO DLL|ADVAPI32.DLL|
|ASYCFILT.DLL|AUTHZ.DLL|AVICAP32.DLL|AVIFIL32.DLL|
|ARCHIVO. CAB. ARCHIVO DLL|CLUSAPI. ARCHIVO DLL|COMCTL32.DLL|ARCHIVO COMDLG32. ARCHIVO DLL|
|COMSVCS.DLL|CREDUI. ARCHIVO DLL|CRYPT32.DLL|CRYPTNET. ARCHIVO DLL|
|CRYPTUI.DLL|D3D8THK.DLL|DBGENG. ARCHIVO DLL|DBGHELP. ARCHIVO DLL|
|DCIMAN32.DLL|DNSAPI.DLL|DSPROP.DLL|DSUIEXT.DLL|
|GDI32.DLL|GLU32.DLL|HLINK. ARCHIVO DLL|ICM32.DLL|
|IMAGEHLP. ARCHIVO DLL|IMM32.DLL|IPHLPAPI. ARCHIVO DLL|IPROP. ARCHIVO DLL|
|KERNEL32.DLL|KSUSER.DLL|LOADPERF. ARCHIVO DLL|LZ32.DLL|
|MAPI32.DLL|MGMTAPI.DLL|MOBSYNC.DLL|MPR. ARCHIVO DLL|
|MPRAPI. ARCHIVO DLL|MQRT.DLL|MSACM32.DLL|MSCMS. ARCHIVO DLL|
|MSI.DLL|MSIMG32.DLL|MSRATING. ARCHIVO DLL|MSTASK. ARCHIVO DLL|
|MSVFW32.DLL|MSWSOCK.DLL|MTXEX.DLL|NDDEAPI. ARCHIVO DLL|
|NETAPI32.DLL|NPPTOOLS. ARCHIVO DLL|NTDSAPI.DLL|NTDSBCLI.DLL|
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL|OLE32. ARCHIVO DLL|
|OLEACC. ARCHIVO DLL|OLEAUT32.DLL|OLEDLG. ARCHIVO DLL|OPENGL32.DLL|
|PDH. ARCHIVO DLL|POWRPROF.DLL|QOSNAME.DLL|CONSULTA. ARCHIVO DLL|
|RASAPI32.DLL|RASDLG. ARCHIVO DLL|RASSAPI. ARCHIVO DLL|RESUTILS. ARCHIVO DLL|
|RICHED20. ARCHIVO DLL|RPCNS4.DLL|RPCRT4.DLL|RTM.DLL|
|RTUTILS.DLL|SCARDDLG. ARCHIVO DLL|SECUR32.DLL|SENSAPI.DLL|
|SETUPAPI.DLL|SFC. ARCHIVO DLL|SHELL32.DLL|SHFOLDER. ARCHIVO DLL|
|SHLWAPI.DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT. ARCHIVO DLL|
|STI.DLL|TAPI32.DLL|TRÁFICO. ARCHIVO DLL|URL.DLL|
|URLMON.DLL|USER32.DLL|USERENV. ARCHIVO DLL|USP10.DLL|
|UXTHEME. ARCHIVO DLL|VDMDBG.DLL|VERSIÓN. ARCHIVO DLL|WINFAX. ARCHIVO DLL|
|WINHTTP.DLL|WININET. ARCHIVO DLL|WINMM.DLL|WINSCARD.DLL|
|WINTRUST.DLL|WLDAP32.DLL|WOW32.DLL|WS2_32.DLL|
|WSNMP32.DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP.DLL|

> [!NOTE]
>  Conservar el último error no se admite para las funciones no administradas que se consumen por código de CLR, en el mismo módulo.

- Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Ejemplo

El ejemplo siguiente define una DLL nativa con una función exportada que modifica el último error.

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

El ejemplo siguiente utiliza el archivo DLL, que muestra cómo utilizar **/CLRSUPPORTLASTERROR**.

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

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
