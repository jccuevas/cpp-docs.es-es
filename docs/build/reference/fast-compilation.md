---
title: Compilación rápida de | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, cle.exe compiler
- compilation, performance
- cl.exe compiler, performance
- fast compiling
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 926c63d3d556d1aa9b85a7ce97e93b60e7c2ea23
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722273"
---
# <a name="fast-compilation"></a>Compilación rápida

Para aumentar la velocidad de las compilaciones:

- Use [recompilación mínima](../../build/reference/gm-enable-minimal-rebuild.md), en que el compilador de C++ vuelve a compilar un archivo de origen solo si depende de los cambios realizados en una clase en un archivo de encabezado.

- [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md) y usar el [precompilado opciones de encabezado](../../build/reference/yc-create-precompiled-header-file.md).

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)