---
title: '/Guard: ehcont (habilitar metadatos de continuación EH)'
description: 'Guía de referencia de la opción del compilador/Guard: ehcont de Microsoft C++.'
ms.date: 06/03/2020
f1_keywords:
- /guard:ehcont
- VC.Project.VCCLCompilerTool.GuardEHContMetadata
helpviewer_keywords:
- /guard:ehcont
- /guard:ehcont compiler option
ms.openlocfilehash: e8775b331440e932efb16148ee15acf1c740cd6e
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421363"
---
# <a name="guardehcont-enable-eh-continuation-metadata"></a>/Guard: ehcont (habilitar metadatos de continuación EH)

Habilita la generación de metadatos de continuación EH (EHCONT) por el compilador.

## <a name="syntax"></a>Sintaxis

> **`/guard:ehcont`**[**`-`**]

## <a name="remarks"></a>Observaciones

La **`/guard:ehcont`** opción hace que el compilador genere una lista ordenada de las direcciones virtuales relativas (RVA) de todos los destinos de continuación de control de excepciones válidos para un archivo binario. Se usa durante el tiempo de ejecución para la `NtContinue` `SetThreadContext` validación del puntero de instrucciones y. De forma predeterminada, **`/guard:ehcont`** está desactivado y debe habilitarse explícitamente. Para deshabilitar explícitamente esta opción, use **`/guard:ehcont-`** .

La **`/guard:ehcont`** opción está disponible en la versión 16,7 de Visual Studio 2019 y versiones posteriores. La característica es compatible con los procesos de 64 bits en un sistema operativo de 64 bits.

La [tecnología de aplicación de flujo de control (CET)](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf) es una característica de seguridad basada en hardware que protege frente a ataques basados en la programación orientada a la devolución (ROP). Mantiene una "pila de sombra" para cada pila de llamadas para exigir la integridad del flujo de control.

Cuando hay pilas disponibles para evitar ataques ROPs, los atacantes pasan a usar otras técnicas de ataque. Una técnica que pueden utilizar es dañar el valor del puntero de instrucción dentro de la estructura de [contexto](/windows/win32/api/winnt/ns-winnt-context) . Esta estructura se pasa a las llamadas del sistema que redirigen la ejecución de un subproceso, como `NtContinue` , [`RtlRestoreContext`](/windows/win32/api/winnt/nf-winnt-rtlrestorecontext) y [`SetThreadContext`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadcontext) . La `CONTEXT` estructura se almacena en memoria. Dañar el puntero de instrucción que contiene puede hacer que las llamadas del sistema transfieran la ejecución a una dirección controlada por un atacante. Actualmente, `NTContinue` se puede llamar a con cualquier punto de continuación. Por eso es esencial validar el puntero de instrucción cuando se habilitan las pilas de sombras.

`RtlRestoreContext`y `NtContinue` se usan durante el desenredo de excepciones del control de excepciones estructurado (SEH) para desenredar en el marco de destino que contiene el `__except` bloque. No se espera que el puntero de instrucción del `__except` bloque esté en la pila de instantáneas, ya que se produciría un error en la validación del puntero de instrucción. El **`/guard:ehcont`** modificador del compilador genera una "tabla de continuación EH". Contiene una lista ordenada de las RVA de todos los destinos de continuación de control de excepciones válidos en el archivo binario. `NtContinue`primero comprueba la pila de instantáneas para el puntero de instrucción proporcionado por el usuario y, si no se encuentra el puntero de instrucción, continúa con la comprobación de la tabla de continuación EH del archivo binario que contiene el puntero de instrucción. Si el binario que lo contiene no se compiló con la tabla, puede continuar con la compatibilidad con binarios heredados `NtContinue` . Es importante distinguir entre los archivos binarios heredados que no tienen datos EHCONT y los binarios que contienen datos EHCONT, pero no entradas de tabla. El primero permite todas las direcciones dentro del archivo binario como destinos de continuación válidos. Esta última no permite ninguna dirección dentro del archivo binario como un destino de continuación válido.

La **`/guard:ehcont`** opción debe pasarse tanto al compilador como al vinculador para que genere RVA de destino de continuación EH para un archivo binario. Si el archivo binario se compila mediante un único comando `cl` , el compilador pasa la opción al vinculador. El compilador también pasa la [**`/guard:cf`**](guard-enable-control-flow-guard.md) opción al vinculador. Si compila y vincula por separado, estas opciones se deben establecer en los comandos del compilador y del enlazador.

Puede vincular código compilado mediante **`/guard:ehcont`** a bibliotecas y archivos de objeto compilados sin él. El enlazador devuelve un error irrecuperable en cualquiera de estos escenarios:

- Una sección de código tiene "desenredado local". Para obtener más información, vea terminación anómala en [la instrucción try-finally](../../cpp/try-finally-statement.md#abnormal-termination).

- Una sección EH (XData) contiene punteros a una sección de código y no para SEH.

- Los punteros son para SEH, pero el archivo objeto no se compiló mediante la vinculación de nivel de función ([/GY](gy-enable-function-level-linking.md)) para generar COMDAT.

El enlazador devuelve un error irrecuperable, ya que no puede generar metadatos en estos escenarios. Esto significa que, si se inicia una excepción, es probable que se produzca un bloqueo en tiempo de ejecución.

En el caso de la información de la sección SEH encontrada en COMDAT, pero no compilada con **`/guard:ehcont`** , el vinculador emite la advertencia **LNK4291**. En este caso, el vinculador genera metadatos correctos y conservador para la sección. Para omitir esta advertencia, use [/ignore (omitir advertencias específicas)](ignore-ignore-specific-warnings.md).

Si el vinculador no puede generar metadatos, emite uno de los siguientes errores:

- **`LNK2046`**`: module contains _local_unwind but was not compiled with /guard:ehcont`

- **`LNK2047`**`: module contains C++ EH or complex EH metadata but was not compiled with /guard:ehcont.`

Para comprobar si un archivo binario contiene datos EHCONT, busque los siguientes elementos al volcar la configuración de carga del archivo binario:

```cmd
e:\>link /dump /loadconfig CETTest.exe
...
            10417500 Guard Flags
...
                       EH Continuation table present      // EHCONT guard flag present
...
    0000000180018640 Guard EH continuation table
                  37 Guard EH continuation count          // May be 0 if no exception handling is used in the binary. Still counts has having EHCONT data.
...
    Guard EH Continuation Table                           // List of RVAs

          Address
          --------
           0000000180002CF5
           0000000180002F03
           0000000180002F0A
...
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la **Configuration Properties**página de propiedades de generación de código de  >  **C/C++ y**propiedades de configuración  >  **Code Generation** .

1. Seleccione la propiedad **Habilitar metadatos de continuación de EH** .

1. En el control desplegable, elija **sí (/Guard: ehcont)** para habilitar los metadatos de continuación EH o **no (/Guard: ehcont-)** para deshabilitarlo.

## <a name="see-also"></a>Consulte también

[/Guard (habilitar protección de flujo de control)](guard-enable-control-flow-guard.md)\
[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
