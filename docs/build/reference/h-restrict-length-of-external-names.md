---
title: /H (Restringir la longitud de los nombres externos)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: bdd3da8d3a5165262c00bc3475122e31f5770726
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270398"
---
# <a name="h-restrict-length-of-external-names"></a>/H (Restringir la longitud de los nombres externos)

Desusado. Restringe la longitud de los nombres externos.

## <a name="syntax"></a>Sintaxis

> **/H**<em>número</em>

## <a name="arguments"></a>Argumentos

*number*<br/>
Especifica la longitud máxima de los nombres externos permitidos en un programa.

## <a name="remarks"></a>Comentarios

De forma predeterminada, la longitud de los nombres externos (públicos) es 2.047 caracteres. Esto es cierto para los programas C y C++. Uso de **/H** puede disminuir solo la longitud máxima permitida de identificadores, no aumentarla. Un espacio entre **/H** y *número* es opcional.

Si un programa contiene más de los nombres externos *número*, se omiten los caracteres adicionales. Si compila un programa sin **/H** y un identificador contiene más de 2.047 caracteres, el compilador generará [Error irrecuperable C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

El límite de longitud incluye cualquier carácter de subrayado inicial creado por el compilador (**\_**) o signo de arroba (**\@**). Estos caracteres forman parte del identificador y ocupan una ubicación significativa.

- El compilador agrega un carácter de subrayado inicial (**\_**) a los nombres modificados por la `__cdecl` (valor predeterminado) y `__stdcall` convenciones de llamada y una líder en el inicio de sesión (**\@** ) para nombres modificados por la `__fastcall` convención de llamada.

- El compilador anexa información de tamaño de argumentos a los nombres modificados por la `__fastcall` y `__stdcall` las convenciones de llamada y agrega información de tipos a los nombres de C++.

Es posible **/H** útil:

- Al crear programas con varios lenguajes o portátiles.

- Al utilizar las herramientas que imponen límites a la longitud de los identificadores externos.

- Si desea restringir la cantidad de espacio que usan los símbolos en una compilación de depuración.

El ejemplo siguiente se muestra cómo usar **/H** puede causar errores si las longitudes de identificador se limitan demasiado:

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

También debe ser cuidadoso al usar el **/H** opción debido a los identificadores de compilador predefinidos. Si la longitud máxima del identificador es demasiado pequeña, algunos identificadores predefinidos será biblioteca sin resolver, así como ciertas llamadas de función. Por ejemplo, si la `printf` se utiliza la función y la opción **/H5** se especifica en tiempo de compilación, el símbolo **_prin** se creará para hacer referencia a `printf`, y esto no se encuentra en la biblioteca.

El uso de **/H** no es compatible con [/GL (Whole Program Optimization)](gl-whole-program-optimization.md).

El **/H** opción está en desuso desde Visual Studio 2005; han aumentado los límites de longitud máxima y **/H** ya no es necesario. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Especifique la opción del compilador en el **opciones adicionales** cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
