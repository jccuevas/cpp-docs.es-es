---
title: "/LTCG (Generaci&#243;n de c&#243;digo en tiempo de enlace) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.LinkTimeCodeGeneration"
  - "VC.Project.VCConfiguration.WholeProgramOptimization"
  - "VC.Project.VCCLWCECompilerTool.WholeProgramOptimization"
  - "/ltcg"
  - "VC.Project.VCCLCompilerTool.WholeProgramOptimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LTCG (opción del vinculador)"
  - "generación de código en el vinculador de C++ en tiempo de enlace"
  - "LTCG (opción del vinculador)"
  - "-LTCG (opción del vinculador)"
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LTCG (Generaci&#243;n de c&#243;digo en tiempo de enlace)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LTCG[:INCREMENTAL|:NOSTATUS|:STATUS|:OFF|:PGINSTRUMENT|:PGOPTIMIZE|:PGUPDATE]  
```  
  
## Comentarios  
 :INCREMENTAL \(opcional\)  
 Especifica que el vinculador solo aplica toda la optimización de programa o la generación de código en tiempo de vínculo \(LTCG\) al conjunto de archivos a los que afecta una modificación, en lugar de a todo el proyecto. De forma predeterminada, esta marca no se establece cuando se especifica \/LTCG y el proyecto entero se vincula con la optimización de todo el programa.  
  
 :NOSTATUS &#124; :STATUS \(opcional\)  
 Especifica si el vinculador muestra un indicador de progreso que informa del porcentaje del vínculo que se ha completado. De forma predeterminada, esta información de estado no se muestra.  
  
 :OFF \(opcional\)  
 Deshabilita la generación de código en tiempo de vínculo. Este comportamiento es el mismo que cuando no se especifica \/LTCG en la línea de comandos.  
  
 :PGINSTRUMENT \(opcional\)  
 Esta opción está en desuso. En su lugar, use **\/LTCG** y **\/GENPROFILE** o **\/FASTGENPROFILE** para generar una compilación instrumentada para la optimización guiada por perfiles.  
  
 Los datos que se recopilan de las ejecuciones instrumentadas se utilizan para crear una imagen optimizada. Para más información, vea [Optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md). La forma abreviada de esta opción es \/LTCG:PGI.  
  
 :PGOPTIMIZE \(opcional\)  
 Esta opción está en desuso. En su lugar, use **\/LTCG** y **\/USEPROFILE** para crear una imagen optimizada. Para más información, vea [Optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md). La forma abreviada de esta opción es \/LTCG:PGO.  
  
 :PGUPDATE \(opcional\)  
 Esta opción está en desuso. En su lugar, use **\/LTCG** y **\/USEPROFILE** para crear una imagen optimizada. Para más información, vea [Optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md). La forma abreviada de esta opción es \/LTCG:PGU.  
  
 La opción \/LTCG indica al vinculador que llame al compilador y realice la optimización de todo el programa. También es posible realizar una optimización guiada por perfiles. Para más información, vea [Optimización guiada por perfiles](../../build/reference/profile-guided-optimizations.md).  
  
 Salvo en las siguientes excepciones, no es posible agregar opciones de vinculador a la combinación PGO de \/LTCG y \/USEPROFILE que no se especificaron en la combinación de inicialización PGO anterior de las opciones \/LTCG y \/GENPROFILE:  
  
-   [\/BASE](../../build/reference/base-base-address.md)  
  
-   [\/FIXED](../../build/reference/fixed-fixed-base-address.md)  
  
-   \/LTCG  
  
-   [\/MAP](../../build/reference/map-generate-mapfile.md)  
  
-   [\/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)  
  
-   [\/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)  
  
-   [\/OUT](../../build/reference/out-output-file-name.md)  
  
-   [\/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)  
  
-   [\/PDB](../../build/reference/pdb-use-program-database.md)  
  
-   [\/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)  
  
-   [\/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)  
  
-   [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md)  
  
 Las opciones del vinculador que se especifiquen junto con las opciones\/LTCG y \/GENPROFILE para inicializar la PGO no tienen que especificarse al compilar con \/LTCG y \/USEPROFILE, ya que están implícitas.  
  
 En el resto de este tema se explica \/LTCG con respecto a la generación de código en tiempo de vinculación.  
  
 \/LTCG está implícito con [\/GL](../../build/reference/gl-whole-program-optimization.md).  
  
 El vinculador invoca la generación de código en tiempo de vínculo si se le pasa un módulo que se compiló con **\/GL** o con un módulo MSIL \(vea [.Archivos netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)\). Si no se especifica explícitamente **\/LTCG** al pasar **\/GL** o módulos MSIL al vinculador, el vinculador finalmente lo detecta y se reinicia el vínculo mediante el uso de **\/LTCG**. Especifique explícitamente **\/LTCG** al pasar **\/GL** y módulos MSIL al vinculador para conseguir el rendimiento de compilación más rápido posible.  
  
 Para lograr un rendimiento más rápido, use **\/LTCG:INCREMENTAL**. Esta opción indica al vinculador que solo debe volver a optimizar el conjunto de archivos a los que haya afectado un cambio de archivo de origen, en lugar de todo el proyecto. Esto puede reducir significativamente el tiempo de vínculo necesario. No es la misma opción que la vinculación incremental.  
  
 El uso de **\/LTCG** no es válido con [\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md).  
  
Si **\/LTCG** se usa para vincular módulos compilados con [\/Og](../../build/reference/og-global-optimizations.md), [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) u [\/Ox](../../build/reference/ox-full-optimization.md), se realizan las optimizaciones siguientes:  
  
-   Inserción entre módulos  
  
-   Asignación de registros entre procedimientos \(solo los sistemas operativos de 64 bits\)  
  
-   Convención de llamada personalizada \(solo x86\)  
  
-   Desplazamiento de TLS pequeño \(solo x86\)  
  
-   Alineamiento doble de pila \(solo x86\)  
  
-   Desambiguación de memoria mejorada \(mejor información de interferencias para las variables globales y los parámetros de entrada\)  
  
> [!NOTE]
> El vinculador determina las optimizaciones que se usaron para compilar cada función y aplica las mismas optimizaciones en tiempo de vinculación.  
  
El uso de **\/LTCG** y **\/Ogt** provoca que una optimización de doble alineación.  
  
Si se especifican **\/LTCG** y **\/Ogs**, no se realizará la doble alineación. Si la mayoría de las funciones de una aplicación se compila para conseguir velocidad y solo algunas se compilan para optimizar el tamaño \(por ejemplo, mediante el uso del pragma [optimize](../../preprocessor/optimize.md)\), el compilador realiza un alineamiento doble de las funciones que se optimizan para tamaño si llaman a funciones que requieren una doble alineación.  
  
Si el compilador puede identificar todos los sitios de llamada de una función, el compilador omite los modificadores de convención de llamada explícitos en una función e intenta optimizar la convención de llamada de la función:  
  
-   Se pasan parámetros en los registros  
  
-   Se reordenan parámetros para la alineación  
  
-   Se quitan parámetros sin utilizar  
  
Si se llama a una función a través de un puntero a función o desde fuera de un módulo que se compila con **\/GL**, el compilador no intenta optimizar la convención de llamada de la función.  
  
> [!NOTE]
> Si utiliza **\/LTCG** y vuelve a definir mainCRTStartup, la aplicación puede tener un comportamiento impredecible relacionado con el código de usuario que se ejecute antes de que se inicialicen los objetos globales.  Hay tres formas de solucionar este problema: no redefinir mainCRTStartup, no compilar el archivo que contiene mainCRTStartup mediante **\/LTCG** o inicializar las variables globales y los objetos estáticamente.  
  
## Módulos \/LTCG y MSIL  
Los módulos que se compilan con [\/GL](../../build/reference/gl-whole-program-optimization.md) y [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) pueden utilizarse como entradas del vinculador cuando se especifica **\/LTCG**.  
  
-   **\/LTCG** puede aceptar archivos objeto nativos, archivos objeto nativos o administrados \(compilado mediante **\/clr**\), archivos objeto puros \(compilados con **\/clr:pure**\) y archivos objeto seguros \(compilados mediante **\/clr:safe**\)  
  
-   **\/LTCG** puede aceptar elementos .netmodule seguros, que se pueden crear mediante el uso de **\/clr:safe \/LN** en Visual C\+\+ y **\/target:module** en cualquier otro compilador de Visual Studio.**\/LTCG** no acepta los elementos .netmodule generados mediante **\/clr** o **\/clr:pure**.  
  
-   \/LTCG:PGI no acepta módulos nativos compilados mediante **\/GL** y **\/clr** ni módulos puros \(creados con **\/clr:pure**\)  
  
#### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Propiedades de configuración**.  
  
3.  Seleccione la página de propiedades **General**.  
  
4.  Modifique la propiedad **Optimización de todo el programa**.  
  
También puede aplicar **\/LTCG** a compilaciones concretas si elige **Compilar**, **Optimización guiada por perfiles** en la barra de menús, o si selecciona una de las opciones de Optimización guiada por perfiles del menú contextual del proyecto.  
  
#### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.  
  
## Vea también  
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)