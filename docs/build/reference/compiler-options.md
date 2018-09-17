---
title: Opciones del compilador | Microsoft Docs
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
ms.openlocfilehash: 76ab322dc4573863a30092b296e87e90c41619ab
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716220"
---
# <a name="compiler-options"></a>Opciones del compilador

cl.exe es una herramienta que controla los compiladores de C++ y Microsoft Visual C++ (MSVC) C y el vinculador. cl.exe se puede ejecutar solo en sistemas operativos que admiten Microsoft Visual Studio para Windows.

> [!NOTE]
> Puede iniciar esta herramienta solo desde un símbolo del sistema de Visual Studio para desarrolladores. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos. Para obtener más información, consulte [código de C o C++ de compilación en la línea de comandos](../building-on-the-command-line.md).

Los compiladores generan archivos de formato de archivo de objeto común (COFF) objeto (.obj). El vinculador genera archivos ejecutables (.exe) o bibliotecas de vínculos dinámicos (DLL).

Tenga en cuenta que todas las opciones del compilador distinguen mayúsculas de minúsculas. Puede usar una barra diagonal hacia delante (`/`) o por un guión (`-`) para especificar una opción del compilador.

Para compilar sin vinculación, utilice el [/c](../../build/reference/c-compile-without-linking.md) opción.

## <a name="find-a-compiler-option"></a>Buscar una opción del compilador

Para buscar una opción del compilador determinado, consulte una de las listas siguientes:

- [Opciones del compilador por orden alfabético](../../build/reference/compiler-options-listed-alphabetically.md)

- [Opciones del compilador por categoría](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Especifique las opciones del compilador

El tema de cada opción del compilador describe cómo se puede establecer en el entorno de desarrollo. Para obtener información sobre cómo especificar opciones fuera del entorno de desarrollo, consulte:

- [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)

- [Archivos de comandos de CL](../../build/reference/cl-command-files.md)

- [Variables de entorno de CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Herramientas de compilación relacionadas

[Opciones del vinculador](../../build/reference/linker-options.md) también afectan a cómo se compila el programa.

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Compilación rápida](../../build/reference/fast-compilation.md)<br/>
[CL invoca el vinculador](../../build/reference/cl-invokes-the-linker.md)
