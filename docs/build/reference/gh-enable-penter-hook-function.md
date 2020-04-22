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
ms.openlocfilehash: 87815b5f0e0450b84acbe3c35b7ef4f31216ec72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749293"
---
# <a name="gh-enable-_penter-hook-function"></a>/GH (Habilitar la función de enlace _penter)

Provoca una llamada `_penter` a la función al inicio de cada método o función.

## <a name="syntax"></a>Sintaxis

```
/Gh
```

## <a name="remarks"></a>Observaciones

La `_penter` función no forma parte de ninguna biblioteca y `_penter`depende de usted proporcionar una definición para .

A menos que planee llamar `_penter`explícitamente , no es necesario proporcionar un prototipo. La función debe aparecer como si tuviera el siguiente prototipo, y debe insertar el contenido de todos los registros en la entrada y hacer estallar el contenido sin cambios al salir:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Esta declaración no está disponible para proyectos de 64 bits.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Ejemplo

El código siguiente, cuando se compila `_penter` con **/Gh**, muestra cómo se llama dos veces; una vez al `main` entrar en la `x`función y una vez al introducir la función .

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
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
