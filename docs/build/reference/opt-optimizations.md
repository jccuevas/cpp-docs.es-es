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
ms.openlocfilehash: 5c0ab3579fcb9633c435305a8b02b0c3f73d7a6f
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825709"
---
# <a name="opt-optimizations"></a>/OPT (Optimizaciones)

Controla las optimizaciones que efectúa LINK durante una compilación.

## <a name="syntax"></a>Sintaxis

> **/OPT:**{**ref** | **Noref**} \
> **/OPT:**{**ICF**[**=**_iteraciones_] | **NOICF**} \
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumentos

**REF** &#124; **Noref**

**/OPT: Ref** elimina las funciones y los datos a los que nunca se hace referencia; **/OPT: Noref** mantiene las funciones y los datos a los que nunca se hace referencia.

Cuando se habilita/OPT: REF, LINK quita las funciones y los datos empaquetados sin referencia, conocidos como *COMDAT*. Esta optimización se conoce como eliminación transitiva de COMDAT. La opción **/OPT: Ref** también deshabilita la vinculación incremental.

Las funciones insertadas y las funciones miembro definidas dentro de una declaración de clase siempre son COMDAT. Todas las funciones de un archivo objeto se convierten en COMDAT si se compila con la opción [/GY](gy-enable-function-level-linking.md) . Para colocar datos **const** en COMDAT, debe declararlos mediante `__declspec(selectany)`. Para obtener información sobre cómo especificar los datos para su eliminación o plegado, vea [selectany](../../cpp/selectany.md).

De forma predeterminada, **/OPT: Ref** se habilita mediante el enlazador a menos que se especifique **/OPT: Noref** o [/Debug](debug-generate-debug-info.md) . Para invalidar este valor predeterminado y mantener los COMDAT sin referencia en el programa, especifique **/OPT: Noref**. Puede usar la opción [/include](include-force-symbol-references.md) para reemplazar la eliminación de un símbolo específico.

Si se especifica [/Debug](debug-generate-debug-info.md) , el valor predeterminado para **/OPT** es **Noref**y todas las funciones se conservan en la imagen. Para invalidar este valor predeterminado y optimizar una compilación de depuración, especifique **/OPT: Ref**. Esto puede reducir el tamaño del archivo ejecutable y puede ser una optimización útil incluso en las compilaciones de depuración. Se recomienda especificar también **/OPT: NOICF** para conservar las funciones idénticas en las compilaciones de depuración. De este modo, resulta más fácil consultar los seguimiento de pila y establecer puntos de interrupción en las funciones que, de otro modo, estarían contraídas.

**ICF**\[**=**_Iteraciones_de ICF] &#124; **NOICF**

Usar **ICF**\[**=**_iteraciones_de ICF] para realizar un plegamiento de COMDAT idéntico. Las funciones COMDAT redundantes se pueden quitar de la salida del vinculador. El parámetro *ITERATIONS* opcional especifica el número de veces que se recorren los símbolos en busca de duplicados. El número predeterminado de iteraciones es 1. En iteraciones adicionales es posible localizar más duplicados que no se han cubierto mediante el plegamiento de las iteraciones anteriores.

De forma predeterminada, el vinculador habilita **/OPT: ICF** a menos que se especifique **/OPT: NOICF** o [/Debug](debug-generate-debug-info.md) . Para invalidar este valor predeterminado e impedir que los COMDAT se detengan en el programa, especifique **/OPT: NOICF**.

En una compilación de depuración, debe especificar explícitamente **/OPT: ICF** para habilitar el plegamiento de COMDAT. Sin embargo, como **/OPT: ICF** puede combinar datos o funciones idénticos, puede cambiar los nombres de función que aparecen en los seguimientos de la pila. También puede hacer imposible establecer puntos de interrupción en determinadas funciones o examinar algunos datos en el depurador, y puede llevarle a funciones inesperadas al recorrer el código de un solo paso. El comportamiento del código es idéntico, pero la presentación del depurador puede ser muy confusa. Por lo tanto, no se recomienda usar **/OPT: ICF** en las compilaciones de depuración, a menos que las ventajas de código más pequeño superen estas desventajas.

