---
title: /Gy (Habilitar vinculación en el nivel de función)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 8724ae4d018948c0f6aa9456f229db96878d7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328279"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Habilitar vinculación en el nivel de función)

Permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs).

## <a name="syntax"></a>Sintaxis

```
/Gy[-]
```

## <a name="remarks"></a>Observaciones

El vinculador requiere que las funciones se empaquetan por separado como COMDAT para excluir u ordenar funciones individuales en un archivo DLL o .exe.

Puede utilizar la opción del vinculador [/OPT (Optimizaciones)](opt-optimizations.md) para excluir las funciones empaquetadas sin referencia del archivo .exe.

Puede utilizar la opción del vinculador [/ORDER (Put Functions in Order)](order-put-functions-in-order.md) para incluir funciones empaquetadas en un orden especificado en el archivo .exe.

Las funciones en línea siempre se empaquetan si se crean instancias como llamadas (lo que se produce, por ejemplo, si la inserción está desactivada o si se toma una dirección de función). Además, las funciones miembro de C++ definidas en la declaración de clase se empaquetan automáticamente; otras funciones no lo son, y es necesario seleccionar esta opción para compilarlas como funciones empaquetadas.

> [!NOTE]
> La opción [/ZI,](z7-zi-zi-debug-information-format.md) utilizada para Editar y continuar, establece automáticamente la opción **/Gy.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Generación de código.**

1. Modifique la propiedad **Habilitar vinculación de nivel de función.**

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
