---
title: -EXPORT (exporta una función) | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22b79454b71f4908d71e683d8bebe4611da7cb14
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861873"
---
# <a name="export-exports-a-function"></a>/EXPORT (Exporta una función)

Exporta una función por nombre u ordinal o datos, desde el programa.

## <a name="syntax"></a>Sintaxis

> **/ EXPORT:**<em>entrada</em>[**,\@**<em>ordinal</em>[**, NONAME**]] [**, datos**]

## <a name="remarks"></a>Comentarios

El **/EXPORT** opción especifica un función o elemento de datos para exportar desde el programa para que otros programas puedan llamar a la función o usar los datos. Las exportaciones se definen normalmente en un archivo DLL.

El *entrada* es el nombre de la función o elemento de datos que va a ser utilizada por el programa que realiza la llamada. *ordinal* especifica un índice en la tabla de exportaciones en el intervalo 1 a 65535; si no especifica *ordinal*, LINK asigna uno. El **NONAME** palabra clave exporta la función solo como un valor ordinal, sin un *entrada*.

El **datos** palabra clave especifica que el elemento exportado es un elemento de datos. El elemento de datos en el programa cliente debe declararse mediante **extern __declspec (dllimport)**.

Hay cuatro métodos para exportar una definición, aparece en el orden recomendado de uso:

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) en el código fuente

1. Un [exportaciones](../../build/reference/exports.md) instrucción en un archivo .def

1. Una especificación /EXPORT en un comando de LINK

1. Un [comentario](../../preprocessor/comment-c-cpp.md) la directiva en el código fuente, del formulario `#pragma comment(linker, "/export: definition ")`.

Todos estos métodos pueden usarse en el mismo programa. Cuando LINK compila un programa que contiene exportaciones, también crea una biblioteca de importación, a menos que se usa un archivo .exp en la compilación.

LINK usa formatos de identificadores representativos. El compilador decora un identificador cuando crea el archivo .obj. Si *entrada* se especifica al vinculador en su no representativo de formulario (tal como aparece en el código fuente), vínculo intenta hacer coincidir el nombre. Si no encuentra a una coincidencia única, vínculo emite un mensaje de error. Use la [DUMPBIN](../../build/reference/dumpbin-reference.md) herramienta para obtener el [nombre representativo](../../build/reference/decorated-names.md) formulario de un identificador al que deberá especificarlo al vinculador.

> [!NOTE]
> No se especifica el formato representativo de los identificadores de C que se declaran `__cdecl` o `__stdcall`.

Si tiene que exportar un nombre de función no representativos y tener exportaciones diferentes dependiendo de la configuración de compilación (por ejemplo, en las compilaciones de 32 bits o 64 bits), puede usar archivos DEF diferentes para cada configuración. (Las directivas de preprocesador condicionales no se permiten en los archivos DEF). Como alternativa, puede usar un `#pragma comment` la directiva antes de una declaración de función, como se muestra aquí, donde `PlainFuncName` es el nombre no representativo, y `_PlainFuncName@4` es el nombre representativo de la función:

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
