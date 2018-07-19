---
title: /OPT (optimizaciones) | Documentos de Microsoft
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc9f7f66b9bd0ee2c0da65d17eac33e1cbc8c316
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463110"
---
# <a name="opt-optimizations"></a>/OPT (Optimizaciones)

Controla las optimizaciones que efectúa LINK durante una compilación.

## <a name="syntax"></a>Sintaxis

> **/ OPT:**{**REF** | **NOREF**}<br/>
> **/ OPT:**{**ICF**[**=**_iteraciones_] | **NOICF**}<br/>
> **/ OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumentos

**REF** &AMP;#124; **NOREF**

**/ OPT: ref** elimina las funciones y los datos que no se hace referencia a nunca; **/OPT: NOREF** mantiene funciones y datos que nunca se hace referencia.

Cuando/OPT: ref está habilitado, LINK quita las funciones empaquetadas y datos, conocidos como *COMDAT*. Esta optimización se conoce como eliminación transitiva de COMDAT. El **/OPT: ref** opción también deshabilita la vinculación incremental.

Las funciones insertadas y las funciones miembro definidas dentro de una declaración de clase siempre son COMDAT. Todas las funciones en un archivo de objeto se realizan en las funciones COMDAT si se ha compilado mediante el uso de la [/Gy](../../build/reference/gy-enable-function-level-linking.md) opción. Para colocar **const** datos de comdat, debe declarar mediante `__declspec(selectany)`. Para obtener información sobre cómo especificar los datos para su eliminación o doblado, consulte [selectany](../../cpp/selectany.md).

De forma predeterminada, **/OPT: ref** está habilitado el vinculador a menos que **/OPT: NOREF** o [/DEBUG](../../build/reference/debug-generate-debug-info.md) se especifica. Para invalidar este comportamiento predeterminado y mantener las funciones COMDAT en el programa, especifique **/OPT: NOREF**. Puede usar el [/INCLUDE](../../build/reference/include-force-symbol-references.md) opción para reemplazar la eliminación de un símbolo concreto.

Si [/DEBUG](../../build/reference/debug-generate-debug-info.md) se especifica, el valor predeterminado de **/OPT** es **NOREF**, y todas las funciones se conservan en la imagen. Para reemplazar este valor predeterminado y optimizar una compilación de depuración, especifique **/OPT: ref**. Esto puede reducir el tamaño de su archivo ejecutable y puede ser que una optimización útil incluso en versiones de depuración se compila. Se recomienda que también especifique **/OPT:NOICF** para conservar idénticos genera las funciones de depuración. De este modo, resulta más fácil consultar los seguimiento de pila y establecer puntos de interrupción en las funciones que, de otro modo, estarían contraídas.

**ICF**\[**=**_iteraciones_] &#124; **NOICF**

Use **ICF**\[**=**_iteraciones_] para realizar un plegamiento idéntico de COMDAT. Las funciones COMDAT redundantes se pueden quitar de la salida del vinculador. Opcional *iteraciones* parámetro especifica el número de veces que se recorren los símbolos en busca de duplicados. El número predeterminado de iteraciones es 1. En iteraciones adicionales es posible localizar más duplicados que no se han cubierto mediante el plegamiento de las iteraciones anteriores.

De forma predeterminada, **/OPT: ICF** está habilitado el vinculador a menos que **/OPT:NOICF** o [/DEBUG](../../build/reference/debug-generate-debug-info.md) se especifica. Para invalidar este comportamiento predeterminado e impedir que las funciones COMDAT se dobla en el programa, especifique **/OPT:NOICF**.

En una compilación de depuración, debe especificar explícitamente **/OPT: ICF** para habilitar el plegamiento de COMDAT. Sin embargo, dado que **/OPT: ICF** puede combinar funciones o datos idénticos, puede cambiar los nombres de función que aparecen en los seguimientos de pila. Se puede también resultar imposible establecer puntos de interrupción en algunas funciones o examinar algunos datos en el depurador y puede podría mostrarle funciones inesperadas al paso a paso a través de su código. El comportamiento del código es idéntico, pero la presentación del depurador puede ser muy confusa. Por lo tanto, no se recomienda que use **/OPT: ICF** en versiones de depuración compilaciones a menos que las ventajas de un código más pequeño compensen estas desventajas.

