---
title: -GZ (habilitar la pila de comprobación de errores en tiempo de ejecución de marco) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gz
dev_langs:
- C++
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f13824064b7c7dcdb75524a22b14a4d90942918
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707231"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Habilitar comprobación de errores del marco de pila en tiempo de ejecución)

Realiza las mismas operaciones que el [/RTC (comprobaciones de errores de tiempo de ejecución)](../../build/reference/rtc-run-time-error-checks.md) opción. Desusado.

## <a name="syntax"></a>Sintaxis

```
/GZ
```

## <a name="remarks"></a>Comentarios

**/GZ** es sólo para su uso en una generación ([/Od (deshabilitar (depurar))](../../build/reference/od-disable-debug.md)) de compilación.

**/GZ** está en desuso desde Visual Studio 2005; use [/RTC (comprobaciones de errores de tiempo de ejecución)](../../build/reference/rtc-run-time-error-checks.md) en su lugar. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)