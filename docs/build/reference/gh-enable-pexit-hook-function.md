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
ms.openlocfilehash: 077096cc296f2aa2128127493a84a91da9a067c5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822176"
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (Habilitar la función de enlace _pexit)

Las llamadas del `_pexit` función al final de cada método o función.

## <a name="syntax"></a>Sintaxis

```
/GH
```

## <a name="remarks"></a>Comentarios

El `_pexit` función no forma parte de cualquier biblioteca y depende de usted para proporcionar una definición para `_pexit`.

A menos que se va a llamar explícitamente a `_pexit`, no es necesario proporcionar un prototipo. La función debe aparecer como si tuviera el siguiente prototipo, y se debe insertar el contenido de todos los registros de entrada y extraer el contenido sin modificar al salir:

```
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit` es similar a `_penter`; vea [/Gh (habilitar _penter la función de enlace)](gh-enable-penter-hook-function.md) para obtener un ejemplo de cómo escribir un `_pexit` función.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
