---
title: /OPT (Optimizaciones)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: b25db4d6c260c3c6751de293aa2a82df8aa05e7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336222"
---
# <a name="opt-optimizations"></a>/OPT (Optimizaciones)

Controla las optimizaciones que efectúa LINK durante una compilación.

## <a name="syntax"></a>Sintaxis

> **/OPT:**-**REF** | **NOREF**?<br/>
> **/OPT:****ICF****=**[_iteraciones_] **NOICF**?<br/>
> **/OPT:**-**LBR** | **NOLBR**?

## <a name="arguments"></a>Argumentos

**REF** &#124; **NOREF**

**/OPT:REF** elimina funciones y datos a los que nunca se hace referencia; **/OPT:NOREF** mantiene funciones y datos a los que nunca se hace referencia.

Cuando /OPT:REF está habilitado, LINK quita las funciones y los datos empaquetados sin referencia, conocidos como *COMDAT*. Esta optimización se conoce como eliminación transitiva de COMDAT. La opción **/OPT:REF** también deshabilita la vinculación incremental.

Las funciones insertadas y las funciones miembro definidas dentro de una declaración de clase siempre son COMDAT. Todas las funciones de un archivo de objeto se convierten en COMDAT si se compila mediante la opción [/Gy.](gy-enable-function-level-linking.md) Para colocar datos **const** en COMDAT, debe `__declspec(selectany)`declararlos mediante . Para obtener información sobre cómo especificar los datos para la eliminación o el plegado, consulte [selectany](../../cpp/selectany.md).

De forma predeterminada, el vinculador habilita **/OPT:REF** a menos que se especifique **/OPT:NOREF** o [/DEBUG.](debug-generate-debug-info.md) Para invalidar este valor predeterminado y mantener los COMDAT sin referencia en el programa, especifique **/OPT:NOREF**. Puede utilizar la opción [/INCLUDE](include-force-symbol-references.md) para anular la eliminación de un símbolo específico.

Si se especifica [/DEBUG,](debug-generate-debug-info.md) el valor predeterminado para **/OPT** es **NOREF**y todas las funciones se conservan en la imagen. Para invalidar este valor predeterminado y optimizar una compilación de depuración, especifique **/OPT:REF**. Esto puede reducir el tamaño del ejecutable y puede ser una optimización útil incluso en compilaciones de depuración. Se recomienda especificar también **/OPT:NOICF** para conservar funciones idénticas en compilaciones de depuración. De este modo, resulta más fácil consultar los seguimiento de pila y establecer puntos de interrupción en las funciones que, de otro modo, estarían contraídas.

**Iteraciones ICF**\[**=**_iterations_] &#124; **NOICF**

Utilice_iteraciones_ **ICF**\[**=**] para realizar plegado COMDAT idéntico. Las funciones COMDAT redundantes se pueden quitar de la salida del vinculador. El parámetro *de iteraciones* opcional especifica el número de veces que se recorren los símbolos de los duplicados. El número predeterminado de iteraciones es 1. En iteraciones adicionales es posible localizar más duplicados que no se han cubierto mediante el plegamiento de las iteraciones anteriores.

De forma predeterminada, **/OPT:ICF** está habilitado por el vinculador a menos que se especifique **/OPT:NOICF** o [/DEBUG.](debug-generate-debug-info.md) Para invalidar este valor predeterminado y evitar que los COMDAT se plieguen en el programa, especifique **/OPT:NOICF**.

En una compilación de depuración, debe especificar explícitamente **/OPT:ICF** para habilitar el plegado COMDAT. Sin embargo, dado **que /OPT:ICF** puede combinar datos o funciones idénticos, puede cambiar los nombres de función que aparecen en los seguimientos de pila. También puede hacer que sea imposible establecer puntos de interrupción en ciertas funciones o examinar algunos datos en el depurador, y puede llevarle a funciones inesperadas al recorrer el código en un solo paso. El comportamiento del código es idéntico, pero la presentación del depurador puede ser muy confusa. Por lo tanto, no se recomienda usar **/OPT:ICF** en compilaciones de depuración a menos que las ventajas de código más pequeño superen estas desventajas.

