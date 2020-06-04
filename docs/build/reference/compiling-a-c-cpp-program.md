---
title: Referencia del compilador de C/C++ MSVC-Visual Studio
description: Opciones del conjunto de herramientas del compilador MSVC
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: c75176b139895d7b00d88aca1c58604b47386894
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077373"
---
# <a name="compiling-a-cc-project"></a>Compilar unC++ proyecto de C/

Las opciones C++ de C y del compilador se pueden establecer en el IDE de Visual Studio o en la línea de comandos.

## <a name="in-visual-studio"></a>En Visual Studio

Puede establecer las opciones del compilador para cada proyecto en el cuadro de diálogo **páginas de propiedades** de Visual Studio. En el panel izquierdo, seleccione **propiedades de configuración**, **CC++ /** y, a continuación, elija la categoría opción del compilador. En el tema de cada opción del compilador se describe cómo puede definirse y dónde se encuentra en el entorno de desarrollo. Consulte [Opciones del compilador MSVC](compiler-options.md) para obtener una lista completa.

## <a name="from-the-command-line"></a>Desde la línea de comandos

Las opciones del compilador (CL.exe) pueden definirse:

- [En la línea de comandos](compiler-command-line-syntax.md)

- [En archivos de comandos](cl-command-files.md)

- [En la variable de entorno de CL](cl-environment-variables.md)

Las opciones especificadas en la variable de entorno de CL se usan cada vez que se invoca CL. Si se menciona un archivo de comandos en la variable de entorno de CL o en la línea de comandos, se usarán las opciones especificadas en dicho archivo. A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.

Las opciones del compilador se procesan "de izquierda a derecha" y, si se detecta un conflicto, tiene prioridad la última opción (la que está situada más a la derecha). La variable de entorno de CL se procesa antes que la línea de comandos, por lo que siempre tendrá prioridad en caso de conflicto con la línea de comandos.

## <a name="additional-compiler-topics"></a>Temas adicionales relacionados con el compilador

- [Opciones del compilador de MSVC](compiler-options.md)

- [Archivos de encabezado precompilados](../creating-precompiled-header-files.md)

- [CL invoca el vinculador](cl-invokes-the-linker.md)

Para obtener información sobre cómo elegir el host del compilador y la arquitectura de destino, consulte [configuración C++ de proyectos para destinos x64 de 64 bits](../configuring-programs-for-64-bit-visual-cpp.md).

## <a name="see-also"></a>Consulte también

[Referencia de compilación de C/C++](c-cpp-building-reference.md)
