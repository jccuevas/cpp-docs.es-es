---
title: /GH (Habilitar la función de enlace _penter)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: bf7734a7b81c9550c060d43c2eabf5cb05332407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292591"
---
# <a name="gh-enable-penter-hook-function"></a>/GH (Habilitar la función de enlace _penter)

Hace que una llamada a la `_penter` función al principio de cada método o función.

## <a name="syntax"></a>Sintaxis

```
/Gh
```

## <a name="remarks"></a>Comentarios

El `_penter` función no forma parte de cualquier biblioteca y depende de usted para proporcionar una definición para `_penter`.

A menos que se va a llamar explícitamente a `_penter`, no es necesario proporcionar un prototipo. La función debe aparecer como si tuviera el siguiente prototipo, y se debe insertar el contenido de todos los registros de entrada y extraer el contenido sin modificar al salir:

```
void __declspec(naked) __cdecl _penter( void );
```

Esta declaración no está disponible para proyectos de 64 bits.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Ejemplo

El siguiente código, cuando se compila con **/Gh**, se muestra cómo `_penter` se llama dos veces; una vez al escribir la función `main` y una vez al escribir la función `x`.

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```Output
In a function!
In a function!
```

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
