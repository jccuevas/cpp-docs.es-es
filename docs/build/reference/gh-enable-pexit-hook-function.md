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
ms.openlocfilehash: 9be8573f5f9c344d2675bd7c9fc7d8beb3c8cffd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527652"
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

`_pexit` es similar a `_penter`; vea [/Gh (habilitar _penter la función de enlace)](../../build/reference/gh-enable-penter-hook-function.md) para obtener un ejemplo de cómo escribir un `_pexit` función.

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