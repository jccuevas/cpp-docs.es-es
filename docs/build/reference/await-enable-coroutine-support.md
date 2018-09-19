---
title: -await (habilitar la compatibilidad con corrutinas) | Microsoft Docs
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5da401f940a39c135ba0b64571b6330a42fed796
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725522"
---
# <a name="await-enable-coroutine-support"></a>/ await (habilitar la compatibilidad con corrutinas)

Use la **/ await** opción del compilador para habilitar la compatibilidad del compilador con las corrutinas.

## <a name="syntax"></a>Sintaxis

> / await

## <a name="remarks"></a>Comentarios

El **/ await** opción del compilador habilita la compatibilidad de compilador para las corrutinas de C++ y las palabras clave **co_await**, **co_yield**, y **co_return**. Esta opción está desactivada de forma predeterminada. Para obtener información sobre la compatibilidad con corrutinas en Visual Studio, consulte el [blog del equipo de Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Para obtener más información acerca de la propuesta estándar de corrutinas, consulte [N4628 Working Draft, especificaciones técnicas para las extensiones de C++ para las corrutinas](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf).

El **/ await** opción está disponible a partir de Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.

2. En **propiedades de configuración**, expanda el **C o C++** carpeta y elija el **línea de comandos** página de propiedades.

3. Escriba el **/ await** opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)