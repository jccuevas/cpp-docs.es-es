---
title: Referencia del compilador de MSVC C o C++ - Visual Studio
description: Opciones de conjunto de herramientas del compilador MSVC.
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: 2269ba69cea2702ff190c791eb6753acb3619f7d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810307"
---
# <a name="compiling-a-cc-project"></a>Compilar un proyecto de C o C++

Opciones del compilador de C y C++ se pueden establecer en el IDE de Visual Studio o en la línea de comandos. 

## <a name="in-visual-studio"></a>En Visual Studio

Puede establecer opciones del compilador para cada proyecto en su Visual Studio **páginas de propiedades** cuadro de diálogo. En el panel izquierdo, seleccione **propiedades de configuración**, **C o C++** y, a continuación, elija la categoría de opción del compilador. En el tema de cada opción del compilador se describe cómo puede definirse y dónde se encuentra en el entorno de desarrollo. Consulte [opciones del compilador MSVC](compiler-options.md) para obtener una lista completa.

## <a name="from-the-command-line"></a>Desde la línea de comandos

Las opciones del compilador (CL.exe) pueden definirse:

- [En la línea de comandos](compiler-command-line-syntax.md)

- [En los archivos de comandos](cl-command-files.md)

- [En la variable de entorno de CL](cl-environment-variables.md)

Las opciones especificadas en la variable de entorno de CL se usan cada vez que se invoca CL. Si se menciona un archivo de comandos en la variable de entorno de CL o en la línea de comandos, se usarán las opciones especificadas en dicho archivo. A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.

Las opciones del compilador se procesan "de izquierda a derecha" y, si se detecta un conflicto, tiene prioridad la última opción (la que está situada más a la derecha). La variable de entorno de CL se procesa antes que la línea de comandos, por lo que siempre tendrá prioridad en caso de conflicto con la línea de comandos.

## <a name="additional-compiler-topics"></a>Temas adicionales relacionados con el compilador

- [Opciones del compilador MSVC](compiler-options.md)

- [Archivos de encabezado precompilados](../creating-precompiled-header-files.md)

- [CL invoca el vinculador](cl-invokes-the-linker.md)

Para obtener información acerca de cómo elegir la arquitectura de host y de destino del compilador, vea [C++ configurar proyectos para 64 bits, x64 destinos](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)
