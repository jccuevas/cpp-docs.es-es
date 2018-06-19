---
title: Opciones del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea07361a292ee5e7cde99cedad2d5ac4c8a53aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374282"
---
# <a name="compiler-options"></a>Opciones del compilador

cl.exe es una herramienta que controla los compiladores de C++ y Microsoft Visual C++ (MSVC) C y el vinculador. cl.exe puede realizarse únicamente en sistemas operativos compatibles con Microsoft Visual Studio para Windows.

> [!NOTE]  
> Puede iniciar esta herramienta solo desde un símbolo del sistema de Visual Studio developer. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos. Para obtener más información, consulte [de compilación de C/C ++ en la línea de comandos](../building-on-the-command-line.md).

Los compiladores generan archivos objeto (.obj) de formato de archivo de objeto común (COFF). El vinculador genera archivos ejecutables (.exe) o bibliotecas de vínculos dinámicos (DLL).

Tenga en cuenta que todas las opciones del compilador distinguen mayúsculas de minúsculas. Puede usar cualquier una barra diagonal (`/`) o por un guión (`-`) para especificar una opción del compilador.

Para compilar sin vinculación, use la [/c](../../build/reference/c-compile-without-linking.md) opción.

## <a name="find-a-compiler-option"></a>Buscar una opción del compilador

Para buscar una opción de compilador determinado, consulte una de las listas siguientes:

- [Opciones del compilador por orden alfabético](../../build/reference/compiler-options-listed-alphabetically.md)

- [Opciones del compilador por categoría](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Especifique las opciones de compilador

El tema de cada opción del compilador describe cómo se puede establecer en el entorno de desarrollo. Para obtener información sobre cómo especificar opciones fuera del entorno de desarrollo, consulte:

- [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)

- [Archivos de comandos de CL](../../build/reference/cl-command-files.md)

- [Variables de entorno de CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Herramientas de generación relacionadas

[Opciones del vinculador](../../build/reference/linker-options.md) también afectan al modo en que se compila el programa.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
[Compilación rápida](../../build/reference/fast-compilation.md)  
[CL invoca el vinculador](../../build/reference/cl-invokes-the-linker.md)  
