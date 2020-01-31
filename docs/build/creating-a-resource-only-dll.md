---
title: Crear un archivo DLL de recursos
description: Cómo crear un archivo DLL de solo recursos en Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821348"
---
# <a name="creating-a-resource-only-dll"></a>Crear un archivo DLL de recursos

Un archivo DLL de recursos es un archivo DLL que sólo contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo. El uso de este tipo de archivo es una buena manera de compartir el mismo conjunto de recursos entre varios programas. También es una buena manera de proporcionar una aplicación con recursos localizados para varios idiomas. Para obtener más información, vea [recursos localizados en aplicaciones MFC: archivos dll satélite](localized-resources-in-mfc-applications-satellite-dlls.md).

## <a name="create-a-resource-only-dll"></a>Crear un archivo DLL de solo recursos

Para crear un archivo DLL de solo recursos, cree un nuevo proyecto de DLL de Windows (no MFC) y agregue los recursos al proyecto:

::: moniker range="vs-2015"

1. Seleccione **proyecto Win32** en el cuadro de diálogo **nuevo proyecto** . Escriba los nombres del proyecto y de la solución y elija **Aceptar**.

1. En el **Asistente para aplicaciones Win32**, seleccione Configuración de la **aplicación**. Elija un **tipo de aplicación** de **dll**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Finalizar** para crear el proyecto.

1. Cree un nuevo script de recursos que contenga los recursos del archivo DLL (por ejemplo, una cadena o un menú). Guarde el archivo de `.rc`.

1. En el menú **proyecto** , seleccione **Agregar elemento existente**y, a continuación, inserte el nuevo archivo de `.rc` en el proyecto.

1. Especifique la opción de vinculador [/NOENTRY](reference/noentry-no-entry-point.md) . `/NOENTRY` impide que el vinculador vincule una referencia a `_main` en el archivo DLL; Esta opción es necesaria para crear un archivo DLL de solo recursos.

1. Compile el archivo DLL.

::: moniker-end
::: moniker range=">=vs-2017"

1. Seleccione **Asistente para escritorio de Windows** en el cuadro de diálogo **nuevo proyecto** y elija **siguiente**. En la página **configurar el nuevo proyecto** , escriba los nombres de proyecto y solución y elija **crear**.

1. En el cuadro de diálogo **proyecto de escritorio de Windows** , seleccione un tipo de **aplicación** de **biblioteca de vínculos dinámicos**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Elija **Aceptar** para crear el proyecto.

1. Cree un nuevo script de recursos que contenga los recursos del archivo DLL (por ejemplo, una cadena o un menú). Guarde el archivo de `.rc`.

1. En el menú **proyecto** , seleccione **Agregar elemento existente**y, a continuación, inserte el nuevo archivo de `.rc` en el proyecto.

1. Especifique la opción de vinculador [/NOENTRY](reference/noentry-no-entry-point.md) . `/NOENTRY` impide que el vinculador vincule una referencia a `_main` en el archivo DLL; Esta opción es necesaria para crear un archivo DLL de solo recursos.

1. Compile el archivo DLL.

::: moniker-end

## <a name="use-a-resource-only-dll"></a>Usar un archivo DLL de solo recursos

La aplicación que utiliza el archivo DLL de solo recursos debe llamar a [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) o a una función relacionada para vincularse explícitamente al archivo dll. Para tener acceso a los recursos, llame a las funciones genéricas `FindResource` y `LoadResource`, que funcionan en cualquier tipo de recurso. O bien, llame a una de las siguientes funciones específicas de recursos:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

La aplicación debe llamar a `FreeLibrary` cuando termine de usar los recursos.

## <a name="see-also"></a>Vea también

[Trabajar con archivos de recursos](../windows/working-with-resource-files.md)\
[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
