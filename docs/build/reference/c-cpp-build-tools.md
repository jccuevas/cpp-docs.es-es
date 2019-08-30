---
title: Herramientas de compilación de MSVC adicionales
ms.date: 08/28/2019
f1_keywords:
- c.build
helpviewer_keywords:
- builds [C++], C/C++ tools
- tools [C++], build
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
ms.openlocfilehash: 53c7c2f8c162cd851b4612e75ba14b019d9cbd63
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177295"
---
# <a name="additional-msvc-build-tools"></a>Herramientas de compilación de MSVC adicionales

Visual Studio proporciona las siguientes utilidades de línea de comandos para ver o manipular los resultados de la compilación:

- [Lib. EXE](lib-reference.md) se usa para crear y administrar una biblioteca de archivos objeto con formato de archivo de objeto común (COFF). También se puede usar para crear archivos de exportación y bibliotecas de importación para hacer referencia a las definiciones exportadas.

- [EDITBIN. EXE](editbin-reference.md) se utiliza para modificar archivos binarios COFF.

- [Dumpbin. EXE](dumpbin-reference.md) muestra información (por ejemplo, una tabla de símbolos) sobre archivos binarios COFF.

- [NMake](nmake-reference.md) Lee y ejecuta archivos make.

- [ERRLOOK](value-edit-control.md), la utilidad de búsqueda de errores, recupera un mensaje de error del sistema o un mensaje de error de módulo basado en el valor especificado.

- [Xdcmake](xdcmake-reference.md). Herramienta para procesar archivos de código fuente que contienen comentarios de documentación marcados con etiquetas XML.

- [BSCMAKE. EXE](bscmake-reference.md) (proporcionado únicamente por compatibilidad con versiones anteriores) crea un archivo de información de examen (. BSC) que contiene información sobre los símbolos (clases, funciones, datos, macros y tipos) del programa. Esta información se puede ver en las ventanas de exploración en el entorno de desarrollo. (También se puede crear un archivo. BSC en el entorno de desarrollo).

El Windows SDK también tiene varias herramientas de compilación, como [RC. EXE](/windows/win32/menurc/resource-compiler), que invoca C++ el compilador para compilar recursos nativos de Windows como cuadros de diálogo, páginas de propiedades, mapas de bits, tablas de cadenas, etc.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)<br/>
[Nombres representativos](decorated-names.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
