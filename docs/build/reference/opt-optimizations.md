---
title: -OPT (optimizaciones) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f8ac107f8a5654601f0c974f82fa83ae6aa83518
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="opt-optimizations"></a>/OPT (Optimizaciones)
Controla las optimizaciones que efectúa LINK durante una compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## <a name="arguments"></a>Argumentos  
 **REF** &AMP;#124; **NOREF**  
 **/ OPT: ref** elimina las funciones y los datos que no se hace referencia a nunca; **/OPT: NOREF** mantiene funciones y datos que nunca se hace referencia.  
  
 Cuando/OPT: ref está habilitado, LINK quita los datos y las funciones empaquetadas. Un objeto contiene funciones empaquetadas y los datos (COMDAT) si se ha compilado mediante el [/Gy](../../build/reference/gy-enable-function-level-linking.md) opción. Esta optimización se conoce como eliminación transitiva de COMDAT. De forma predeterminada, **/OPT: ref** está habilitada en versiones no depuradas. Para invalidar este comportamiento predeterminado y mantener las funciones COMDAT en el programa, especifique **/OPT: NOREF**. Puede usar el [/INCLUDE](../../build/reference/include-force-symbol-references.md) opción para reemplazar la eliminación de un símbolo concreto.  
  
 Cuando **/OPT: ref** está habilitado explícitamente o de forma predeterminada, una forma limitada de **/OPT: ICF** está habilitada que solo contrae las funciones idénticas. Si desea que **/OPT: ref** pero no **/OPT: ICF**, debe especificar **/OPT: REF, NOICF** o **/OPT:NOICF**.  
  
 Si [/DEBUG](../../build/reference/debug-generate-debug-info.md) se especifica, el valor predeterminado de **/OPT** es **NOREF**, y todas las funciones se conservan en la imagen. Para reemplazar este valor predeterminado y optimizar una compilación de depuración, especifique **/OPT: ref**. Dado que **/OPT: ref** implica **/OPT: ICF**, se recomienda que también especifique **/OPT:NOICF** para conservar funciones idénticas en versiones de depuración. De este modo, resulta más fácil consultar los seguimiento de pila y establecer puntos de interrupción en las funciones que, de otro modo, estarían contraídas. El **/OPT: ref** opción deshabilita la vinculación incremental.  
  
 Se debe marcar explícitamente `const` datos como COMDAT; use [__declspec (selectany)](../../cpp/selectany.md).  
  
 Especificar **/OPT: ICF** no habilita la **/OPT: ref** opción.  
  
 **FIREWALL DE WINDOWS [=** `iterations` **] &AMP;#124; NOICF**  
 Use **/OPT: ICF [=**`iterations`**]** para realizar un plegamiento idéntico de COMDAT. Las funciones COMDAT redundantes se pueden quitar de la salida del vinculador. El parámetro opcional `iterations` especifica el número de veces que se recorren los símbolos en busca de duplicados. El número predeterminado de iteraciones es dos. En iteraciones adicionales es posible localizar más duplicados que no se han cubierto mediante el plegamiento de las iteraciones anteriores.  
  
 El vinculador se comporta de manera diferente cuando **/OPT: ref** se especifica, y **ICF** está en vigor de forma predeterminada, que cuando **/OPT: REF, ICF** se especifica explícitamente. La forma de **ICF** que está habilitado con **/OPT: ref** por sí solo no dobla datos de solo lectura: Esto incluye .rdata, .pdata y .xdata. Por tanto, aparecen menos funciones plegadas cuando las imágenes se generan para [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ya que las funciones de estos módulos son más dependientes de los datos de solo lectura, como .pdata y .xdata. Para obtener completa **ICF** plegamiento de comportamiento, especifique explícitamente **/OPT: ICF**.  
  
 Para colocar funciones en comdat, use la **/Gy** opción de compilador; para insertar `const` datos, se declara `__declspec(selectany)`. Para obtener información acerca de cómo especificar datos de plegamiento, consulte [selectany](../../cpp/selectany.md).  
  
 De forma predeterminada, **ICF** está activado si **REF** se encuentra en. Para invalidar este comportamiento predeterminado si **REF** está especificado, utilice **NOICF**. Cuando **/OPT: ref** no se especifica en una compilación de depuración, debe especificar explícitamente **/OPT: ICF** para habilitar el plegamiento de COMDAT. Sin embargo, dado que **/OPT: ICF** puede combinar funciones o datos idénticos, puede cambiar los nombres de función que aparecen en los seguimientos de pila. También puede resultar imposible establecer puntos de interrupción en algunas funciones o examinar algunos datos en el depurador, y podría mostrarle funciones inesperadas al recorrer el código paso a paso. Por lo tanto, no se recomienda que use **/OPT: ICF** en versiones de depuración compilaciones a menos que las ventajas de un código más pequeño compensen estas desventajas.  
  
> [!NOTE]
>  Dado que **/OPT: ICF** puede originar la misma dirección que se asignará a diversas funciones o miembros de datos de solo lectura (`const` variables compiladas mediante **/Gy**), puede interrumpir un programa que depende direcciones únicas de funciones o miembros de datos de solo lectura. Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md).  
  
 **LBR** &AMP;#124; **NOLBR**  
 El **/OPT:LBR** y **/OPT:NOLBR** opciones se aplican sólo a los archivos binarios ARM. Dado que algunas instrucciones de bifurcación del procesador de ARM tienen un intervalo limitado, si el vinculador detecta un salto a una dirección fuera del intervalo, reemplaza la dirección de destino de la instrucción de bifurcación por la dirección de una "isla" de código que contiene una instrucción de bifurcación que apunta al destino real. Puede usar **/OPT:LBR** para optimizar la detección de instrucciones de bifurcación largas y la posición de islas de código intermedio para minimizar el tamaño total del código. **/OPT:NOLBR** indica al vinculador que genere islas de código para obtener instrucciones de bifurcación largas tal como se encuentren, sin optimización.  
  
 De forma predeterminada, el **/OPT:LBR** opción se establece cuando no se habilita la vinculación incremental. Si desea que un vínculo no incremental pero no las optimizaciones de bifurcación largas, especifique **/OPT:NOLBR**. El **/OPT:LBR** opción deshabilita la vinculación incremental.  
  
## <a name="remarks"></a>Comentarios  
 Las optimizaciones normalmente disminuyen el tamaño de la imagen y aumentan la velocidad del programa, a costa de un incremento del tiempo de vinculación.  
  
 Puede usar el [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) opción para ver las funciones que se han quitado mediante **/OPT: ref** y las funciones que se han plegado mediante **/OPT: ICF**.  
  
### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:ICF u OPT:REF en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel izquierdo, expanda **propiedades de configuración**, **vinculador**, **optimización**.  
  
3.  Modifique una de estas propiedades:  
  
    -   **Habilitar plegamiento de COMDAT**  
  
    -   **Referencias**  
  
### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador OPT:LBR en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **vinculador** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Escriba la opción en **opciones adicionales**:  
  
     `/opt:lbr`  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)
