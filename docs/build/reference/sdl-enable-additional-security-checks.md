---
title: /sdl (habilitar comprobaciones adicionales de seguridad)
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: 0618b796d492395c3e0e5413047ac0260082baff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318451"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (habilitar comprobaciones adicionales de seguridad)

Agrega las comprobaciones recomendadas del ciclo de vida de desarrollo de seguridad (SDL). Estas comprobaciones incluyen advertencias adicionales relativas a la seguridad como errores y características seguras adicionales de generación de código.

## <a name="syntax"></a>Sintaxis

```
/sdl[-]
```

## <a name="remarks"></a>Comentarios

**/SDL** habilita un supraconjunto de las comprobaciones de seguridad de línea de base proporcionado por [/GS](gs-buffer-security-check.md) e invalida **/GS-**. De forma predeterminada, **/sdl** está desactivada. **/SDL-** deshabilita las comprobaciones de seguridad adicionales.

## <a name="compile-time-checks"></a>Comprobaciones en tiempo de compilación

**/SDL** habilita estas advertencias como errores:

|Advertencia habilitada por /sdl|Modificador equivalente de la línea de comandos|Descripción|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Se aplicó un operador unario menos a un tipo unsigned, lo que produce un resultado sin signo.|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Una constante negativa de tipo entero se convirtió a un tipo sin signo, lo que produce un resultado que posiblemente carece de sentido.|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|El uso de `continue`, `break` o `goto` palabras clave en un `__finally` / `finally` bloque tiene un comportamiento indefinido durante la terminación anormal.|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|El código que inicializa una variable no se ejecuta.|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Uso de una variable local sin inicializar.|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Uso de una variable de puntero local potencialmente no inicializada.|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Saturación del búfer cuando se utilizan funciones específicas de C en tiempo de ejecución (CRT).|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Uso de una función marcada con pragma [en desuso](../../preprocessor/deprecated-c-cpp.md).|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Uso de una función marcada como [en desuso](../../cpp/deprecated-cpp.md).|

## <a name="runtime-checks"></a>Comprobaciones en tiempo de ejecución

Cuando **/sdl** está habilitada, el compilador genera código para realizar estas comprobaciones en tiempo de ejecución:

- Habilita el modo estricto de **/GS** detección de saturación del búfer de tiempo de ejecución, equivale a compilar con `#pragma strict_gs_check(push, on)`.

- Realiza una inmunización de puntero limitada. En las expresiones que no implican desreferenciación y en los tipos que no tienen un destructor definido por el usuario, las referencias de puntero se establecen en una dirección no válida después de una llamada a `delete`. Esto ayuda a evitar la reutilización de las referencias de puntero obsoletas.

- Realiza la inicialización de puntero de miembro de clase. Automáticamente inicializa los miembros de tipo de puntero a la clase **nullptr** en las instancias de objeto (antes de que se ejecute el constructor). Esto ayuda a impedir el uso de punteros no inicializados que el constructor no inicializa explícitamente. Se llama a la inicialización de puntero de miembro generado por el compilador siempre y cuando:

  - El objeto no está asignado mediante un personalizado (definido por el usuario) `operator new`

  - El objeto no está asignado como parte de una matriz (por ejemplo `new A[x]`)

  - La clase no está administrada o importada

  - La clase tiene un constructor predeterminado definido por el usuario.

  Para inicializar la función de inicialización de la clase generada por el compilador, debe ser un miembro de un puntero, no una propiedad o una constante.

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [advertencias, /sdl y mejora de la detección de variables sin inicializar](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **C o C++** carpeta.

1. En el **General** página, seleccione la opción de la **comprobaciones SDL** lista desplegable.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