> [!NOTE]
> Dado que **/OPT:ICF** puede hacer que la misma dirección se asigne a diferentes funciones o miembros de datos de solo lectura (es decir, **variables const** cuando se compila mediante **/Gy**), puede interrumpir un programa que depende de direcciones únicas para funciones o miembros de datos de solo lectura. Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Las opciones **/OPT:LBR** y **/OPT:NOLBR** solo se aplican a los archivos binarios ARM. Dado que ciertas instrucciones de bifurcación del procesador ARM tienen un intervalo limitado, si el vinculador detecta un salto a una dirección fuera de rango, reemplaza la dirección de destino de la instrucción de bifurcación por la dirección de un código "isla" que contiene una instrucción de bifurcación que tiene como destino el destino real. Puede usar **/OPT:LBR** para optimizar la detección de instrucciones de bifurcación largas y la colocación de islas de código intermedias para minimizar el tamaño total del código. **/OPT:NOLBR** indica al vinculador que genere islas de código para instrucciones de rama largas a medida que se encuentran, sin optimización.

De forma predeterminada, la opción **/OPT:LBR** se establece cuando la vinculación incremental no está habilitada. Si desea un vínculo no incremental pero no optimizaciones de ramas largas, especifique **/OPT:NOLBR**. La opción **/OPT:LBR** deshabilita la vinculación incremental.

## <a name="remarks"></a>Observaciones

Cuando se utiliza en la línea de comandos, el vinculador tiene como valor predeterminado **/OPT:REF,ICF,LBR**. Si se especifica **/DEBUG,** el valor predeterminado es **/OPT:NOREF,NOICF,NOLBR**.

Las optimizaciones **/OPT** generalmente disminuyen el tamaño de la imagen y aumentan la velocidad del programa. Estas mejoras pueden ser sustanciales en programas más grandes, por lo que están habilitadas de forma predeterminada para compilaciones minoristas.

La optimización del vinculador toma tiempo adicional por adelantado, pero el código optimizado también ahorra tiempo cuando el vinculador tiene menos reubicaciones para corregir y crea una imagen final más pequeña, y ahorra aún más tiempo cuando tiene menos información de depuración para procesar y escribir en la PDB. Cuando la optimización está habilitada, puede dar lugar a un tiempo de enlace más rápido en general, ya que el pequeño costo adicional en el análisis puede ser más que compensado por el ahorro de tiempo en los desplazamientos del vinculador sobre binarios más pequeños.

Los argumentos **/OPT** se pueden especificar juntos, separados por comas. Por ejemplo, en lugar de **/OPT:REF /OPT:NOICF**, puede especificar **/OPT:REF,NOICF**.

Puede utilizar la opción del vinculador [/VERBOSE](verbose-print-progress-messages.md) para ver las funciones que se quitan mediante **/OPT:REF** y las funciones plegadas por **/OPT:ICF**.

Los argumentos **/OPT** a menudo se establecen para los proyectos creados mediante el cuadro de diálogo **Nuevo proyecto** en el IDE de Visual Studio y, por lo general, tienen valores diferentes para las configuraciones de depuración y versión. Si no se establece ningún valor para estas opciones del vinculador en el proyecto, puede obtener los valores predeterminados del proyecto, que pueden ser diferentes de los valores predeterminados utilizados por el vinculador en la línea de comandos.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:ICF u OPT:REF en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**Optimización** del > **vinculador** > de propiedades de **configuración.**

1. Modifique una de estas propiedades:

   - **Habilitar plegamiento de COMDAT**

   - **Referencias**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:LBR en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades de la línea de**comandos** del**vinculador** > de propiedades > de **configuración.**

1. Introduzca la opción En **Opciones adicionales:**

   `/opt:lbr` o `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Consulte también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones de MSVC Linker](linker-options.md)
