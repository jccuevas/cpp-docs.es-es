---
title: /await (Habilitar la compatibilidad con corrutinas)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: eeab3f4a1afc73e341f04222a55c8ce429490742
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078448"
---
# <a name="await-enable-coroutine-support"></a>/await (Habilitar la compatibilidad con corrutinas)

Use la opción del compilador **/Await** para habilitar la compatibilidad del compilador con las corrutinas.

## <a name="syntax"></a>Sintaxis

> /Await

## <a name="remarks"></a>Observaciones

La opción del compilador **/Await** habilita C++ la compatibilidad del compilador con las corutinas y las palabras clave **co_await**, **co_yield**y **co_return**. Esta opción está desactivada de forma predeterminada. Para obtener información sobre la compatibilidad con las corrutinas en Visual Studio, consulte el [blog del equipo de Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Para obtener más información sobre la propuesta estándar de las corrutinas, consulte el [borrador de C++ trabajo de N4628, especificación técnica de las extensiones para las corrutinas](https://wg21.link/n4628).

La opción **/Await** está disponible a partir de Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto.

1. En **propiedades de configuración**, expanda la carpeta **CC++ /** y elija la página de propiedades **línea de comandos** .

1. Escriba la opción del compilador **/Await** en el cuadro **opciones adicionales** . Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
