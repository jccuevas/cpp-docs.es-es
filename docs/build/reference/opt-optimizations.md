---
title: "/OPT (Optimizaciones) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.OptimizeReferences"
  - "/opt"
  - "VC.Project.VCLinkerTool.OptimizeForWindows98"
  - "VC.Project.VCLinkerTool.EnableCOMDATFolding"
  - "VC.Project.VCLinkerTool.OptimizeFolding"
  - "VC.Project.VCLinkerTool.FoldingIterations"
  - "VC.Project.VCLinkerTool.OptimizeFoldingIterations"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/OPT (opción del vinculador)"
  - "LINK (herramienta) [C++], controlar optimizaciones"
  - "vinculador [C++], optimizaciones"
  - "OPT (opción del vinculador)"
  - "-OPT (opción del vinculador)"
  - "optimización, vinculador"
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# /OPT (Optimizaciones)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controla las optimizaciones que efectúa LINK durante una compilación.  
  
## Sintaxis  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## Argumentos  
 **REF** &#124; **NOREF**  
 **\/OPT:REF** elimina las funciones y los datos a los que nunca se hace referencia; mientras que **\/OPT:NOREF** los mantiene.  
  
 Cuando \/OFT:REF está habilitado, LINK quita los datos y funciones empaquetados que no tienen referencias.  Un objeto contendrá funciones y datos empaquetados \(COMDAT\) si se compiló con la opción [\/Gy](../../build/reference/gy-enable-function-level-linking.md).  Esta optimización se conoce como eliminación transitiva de COMDAT.  De forma predeterminada, **\/OPT:REF** está habilitado en las compilaciones que no son de depuración.  Para reemplazar este valor predeterminado y mantener las funciones COMDAT sin referencias en el programa, especifique **\/OPT:NOREF**.  Se puede usar la opción [\/INCLUDE](../../build/reference/include-force-symbol-references.md) para reemplazar la eliminación de un símbolo concreto.  
  
 Cuando **\/OPT:REF** está habilitado, ya sea explícitamente o de forma predeterminada, se habilita un formulario limitado de **\/OPT:ICF** que solo contrae las funciones idénticas.  Si desea activar **\/OPT:REF** pero no **\/OPT:ICF**, debe especificar **\/OPT:REF,NOICF** u **\/OPT:NOICF**.  
  
 Si se especifica [\/DEBUG](../../build/reference/debug-generate-debug-info.md), el valor predeterminado de **\/OPT** es **NOREF** y se conservan todas las funciones en la imagen.  Para reemplazar este valor predeterminado y optimizar una compilación de depuración, especifique **\/OPT:REF**.  Dado que **\/OPT:REF** implica **\/OPT:ICF**, es recomendable que especifique también **\/OPT:NOICF** para conservar funciones idénticas en versiones de depuración.  De este modo, resulta más fácil consultar los seguimiento de pila y establecer puntos de interrupción en las funciones que, de otro modo, estarían contraídas.  La opción **\/OPT:REF** deshabilita la vinculación incremental.  
  
 Debe marcar explícitamente los datos `const` como COMDAT; use [\_\_declspec\(selectany\)](../../cpp/selectany.md).  
  
 Al especificar **\/OPT:ICF** no se habilita la opción **\/OPT:REF**.  
  
 **ICF\[\=**  `iterations` **\] &#124; NOICF**  
 Utilice **\/OPT:ICF\[\=**`iterations`**\]** para realizar un plegamiento idéntico de COMDAT.  Las funciones COMDAT redundantes se pueden quitar de la salida del vinculador.  El parámetro opcional `iterations` especifica el número de veces que se recorren los símbolos en busca de duplicados.  El número predeterminado de iteraciones es dos.  En iteraciones adicionales es posible localizar más duplicados que no se han cubierto mediante el plegamiento de las iteraciones anteriores.  
  
 El vinculador se comporta de manera diferente cuando se especifica **\/OPT:REF** \(y **ICF** está vigente de forma predeterminada\) que cuando se especifica explícitamente **\/OPT:REF,ICF**.  En el formulario de **ICF** que está habilitado con un único **\/OPT:REF** no se contraen los datos de solo lectura \(esto incluye .rdata, .pdata y .xdata\).  Por tanto, aparecen menos funciones plegadas cuando las imágenes se generan para [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ya que las funciones de estos módulos son más dependientes de los datos de solo lectura, como .pdata y .xdata.  Para obtener el comportamiento de plegamiento completo de **ICF**, especifique explícitamente **\/OPT:ICF**.  
  
 Para colocar funciones en COMDAT, se usa la opción del compilador **\/Gy**; para incluir datos de `const`, se declara `__declspec(selectany)`.  Para obtener información sobre cómo especificar los datos para que se contraigan, vea [selectany](../../cpp/selectany.md).  
  
 De forma predeterminada, la opción **ICF** se activa si la opción **REF** está activada.  Para invalidar este valor predeterminado si se especifica **REF**, utilice **NOICF**.  Cuando no se especifica **\/OPT:REF** en una compilación de depuración, debe especificarse explícitamente **\/OPT:ICF** para habilitar el plegamiento de COMDAT.  Sin embargo, como **\/OPT:ICF** puede combinar funciones o datos idénticos, puede cambiar los nombres de función que aparecen en los seguimientos de la pila.  También puede resultar imposible establecer puntos de interrupción en algunas funciones o examinar algunos datos en el depurador, y podría mostrarle funciones inesperadas al recorrer el código paso a paso.  Por consiguiente, no es recomendable usar **\/OPT:ICF** en las compilaciones de depuración a menos que las ventajas de tener un código más pequeño compensen estas desventajas.  
  
> [!NOTE]
>  Dado que **\/OPT:ICF** puede originar la misma dirección que se va a asignar a diversas funciones o miembros de datos de solo lectura \(variables `const` compiladas con **\/Gy**\), puede interrumpir un programa que dependa de direcciones únicas de funciones o miembros de datos de solo lectura.  Para obtener más información, vea [\/Gy \(Habilitar vinculación en el nivel de función\)](../../build/reference/gy-enable-function-level-linking.md).  
  
 **LBR** &#124; **NOLBR**  
 Las opciones **\/OPT:LBR** y **\/OPT:NOLBR** se aplican solo a los binarios de ARM.  Dado que algunas instrucciones de bifurcación del procesador de ARM tienen un intervalo limitado, si el vinculador detecta un salto a una dirección fuera del intervalo, reemplaza la dirección de destino de la instrucción de bifurcación por la dirección de una "isla" de código que contiene una instrucción de bifurcación que apunta al destino real.  Puede usar **\/OPT:LBR** para optimizar la detección de instrucciones de bifurcación largas y la posición de islas de código intermedio para minimizar el tamaño total del código.  **\/OPT:NOLBR** indica al vinculador que genere islas de código para las instrucciones de bifurcación largas tal como se encuentren, sin optimización.  
  
 De forma predeterminada, la opción **\/OPT:LBR** se establece cuando la vinculación incremental no está habilitada.  Si desea usar un vínculo no incremental pero no desea realizar optimizaciones de bifurcación largas, especifique **\/OPT:NOLBR**.  La opción **\/OPT:LBR** deshabilita la vinculación incremental.  
  
## Comentarios  
 Las optimizaciones normalmente disminuyen el tamaño de la imagen y aumentan la velocidad del programa, a costa de un incremento del tiempo de vinculación.  
  
 Puede utilizar la opción [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md) para ver las funciones que se han quitado mediante **\/OPT:REF** y las funciones que se han plegado mediante **\/OPT:ICF**.  
  
### Para establecer la opción del vinculador OPT:ICF u OPT:REF en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En el panel izquierdo, expanda **Propiedades de configuración**, **Vinculador** y **Optimización**.  
  
3.  Modifique una de estas propiedades:  
  
    -   **Habilitar plegamiento de COMDAT**  
  
    -   **Referencias**  
  
### Para establecer la opción del vinculador OPT:LBR en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en **Opciones adicionales**:  
  
     `/opt:lbr`  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)