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
ms.openlocfilehash: 5d6e12a1003ea125b0da4bfef580d8096e97553a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336105"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist (Suprimir _ftol)

En desuso. Suprime la llamada de la función del asistente `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero.

## <a name="syntax"></a>Sintaxis

```
/QIfist
```

## <a name="remarks"></a>Observaciones

> [!NOTE]
> **/QIfist** solo está disponible en el compilador de destino x86; esta opción del compilador no está disponible en los compiladores destinados a x64 o ARM.

Además de realizar la conversión de un tipo de punto flotante a un tipo entero, la función `_ftol` garantiza que el modo de redondeo de la unidad de punto flotante (FPU) se hace a cero (se trunca) mediante el establecimiento de los bits 10 y 11 de la palabra de control. Esto garantiza que la conversión de un tipo de punto flotante en tipo entero se realiza como se describe en la norma ANSI C (la parte fraccionaria del número se descarta). Cuando se utiliza **/QIfist**, esta garantía ya no se aplica. El modo de redondeo será uno de los cuatro documentados en los manuales de referencia de Intel:

- Redondeo al más próximo (número par si está equidistante)

- Redondeo a infinito negativo

- Redondeo a infinito positivo

- Redondeo a cero

Puede utilizar la función [_control87, _controlfp _control87_2 \_](../../c-runtime-library/reference/control87-controlfp-control87-2.md) En tiempo de ejecución para modificar el comportamiento de redondeo de la FPU. El modo de redondeo predeterminado de la FPU es "Redondeo al más próximo". El uso de **/QIfist** puede mejorar el rendimiento de la aplicación, pero no sin riesgo. Debe probar exhaustivamente las partes del código que son sensibles a los modos de redondeo antes de confiar en el código creado con **/QIfist** en entornos de producción.

[/arch (x86)](arch-x86.md) y **/QIfist** no se pueden utilizar en el mismo compilando.

> [!NOTE]
> **/QIfist** no está en vigor de forma predeterminada porque los bits de redondeo también afectan al redondeo de punto flotante a punto flotante (que se produce después de cada cálculo), por lo que cuando se establecen los indicadores para el redondeo de estilo C (hacia cero), los cálculos de punto flotante pueden ser diferentes. **/QIfist** no debe utilizarse si el código depende del comportamiento esperado de truncar la parte fraccionaria del número de punto flotante. Si no está seguro, no utilice **/QIfist**.

La opción **/QIfist** está en desuso a partir de Visual Studio 2005. Se han realizado mejoras importantes en el compilador en cuanto a la velocidad de conversión de los tipos float a int. Para obtener una lista de opciones del compilador en desuso, vea Opciones del compilador en **desuso y quitadas** en [Opciones del compilador enumeradas por categoría](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[/Q (Opciones) (Operaciones de bajo nivel)](q-options-low-level-operations.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
