---
title: Opciones del compilador MSVC
ms.date: 01/29/2018
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: 831aade72cd728ec42aee5ef1f320deb7bdf173d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816521"
---
# <a name="compiler-options"></a>Opciones del compilador

cl.exe es una herramienta que controla los compiladores de C++ y Microsoft Visual C++ (MSVC) C y el vinculador. cl.exe se puede ejecutar solo en sistemas operativos que admiten Microsoft Visual Studio para Windows.

> [!NOTE]
> Puede iniciar esta herramienta solo desde un símbolo del sistema de Visual Studio para desarrolladores. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos. Para obtener más información, consulte [usar el conjunto de herramientas desde la línea de comandos MSVC](../building-on-the-command-line.md).

Los compiladores generan archivos de formato de archivo de objeto común (COFF) objeto (.obj). El vinculador genera archivos ejecutables (.exe) o bibliotecas de vínculos dinámicos (DLL).

Tenga en cuenta que todas las opciones del compilador distinguen mayúsculas de minúsculas. Puede usar una barra diagonal hacia delante (`/`) o por un guión (`-`) para especificar una opción del compilador.

Para compilar sin vinculación, utilice el [/c](c-compile-without-linking.md) opción.

## <a name="find-a-compiler-option"></a>Buscar una opción del compilador

Para buscar una opción del compilador determinado, consulte una de las listas siguientes:

- [Opciones del compilador por orden alfabético](compiler-options-listed-alphabetically.md)

- [Opciones del compilador por categoría](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Especifique las opciones del compilador

El tema de cada opción del compilador describe cómo se puede establecer en el entorno de desarrollo. Para obtener información sobre cómo especificar opciones fuera del entorno de desarrollo, consulte:

- [Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)

- [Archivos de comandos de CL](cl-command-files.md)

- [Variables de entorno de CL](cl-environment-variables.md)

## <a name="related-build-tools"></a>Herramientas de compilación relacionadas

[Las opciones del vinculador MSVC](linker-options.md) también afectan a cómo se compila el programa.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)<br/>
[CL invoca el vinculador](cl-invokes-the-linker.md)
