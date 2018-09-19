---
title: -Gy (habilitar vinculación en el nivel de función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
dev_langs:
- C++
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09faa1a1d2b6743b7fce31af32ba4fe1572b592e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705008"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Habilitar vinculación en el nivel de función)

Permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs).

## <a name="syntax"></a>Sintaxis

```
/Gy[-]
```

## <a name="remarks"></a>Comentarios

El vinculador requiere que las funciones se empaqueta por separado como COMDAT para excluir u ordenar funciones individuales en un archivo .exe o DLL.

Puede usar la opción del vinculador [/OPT (optimizaciones)](../../build/reference/opt-optimizations.md) para excluir las funciones empaquetadas desde el archivo .exe.

Puede usar la opción del vinculador [/ORDER (colocar funciones en orden)](../../build/reference/order-put-functions-in-order.md) para incluir funciones empaquetadas en un orden especificado en el archivo .exe.

Las funciones inline siempre se empaquetan si sus instancias se crean como llamadas (lo que ocurre, por ejemplo, si la inserción es o si se toma una dirección de función). Además, las funciones de miembro de C++ definidas en la declaración de clase se empaquetan de manera automática; otras funciones no son, y al seleccionar esta opción es necesaria para compilarlos como funciones empaquetadas.

> [!NOTE]
>  El [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción, se utiliza para editar y continuar, se establece automáticamente la **/Gy** opción.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **generación de código** página de propiedades.

1. Modificar el **habilitar vinculación en el nivel de función** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)