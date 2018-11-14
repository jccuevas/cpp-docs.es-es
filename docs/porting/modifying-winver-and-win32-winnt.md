---
title: Modificar WINVER y _WIN32_WINNT
ms.date: 09/04/2017
helpviewer_keywords:
- WINVER in an upgraded Visual C++ project
- _WIN32_WINNT in an upgraded Visual C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: 3381b6657f78144e7804112135c437824d8555fe
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332250"
---
# <a name="modifying-winver-and-win32winnt"></a>Modificar WINVER y _WIN32_WINNT

Visual C++ ya no admite como destino Windows 95, Windows 98, Windows ME, Windows NT o Windows 2000. Si las macros **WINVER** o **_WIN32_WINNT** están asignadas a una de estas versiones de Windows, debe modificar las macros. Al actualizar un proyecto creado con una versión anterior de Visual C++, pueden producirse errores de compilación relacionados con las macros **WINVER** o **_WIN32_WINNT** macros si están asignadas a una versión de Windows que ya no se admite.

## <a name="remarks"></a>Comentarios

Para modificar las macros, en un archivo de encabezado (por ejemplo, targetver.h que se incluye al crear un proyecto destinado a Windows), agregue las líneas siguientes.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Esto tiene como destino el sistema operativo de Windows 10. Estos valores se muestran en el archivo de encabezado de Windows SDKDDKVer.h, que también define las macros para cada versión de Windows. Debe agregar la instrucción #define antes de incluir SDKDDKVer.h. Aquí se muestran las líneas de la versión de Windows 10 de SDKDDKVer.h que codifican los valores para cada versión de Windows:

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

Si no ve todas estas versiones de Windows en la copia de SDKDDKVer.h que está revisando, probablemente esté utilizando una versión anterior del SDK de Windows. De forma predeterminada, los proyectos de Win32 de Visual Studio 2017 usan el SDK de Windows 10.

> [!NOTE]
> No se garantiza que los valores funcionen si incluye encabezados de MFC internos en la aplicación.

También puede definir esta macro mediante la opción del compilador `/D`. Para obtener más información, vea [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md).

Para obtener más información sobre el significado de estas macros, consulte [Uso de los encabezados de Windows](/windows/desktop/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Vea también

[Historial de cambios en Visual C++](../porting/visual-cpp-change-history-2003-2015.md)