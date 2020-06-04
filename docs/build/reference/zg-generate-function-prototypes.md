---
title: /Zg (Generar prototipos de función)
ms.date: 11/04/2016
f1_keywords:
- /zg
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
ms.openlocfilehash: 591460b78a461aa2e33f873b79d6dcec0277f99f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446202"
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Generar prototipos de función)

Quitado. Crea un prototipo de función para cada función definida en el archivo de origen, pero no compila el archivo de origen.

## <a name="syntax"></a>Sintaxis

```
/Zg
```

## <a name="remarks"></a>Comentarios

Esta opción de compilador ya no está disponible. Se ha eliminado en Visual Studio 2015. Esta página se conserva para usuarios de versiones anteriores de Visual Studio.

El prototipo de función incluye el tipo de valor devuelto de función y una lista de tipos de argumento. La lista de tipos de argumento se crea a partir de los tipos de los parámetros formales de la función. Se omiten los prototipos de función ya presentes en el archivo de origen.

La lista de prototipos se escribe en la salida estándar. Esta lista puede resultarle útil para comprobar que los argumentos reales y los parámetros formales de una función son compatibles. Para guardar la lista, redirija la salida estándar a un archivo. A continuación, puede usar **#include** para que la lista de prototipos de función forme parte del archivo de origen. Al hacerlo, el compilador realizará una comprobación de tipos de argumento.

Si usa la opción **/Zg** y el programa contiene parámetros formales con los tipos struct, enum o union (o punteros a estos tipos), la declaración de cada tipo struct, enum o union debe tener una etiqueta (nombre). En el ejemplo siguiente, el nombre de etiqueta es `MyStruct`.

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

El **/Zg** opción ha quedado en desuso en Visual Studio 2005 y se quitó en Visual Studio 2015. El compilador de MSVC ha quitado la compatibilidad con código de estilo C anterior. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
