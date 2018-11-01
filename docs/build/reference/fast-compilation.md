---
title: Compilación rápida
ms.date: 11/04/2016
helpviewer_keywords:
- performance, cle.exe compiler
- compilation, performance
- cl.exe compiler, performance
- fast compiling
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
ms.openlocfilehash: ab3171d7bb6d85cbe010e0efce39eda14b166527
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667663"
---
# <a name="fast-compilation"></a>Compilación rápida

Para aumentar la velocidad de las compilaciones:

- Use [recompilación mínima](../../build/reference/gm-enable-minimal-rebuild.md), en que el compilador de C++ vuelve a compilar un archivo de origen solo si depende de los cambios realizados en una clase en un archivo de encabezado.

- [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md) y usar el [precompilado opciones de encabezado](../../build/reference/yc-create-precompiled-header-file.md).

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)