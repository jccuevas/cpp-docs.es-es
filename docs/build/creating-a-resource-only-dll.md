---
title: Crear un archivo DLL de recursos
description: Cómo crear un archivo DLL solo de recursos en Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821348"
---
# <a name="creating-a-resource-only-dll"></a>Crear un archivo DLL de recursos

Un archivo DLL de recursos es un archivo DLL que sólo contiene recursos, como iconos, mapas de bits, cadenas y cuadros de diálogo. El uso de este tipo de archivo es una buena manera de compartir el mismo conjunto de recursos entre varios programas. También es una buena manera de proporcionar a una aplicación recursos localizados para varios idiomas. Para obtener más información, consulte [Recursos localizados en aplicaciones MFC: archivos DLL satélite](localized-resources-in-mfc-applications-satellite-dlls.md).

## <a name="create-a-resource-only-dll"></a>Creación de un archivo DLL solo de recursos

Para crear un archivo DLL solo de recursos, debe crear un proyecto de archivo DLL de Windows (que no esté basado en MFC) y agregar los recursos al proyecto:

::: moniker range="vs-2015"

1. Seleccione **Proyecto Win32** en el cuadro de diálogo **Nuevo proyecto**. Escriba los nombres del proyecto y de la solución y elija **Aceptar**.

1. En el **Asistente para aplicaciones Win32**, seleccione **Configuración de la aplicación**. En **Tipo de aplicación**, seleccione **DLL**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Haga clic en **Finalizar** para crear el proyecto.

1. Cree un script de recursos que contenga los recursos para el archivo DLL (como una cadena o un menú). Guarde el archivo `.rc`.

1. En el menú **Proyecto**, seleccione **Agregar elemento existente** e inserte el nuevo archivo `.rc` en el proyecto.

1. Especifique la opción [/NOENTRY](reference/noentry-no-entry-point.md) del enlazador. `/NOENTRY` impide que el enlazador vincule una referencia a `_main` en el archivo DLL; esta opción es necesaria para crear un archivo DLL solo de recursos.

1. Compile el archivo DLL.

::: moniker-end
::: moniker range=">=vs-2017"

1. Seleccione el **Asistente para escritorio de Windows** en el cuadro de diálogo **Nuevo proyecto** y elija **Siguiente**. En la página **Configurar el nuevo proyecto**, escriba los nombres del proyecto y de la solución y elija **Crear**.

1. En el cuadro de diálogo **Proyecto de escritorio de Windows**, en **Tipo de aplicación**, seleccione **Biblioteca de vínculos dinámicos**. En **Opciones adicionales**, seleccione **Proyecto vacío**. Seleccione **Aceptar** para crear el proyecto.

1. Cree un script de recursos que contenga los recursos para el archivo DLL (como una cadena o un menú). Guarde el archivo `.rc`.

1. En el menú **Proyecto**, seleccione **Agregar elemento existente** e inserte el nuevo archivo `.rc` en el proyecto.

1. Especifique la opción [/NOENTRY](reference/noentry-no-entry-point.md) del enlazador. `/NOENTRY` impide que el enlazador vincule una referencia a `_main` en el archivo DLL; esta opción es necesaria para crear un archivo DLL solo de recursos.

1. Compile el archivo DLL.

::: moniker-end

## <a name="use-a-resource-only-dll"></a>Uso de un archivo DLL solo de recursos

La aplicación que usa el archivo DLL solo de recursos debe llamar a [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) o a una función relacionada para vincular explícitamente al archivo DLL. Para acceder a los recursos, llame a las funciones genéricas `FindResource` y `LoadResource`, que funcionan en cualquier tipo de recurso. También puede llamar a una de las siguientes funciones específicas de recursos:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

La aplicación debe llamar a `FreeLibrary` cuando deje de usar los recursos.

## <a name="see-also"></a>Vea también

[Trabajar con archivos de recursos](../windows/working-with-resource-files.md)\
[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
