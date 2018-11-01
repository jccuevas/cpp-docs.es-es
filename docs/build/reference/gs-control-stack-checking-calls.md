---
title: /Gs (Controlar llamadas de comprobación de la pila)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: 52e203380045c3e23b04950cb241176f10321c2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646485"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (Controlar llamadas de comprobación de la pila)

Controla el umbral para las comprobaciones de la pila.

## <a name="syntax"></a>Sintaxis

> **/GS**[*tamaño*]

## <a name="arguments"></a>Argumentos

*size*<br/>
(Opcional) Número de bytes que pueden ocupar las variables locales antes de que se inicie un sondeo de pila. Se permite ningún espacio entre **/Gs** y *tamaño*.

## <a name="remarks"></a>Comentarios

Un *sondeo de pila* es una secuencia de código que el compilador inserta al principio de una llamada de función. Cuando se inicia un sondeo de pila, se introduce en la memoria sin causar conflictos, en la cantidad de espacio necesaria para almacenar las variables locales de la función. Esto hace que el sistema operativo en la página de forma transparente en la memoria de pila adicional si es necesario, antes de que se ejecuta el resto de la función.

De forma predeterminada, el compilador genera código que inicia un sondeo de pila cuando una función requiere más de una página de espacio de pila. Esto es equivalente a una opción del compilador de **/Gs4096** para x86, x 64, ARM, ARM64 plataformas y. Este valor permite a una aplicación y al administrador de memoria de Windows aumentar la cantidad de memoria asignada dinámicamente a la pila del programa en tiempo de ejecución.

> [!NOTE]
> El valor predeterminado de **/Gs4096** permite que la pila de aplicaciones para Windows aumente correctamente en tiempo de ejecución del programa. Le recomendamos que no cambie el valor predeterminado, excepto si sabe exactamente por qué tiene que cambiarlo.

Algunos programas, como los controladores de dispositivos virtuales, no requieren este mecanismo predeterminado de aumento de la pila. En tales casos, los sondeos de pila no son necesarios y puede impedir el compilador genere configurando *tamaño* en un valor mayor que requerirán las funciones de almacenamiento de variables locales.

**/ Gs0** inicia sondeos para cada llamada de función que requiere el almacenamiento para las variables locales de la pila. Esto puede afectar negativamente al rendimiento.

Para x64 tiene como destino, si la **/Gs** opción se especifica sin un *tamaño* argumento, es el mismo que **/Gs0**. Si el *tamaño* argumento es de 1 a 9, se genera la advertencia D9014 y el efecto es lo mismo que especificar **/Gs0**.

Para x86, ARM, ARM64 objetivos y el **/Gs** opción sin un *tamaño* argumento es igual a **/Gs4096**. Si el *tamaño* argumento es de 1 a 9, se genera la advertencia D9014 y el efecto es lo mismo que especificar **/Gs4096**.

Para todos los destinos, un *tamaño* argumento entre 10 y 2147485647 establece el umbral en el valor especificado. Un *tamaño* de error irrecuperable C1049 de causas 2147485648 o superior.

Puede activar o desactivar las comprobaciones de la pila mediante la [check_stack](../../preprocessor/check-stack.md) directiva. **/GS** y `check_stack` pragma no tienen ningún efecto en las rutinas de biblioteca de C estándar; afectan a solo las funciones que se compilan.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Escriba el **/Gs** opción del compilador y un tamaño opcional en **opciones adicionales**. Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)