---
title: "/Zo (Mejorar la depuraci&#243;n optimizada) | Microsoft Docs"
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
  - "-Zo"
  - "/Zo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zo opción del compilador [C++]"
  - "Zo opción del compilador [C++]"
  - "-Zo (opción del compilador) [C++]"
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zo (Mejorar la depuraci&#243;n optimizada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera información de depuración mejorada para código optimizado en versiones no depuradas.  
  
## Sintaxis  
  
```cpp  
/Zo[-]  
```  
  
## Comentarios  
 El modificador del compilador **\/Zo** genera información de depuración mejorada para código optimizado.  La optimización puede usar registros para variables locales, reordenar código, vectorizar bucles y llamadas a funciones en línea.  Estas optimizaciones pueden interferir con la relación entre el código fuente y el código de objeto compilado.  El modificador **\/Zo** indica al compilador que genere información adicional de depuración para las variables locales y las funciones insertadas.  Úselo para ver las variables en las ventanas **Automáticos**, **Variables locales** e **Inspección** cuando recorra el código optimizado en el depurador de Visual Studio.  También permite que los seguimientos de pila muestren las funciones inline en el depurador WinDBG.  Las compilaciones de depuración que deshabilitaron las optimizaciones \([\/Od](../../build/reference/od-disable-debug.md)\) no necesitan la información de depuración adicional generada cuando se especifica **\/Zo**.  Use el modificar **\/Zo** para depurar las configuraciones de Liberar con la optimización activada.  Para obtener más información sobre los modificadores de optimización, vea [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md).  La opción **\/Zo** está habilitada de forma predeterminada en Visual Studio 2015 al especificar la información de depuración con **\/Zi** o **\/Z7**.  Especifique **\/Zo\-** para deshabilitar explícitamente esta opción del compilador.  
  
 El modificador **\/Zo** está disponible en Visual Studio 2013 Update 3 y reemplaza al modificador **\/d2Zi\+** no documentado anteriormente.  
  
### Para establecer la opción del compilador \/Zo en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Elija la carpeta **Propiedades de configuración**, **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para que incluya `/Zo` y, luego, elija **Aceptar**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Consulta <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [Editar y continuar](../Topic/Edit%20and%20Continue.md)