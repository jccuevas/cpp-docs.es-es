---
title: /GH (Habilitar la función de enlace _pexit)
ms.date: 11/04/2016
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: 5382ba90f490aaa12e9e55767fdf15170a69ced5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749227"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (Habilitar la función de enlace _pexit)

Llama `_pexit` a la función al final de cada método o función.

## <a name="syntax"></a>Sintaxis

```
/GH
```

## <a name="remarks"></a>Observaciones

La `_pexit` función no forma parte de ninguna biblioteca y `_pexit`depende de usted proporcionar una definición para .

A menos que planee llamar `_pexit`explícitamente , no es necesario proporcionar un prototipo. La función debe aparecer como si tuviera el siguiente prototipo, y debe insertar el contenido de todos los registros en la entrada y hacer estallar el contenido sin cambios al salir:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit`es similar `_penter`a ; ver [/Gh (Habilitar _penter función de enlace)](gh-enable-penter-hook-function.md) para obtener un ejemplo de cómo escribir una `_pexit` función.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
