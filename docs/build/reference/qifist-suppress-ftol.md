---
title: /QIfist (Suprimir _ftol)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 7af88c91793688d23cf35177ae7a5250b04832a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319296"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (Suprimir _ftol)

Desusado. Suprime la llamada de la función del asistente `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero.

## <a name="syntax"></a>Sintaxis

```
/QIfist
```

## <a name="remarks"></a>Comentarios

> [!NOTE]
>  **/QIfist** solo está disponible en el compilador con destino x86; esta opción del compilador no está disponible en los compiladores con destino x64 o ARM.

Además de realizar la conversión de un tipo de punto flotante a un tipo entero, la función `_ftol` garantiza que el modo de redondeo de la unidad de punto flotante (FPU) se hace a cero (se trunca) mediante el establecimiento de los bits 10 y 11 de la palabra de control. Esto garantiza que la conversión de un tipo de punto flotante en tipo entero se realiza como se describe en la norma ANSI C (la parte fraccionaria del número se descarta). Cuando se usa **/QIfist**, esta garantía ya no es aplicable. El modo de redondeo será uno de los cuatro documentados en los manuales de referencia de Intel:

- Redondeo al más próximo (número par si está equidistante)

- Redondeo a infinito negativo

- Redondeo a infinito positivo

- Redondeo a cero

Puede usar el [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) función de tiempo de ejecución de C para modificar el comportamiento de redondeo de la FPU. El modo de redondeo predeterminado de la FPU es "Redondeo al más próximo". Uso de **/QIfist** puede mejorar el rendimiento de la aplicación, pero no sin riesgo. Debe probar exhaustivamente las partes del código que sean sensibles al modo de redondeo antes de lanzar un código generado con **/QIfist** en entornos de producción.

[/ arch (x86)](arch-x86.md) y **/QIfist** no se puede usar en la misma operación de compilación.

> [!NOTE]
>  **/QIfist** es no en vigor de forma predeterminada porque los bits de redondeo también afectan al punto flotante de punto de redondeo (que se produce después de cada cálculo), por lo que cuando se establecen las marcas para redondeo de estilo C (a cero), su tipo flotante los cálculos pueden ser diferentes. **/QIfist** no debe usarse si el código depende del comportamiento esperado de truncar la parte fraccionaria del número de punto flotante. Si no está seguro, no use **/QIfist**.

El **/QIfist** opción está en desuso a partir de Visual Studio 2005. Se han realizado mejoras importantes en el compilador en cuanto a la velocidad de conversión de los tipos float a int. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](q-options-low-level-operations.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