> [!NOTE]
> Dado que **/OPT: ICF** puede originar la misma dirección que se asignará a diversas funciones o miembros de datos de solo lectura (es decir, **const** variables cuando se compila utilizando **/Gy**), puede interrumpir un programa que dependa de direcciones únicas de funciones o miembros de datos de solo lectura. Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md).

**LBR** &AMP;#124; **NOLBR**

El **/OPT:LBR** y **/OPT:NOLBR** opciones se aplican sólo a los archivos binarios ARM. Dado que algunas instrucciones de bifurcación del procesador de ARM tienen un intervalo limitado, si el vinculador detecta un salto a una dirección fuera del intervalo, reemplaza la dirección de destino de la instrucción de bifurcación por la dirección de una "isla" de código que contiene una instrucción de bifurcación que apunta al destino real. Puede usar **/OPT:LBR** para optimizar la detección de instrucciones de bifurcación largas y la posición de islas de código intermedio para minimizar el tamaño total del código. **/OPT:NOLBR** indica al vinculador que genere islas de código para obtener instrucciones de bifurcación largas tal como se encuentren, sin optimización.

De forma predeterminada, el **/OPT:LBR** opción se establece cuando no se habilita la vinculación incremental. Si desea que un vínculo no incremental pero no las optimizaciones de bifurcación largas, especifique **/OPT:NOLBR**. El **/OPT:LBR** opción deshabilita la vinculación incremental.

## <a name="remarks"></a>Comentarios

Cuando se usa en la línea de comandos, el vinculador tiene como valor predeterminado **LBR/OPT: REF, ICF,**. Si **/DEBUG** se especifica, el valor predeterminado es **NOLBR/OPT: NOREF, NOICR,**.

El **/OPT** optimizaciones suele reducir el tamaño de la imagen y aumentar la velocidad del sistema. Estas mejoras pueden ser considerables en programas más grandes, que es la razón por la que se habilitan de forma predeterminada para las compilaciones comerciales.

Optimización del vinculador tarda un tiempo adicional por adelantado, pero el código optimizado también ahorra tiempo cuando el vinculador tiene la reubicaciones menos que se corrigen y crea una imagen final más pequeña y guarda incluso más tiempo si tiene menos información de depuración para procesar y escribir en el archivo PDB. Cuando se habilita la optimización, puede provocar un tiempo de vinculación más rápido en general, como el costo adicional pequeño en el análisis puede ser más de desplazamiento en el momento en el ahorro en el vinculador pasa por encima de los archivos binarios más pequeños.

El **/OPT** argumentos se pueden especificar juntos, separados por comas. Por ejemplo, en lugar de **/OPT: REF /OPT:NOICF**, puede especificar **/OPT: REF, NOICF**.

Puede usar el [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) opción del vinculador para ver las funciones que se han quitado mediante **/OPT: ref** y las funciones que se han plegado mediante **/OPT: ICF**.

El **/OPT** argumentos a menudo están establecidos para los proyectos creados mediante el uso de la **nuevo proyecto** cuadro de diálogo en el IDE de Visual Studio, y normalmente tienen valores diferentes para la depuración y configuración de lanzamiento. Si se establece ningún valor para estas opciones del vinculador en el proyecto, puede obtener los valores predeterminados del proyecto, que pueden ser diferentes de los valores predeterminados utilizados por el enlazador en la línea de comandos.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:ICF u OPT:REF en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **optimización** página de propiedades.

1. Modifique una de estas propiedades:

   - **Habilitar plegamiento de COMDAT**

   - **Referencias**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:LBR en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba la opción en **opciones adicionales**:

   `/opt:lbr` o `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)
- [Opciones del vinculador](../../build/reference/linker-options.md)
