---
title: /Oi (Generar funciones intrínsecas)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
ms.openlocfilehash: f3afedade6f99129c21069e5117daa4ceb616cc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320349"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Generar funciones intrínsecas)

Reemplaza algunas llamadas función con formas intrínsecas o especiales de la función que ayudará a la aplicación se ejecute más rápido.

## <a name="syntax"></a>Sintaxis

```
/Oi[-]
```

## <a name="remarks"></a>Comentarios

Programas que usan funciones intrínsecas son más rápidas porque no tiene la sobrecarga de llamadas de función, pero podría ser más grandes debido al código adicional que se creó.

Consulte [intrínseco](../../preprocessor/intrinsic.md) para obtener más información en el que las funciones tienen formas intrínsecas.

**/Oi** es solo una solicitud al compilador para reemplazar algunas llamadas de función con formas intrínsecas; el compilador puede llamar a la función (y no reemplazar la llamada de función con una función intrínseca) si dará como resultado un mejor rendimiento.

**x86 específico**

Las funciones intrínsecas de punto flotante no se realiza ninguna comprobación especial en los valores de entrada y por lo que funcionan en intervalos de entrada restringidos y tener control de excepciones diferentes y las condiciones de límite que las rutinas de biblioteca con el mismo nombre. El uso de las formas intrínsecas auténticas implica la pérdida de control de excepciones de IEEE y de `_matherr` y `errno` funcionalidad; esta última implica la pérdida de conformidad con ANSI. Sin embargo, las formas intrínsecas pueden acelerar considerablemente los programas que usan punto flotante, y muchos programas, los problemas de conformidad tienen poco valor práctico.

Puede usar el [Za](za-ze-disable-language-extensions.md) opción del compilador para reemplazar la generación de opciones verdaderas intrínsecas de punto flotante. En este caso, las funciones se generan como rutinas de biblioteca que pasan los argumentos directamente al chip de punto flotante, en lugar de insertarlos en la pila del programa.

**END x86 específico**

También usa [intrínseco](../../preprocessor/intrinsic.md) para crear funciones intrínsecas o [(función) (C/C ++)](../../preprocessor/function-c-cpp.md) para forzar explícitamente una llamada de función.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **optimización** página de propiedades.

1. Modificar el **habilitar funciones intrínsecas** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](o-options-optimize-code.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Intrínsecos del controlador](../../intrinsics/compiler-intrinsics.md)
