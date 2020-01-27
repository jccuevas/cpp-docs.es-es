---
title: Actualización de WINVER y _WIN32_WINNT
description: Cuándo y cómo actualizar las macros WINVER y _WIN32_WINNT en proyectos de Visual Studio C++ actualizados.
ms.date: 01/22/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: b81c7967732c7b0c23ff0eb73d2a866a9b33713b
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725701"
---
# <a name="update-winver-and-_win32_winnt"></a>Actualización de WINVER y _WIN32_WINNT

Al usar el Windows SDK, puede especificar las versiones de Windows en las que se puede ejecutar el código. Las macros de preprocesador **winver** y **_WIN32_WINNT** especifican la versión mínima del sistema operativo que admite el código. Visual Studio y el compilador de Microsoft C++ admiten el destino de Windows 7 SP1 y versiones posteriores. Los conjuntos de herramientas más antiguos incluyen compatibilidad con Windows XP SP4, Windows Server 2003 SP4, vista y Windows Server 2008. No se admiten Windows 95, Windows 98, Windows ME, Windows NT y Windows 2000.

Al actualizar un proyecto anterior, puede que tenga que actualizar las macros **winver** o **_WIN32_WINNT** . Si se les asignan valores para una versión no compatible de Windows, es posible que vea errores de compilación relacionados con estas macros.

## <a name="remarks"></a>Notas

Para modificar las macros, en un archivo de encabezado (por ejemplo, en *targetver. h*, que se incluye en algunas plantillas de proyecto que tienen como destino Windows), agregue las líneas siguientes.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Las macros del ejemplo se establecen para tener como destino cada versión del sistema operativo Windows 10. Los valores posibles se muestran en el archivo de encabezado de Windows *sdkddkver. h*, que define las macros para cada versión principal de Windows. Para compilar la aplicación para admitir una plataforma Windows anterior, incluya *WinSDKVer. h*. Después, establezca las macros **winver** y **_WIN32_WINNT** en la plataforma compatible más antigua antes de incluir *sdkddkver. h*. Estas son las líneas de la versión del SDK de Windows 10 de *sdkddkver. h* que codifican los valores para cada versión principal de Windows:

```C
//
// _WIN32_WINNT version constants
//
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10
```

Para un enfoque más específico sobre el control de versiones, puede usar las constantes de la versión NTDDI en *sdkddkver. h*. Estas son algunas de las macros definidas por *sdkddkver. h* en el SDK de Windows 10 versión 10.0.18362.0:

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

Las macros **OSVER**, **SPVER**y **SUBVER** se pueden usar en el código para controlar la compilación condicional para diferentes niveles de compatibilidad con la API.

Es posible que no vea todas estas versiones de Windows en la lista *sdkddkver. h* que está viendo. Esto significa que probablemente esté usando una versión anterior de la Windows SDK. De forma predeterminada, los nuevos proyectos de Windows en Visual Studio usan el SDK de Windows 10.

> [!NOTE]
> No se garantiza que los valores funcionen si incluye encabezados de MFC internos en la aplicación.

También puede definir esta macro mediante la opción del compilador `/D`. Para obtener más información, vea [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md).

Para obtener más información sobre el significado de estas macros, consulte [Uso de los encabezados de Windows](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Vea también

[Historial de cambios en Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
