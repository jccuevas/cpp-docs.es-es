---
title: Requisitos de compilación para los controles comunes de Windows
ms.date: 08/19/2019
helpviewer_keywords:
- Common Controls (MFC), build requirements
- Common Controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: cf2139e04d2f72feb7951010caa351d67ccc5a93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619743"
---
# <a name="build-requirements-for-windows-common-controls"></a>Requisitos de compilación para los controles comunes de Windows

La biblioteca MFC (Microsoft Foundation Class) es compatible con [los controles comunes de Windows](/windows/win32/controls/common-controls-intro). Los controles comunes se incluyen en Windows y la biblioteca se incluye en Visual Studio. La biblioteca MFC proporciona nuevos métodos que mejoran las clases existentes, así como clases y métodos adicionales que admiten controles comunes de Windows. Al compilar la aplicación, debe seguir los requisitos de compilación y migración que se describen en las secciones siguientes.

## <a name="compilation-requirements"></a>Requisitos de compilación

### <a name="supported-versions"></a>Versiones admitidas

MFC es compatible con todas las versiones de los controles comunes. Para obtener información sobre las versiones de controles comunes de Windows, vea [versiones de control comunes](/windows/win32/controls/common-control-versions).

### <a name="supported-character-sets"></a>Juegos de caracteres compatibles

Los controles comunes de Windows solo admiten el juego de caracteres Unicode, no el juego de caracteres ANSI. Si compila la aplicación en la línea de comandos, use las siguientes opciones del compilador de definición (/D) para especificar Unicode como el juego de caracteres subyacente:

```
/D_UNICODE /DUNICODE
```

Si compila la aplicación en el entorno de desarrollo integrado (IDE) de Visual Studio, especifique la opción **juego de caracteres Unicode** de la propiedad **juego de caracteres** en el nodo **General** de las propiedades del proyecto.

## <a name="migration-requirements"></a>Requisitos de migración

Si usa el IDE de Visual Studio para compilar una nueva aplicación MFC que utiliza controles comunes de Windows, el IDE declara automáticamente un manifiesto adecuado. Sin embargo, si migra una aplicación MFC existente desde Visual Studio 2005 o una versión anterior y desea usar los controles comunes, el IDE no proporciona automáticamente información de manifiesto para actualizar la aplicación. En su lugar, debe insertar manualmente el siguiente código fuente en el archivo de encabezado precompilado:

```
#ifdef UNICODE
#if defined _M_IX86
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_IA64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_X64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#else
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")
#endif
#endif
```

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](general-mfc-topics.md)<br/>
[Gráfico de jerarquías](hierarchy-chart.md)<br/>
[API ANSI en desuso](deprecated-ansi-apis.md)
