---
title: Crear un archivo DLL de recursos
ms.date: 11/04/2016
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
ms.openlocfilehash: 0d729be60ebec7a37d07fed1d14c4fd5330c7242
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220839"
---
# <a name="creating-a-resource-only-dll"></a>Crear un archivo DLL de recursos

Un archivo DLL de recursos es un archivo DLL que sólo contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo. El uso de este tipo de archivo es una buena manera de compartir el mismo conjunto de recursos entre varios programas. También es una buena forma de proporcionar una aplicación con recursos localizados en varios idiomas (vea [recursos localizados en aplicaciones MFC: Archivos DLL satélite](localized-resources-in-mfc-applications-satellite-dlls.md)).

Para crear un archivo DLL de recursos debe crear un nuevo proyecto de archivo DLL para Win32 (que no esté basado en MFC) y agregar los recursos al proyecto.

- Seleccione proyecto Win32 en el **nuevo proyecto** diálogo cuadro y especifique un tipo de proyecto DLL en el Asistente para proyectos Win32.

- Cree un nuevo script de recursos que contenga los recursos (como una cadena o un menú) para el archivo DLL y guarde el archivo .rc.

- En el **proyecto** menú, haga clic en **Agregar elemento existente**y, a continuación, inserte el nuevo archivo .rc en el proyecto.

- Especifique el [/NOENTRY](reference/noentry-no-entry-point.md) opción del vinculador. /NOENTRY evita que el vinculador vincule una referencia a `_main` en el archivo DLL; esta opción es necesaria para crear un archivo DLL de recursos.

- Compile el archivo DLL.

Debe llamar la aplicación que utiliza el archivo DLL de recursos [LoadLibrary](loadlibrary-and-afxloadlibrary.md) para vincularse explícitamente a la DLL. Para obtener acceso a los recursos, llame a las funciones genéricas `FindResource` y `LoadResource`, que funcionan en cualquier tipo de recurso, o llamar a una de las funciones específicas de los recursos siguientes:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

La aplicación debe llamar a `FreeLibrary` cuando termine con los recursos.

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Crear archivos DLL de C o C++ en Visual Studio](dlls-in-visual-cpp.md)
