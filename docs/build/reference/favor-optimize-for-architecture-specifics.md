---
title: "/favor (optimizar para valores espec&#237;ficos de la arquitectura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/favor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-favor (opción del compilador) [C++]"
  - "/favor (opción del compilador) [C++]"
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
caps.latest.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# /favor (optimizar para valores espec&#237;ficos de la arquitectura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/favor:** `option` produce código optimizado para una arquitectura concreta o para las características de micro\- arquitecturas en AMD y arquitecturas de Intel.  
  
## Sintaxis  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## Comentarios  
 **\/favor:blend**  
 \(x86 y x64\) produce código optimizado para las características de micro\- arquitecturas en AMD y arquitecturas de Intel.  Mientras **\/favor:blend** no puede dar el máximo rendimiento posible en un procesador concreto, está diseñado para proporcionar el máximo rendimiento a través de un gran número de procesadores x86 y x64.  De forma predeterminada, **\/favor:blend** está vigente.  
  
 **\/favor:ATOM**  
 \(x86 y x64\) produce código optimizado para las características del procesador y de Intel Centrino Atom Processor Technology Intel Atom.  El código que se genera mediante **\/favor:ATOM** también puede mostrar las instrucciones de Intel SSSE3, de SSE3, de SSE2, y de SSE para los procesadores Intel.  
  
 **\/favor:AMD64**  
 \(x64 solamente\) optimiza el código generado para AMD Opteron, y procesadores de Athlon que admiten extensiones de 64 bits.  El código optimizado puede ejecutarse en todas las plataformas compatible x64.  El código que se genera mediante **\/favor:AMD64** puede provocar un rendimiento peor en los procesadores Intel que Intel64 admiten.  
  
 **\/favor:INTEL64**  
 \(x64 solamente\) optimiza el código generado para los procesadores Intel que Intel64 admiten, que produce normalmente mejor rendimiento para esa plataforma.  El código resultante puede ejecutarse en cualquier plataforma x64.  El código que se genera con **\/favor:INTEL64** podría producir rendimiento peor en AMD Opteron, y procesadores de Athlon que admiten extensiones de 64 bits.  
  
> [!NOTE]
>  La arquitectura de Intel64 se conocía anteriormente como Tecnología de Memoria Extendida 64 \(EM64T\), y la opción del compilador correspondiente era **\/favor:EM64T**.  
  
 Para obtener información sobre cómo programar para la arquitectura de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] , vea [Convenciones de software x64](../../build/x64-software-conventions.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro de **Opciones adicionales** .  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)