> [!NOTE]
> Dado que **/OPT: ICF** puede hacer que se asigne la misma dirección a distintas funciones o a miembros de datos de solo lectura (es decir, variables **const** cuando se compilan con **/GY**), puede interrumpir un programa que dependa de direcciones únicas para funciones o miembros de datos de solo lectura. Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Las opciones **/OPT: LBR** y **/OPT: NOLBR** solo se aplican a los archivos binarios de ARM. Dado que algunas instrucciones de bifurcación del procesador ARM tienen un intervalo limitado, si el vinculador detecta un salto a una dirección fuera del intervalo, reemplaza la dirección de destino de la instrucción de bifurcación por la dirección de una "isla" de código que contiene una instrucción de bifurcación que tiene como destino el destino real. Puede usar **/OPT: LBR** para optimizar la detección de instrucciones de bifurcación largas y la posición de islas de código intermedio para minimizar el tamaño total del código. **/OPT: NOLBR** indica al enlazador que genere islas de código para las instrucciones de bifurcación largas a medida que se encuentren, sin optimización.

De forma predeterminada, la opción **/OPT: LBR** se establece cuando la vinculación incremental no está habilitada. Si desea un vínculo no incremental pero no optimizaciones de rama largas, especifique **/OPT: NOLBR**. La opción **/OPT: LBR** deshabilita la vinculación incremental.

## <a name="remarks"></a>Observaciones

Cuando se usa en la línea de comandos, el vinculador toma como valor predeterminado **/OPT: Ref, ICF, LBR**. Si se especifica **/Debug** , el valor predeterminado es **/OPT: Noref, NOICF, NOLBR**.

Las optimizaciones **/OPT** normalmente reducen el tamaño de la imagen y aumentan la velocidad del programa. Estas mejoras pueden ser sustanciales en programas más grandes, por lo que están habilitadas de forma predeterminada para las compilaciones comerciales.

La optimización del enlazador tarda más tiempo en completarse, pero el código optimizado también ahorra tiempo cuando el vinculador tiene menos reubicaciones para corregir y crea una imagen final más pequeña, y guarda incluso más tiempo cuando tiene menos información de depuración para procesar y escribir en el archivo PDB. Cuando la optimización está habilitada, puede dar lugar a un tiempo de vínculo más rápido, ya que el menor costo adicional en el análisis puede ser mayor que el desplazamiento por el ahorro de tiempo en el enlazador pasa sobre archivos binarios más pequeños.

Los argumentos **/OPT** se pueden especificar juntos, separados por comas. Por ejemplo, en lugar de **/OPT: Ref/OPT: NOICF**, puede especificar **/OPT: Ref, NOICF**.

Puede usar la opción del vinculador [/verbose](verbose-print-progress-messages.md) para ver las funciones que se quitan mediante **/OPT: Ref** y las funciones que se doblan mediante **/OPT: ICF**.

Los argumentos **/OPT** se establecen a menudo para los proyectos creados con el cuadro de diálogo **nuevo proyecto** en el IDE de Visual Studio y, por lo general, tienen valores diferentes para las configuraciones de depuración y lanzamiento. Si no se establece ningún valor para estas opciones del vinculador en el proyecto, puede obtener los valores predeterminados del proyecto, que pueden ser diferentes de los valores predeterminados que usa el enlazador en la línea de comandos.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:ICF u OPT:REF en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la **Página propiedades** > de configuración de**optimización** del**vinculador** > .

1. Modifique una de estas propiedades:

   - **Habilitar plegamiento de COMDAT**

   - **Referencias**.

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:LBR en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**línea de comandos** del**vinculador** > de **propiedades** > de configuración.

1. Escriba la opción en **opciones adicionales**:

   `/opt:lbr` o `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Consulte también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del vinculador MSVC](linker-options.md)
