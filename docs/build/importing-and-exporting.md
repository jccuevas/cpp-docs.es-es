---
title: Importar y exportar
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220644"
---
# <a name="importing-and-exporting"></a>Importar y exportar

Puede importar símbolos públicos en una aplicación o exportar funciones de un archivo DLL con dos métodos:

- Mediante el uso de un archivo de definición de módulos (.def) al compilar el archivo DLL.

- Mediante el uso de las palabras clave **__declspec(dllimport)** o **__declspec(dllexport)** en una definición de función de la aplicación principal.

## <a name="using-a-def-file"></a>Uso de un archivo .def

Un archivo de definición de módulos (.def) es un archivo de texto que contiene una o varias instrucciones de módulo que describen varios atributos de un archivo DLL. Si no usa **__declspec(dllimport)** o **__declspec(dllexport)** para exportar las funciones de un archivo DLL, el archivo DLL requiere un archivo .def.

Puede usar archivos .def para [importar en una aplicación](importing-using-def-files.md) o [exportar de un archivo DLL](exporting-from-a-dll-using-def-files.md).

## <a name="using-__declspec"></a>Uso de __declspec

No es necesario que use **__declspec(dllimport)** para que el código se compile correctamente, pero, en caso de que lo haga, el compilador generará mejor código. El compilador podrá generar un código de mayor calidad porque puede determinar si una función existe en un archivo DLL, lo que permite al compilador generar código que omite un nivel de direccionamiento indirecto que normalmente estaría presente en una llamada de función que haya cruzado un límite de DLL. Aun así, debe usar **__declspec(dllimport)** para importar las variables usadas en un archivo DLL.

Con la sección EXPORTS adecuada del archivo .def, no es necesario el uso de **__declspec(dllexport)** . **__declspec(dllexport)** se ha agregado para proporcionar una manera sencilla de exportar funciones de un archivo .exe o .dll sin necesidad de usar un archivo .def.

El formato de archivo portable ejecutable de Win32 está diseñado para minimizar el número de páginas que se deben tocar para corregir las importaciones. Para ello, coloca todas las direcciones de importación de cualquier programa en un lugar denominado "tabla de direcciones de importación". Esto permite que el cargador modifique solo una o dos páginas al acceder a estas importaciones.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Importar a una aplicación](importing-into-an-application-using-declspec-dllimport.md)

- [Exportar desde un archivo DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Vea también

[Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
