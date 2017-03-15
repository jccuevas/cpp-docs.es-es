---
title: "Generaci&#243;n de manifiestos en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "manifiestos [C++]"
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Generaci&#243;n de manifiestos en Visual Studio
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La generación de un archivo de manifiesto para un proyecto determinado se puede controlar en el cuadro de diálogo **Páginas de propiedades** del proyecto.  En la ficha **Propiedades de configuración**, haga clic en **Vinculador**, en **Archivo de manifiesto** y, finalmente, en **Generar manifiesto**.  De manera predeterminada, las propiedades del proyecto de los nuevos proyectos se establecen para generar un archivo de manifiesto.  Sin embargo, es posible deshabilitar la generación del manifiesto para un proyecto mediante la propiedad **Generar manifiesto** del proyecto.  Cuando esta propiedad se establece en **Sí**, se genera el manifiesto para este proyecto.  En caso contrario, el vinculador omite la información del ensamblado al resolver dependencias del código de aplicación y no genera el manifiesto.  
  
 El sistema de compilación de Visual Studio permite incrustar el manifiesto en el archivo de aplicación binario final, o bien generarlo como archivo externo.  La opción **Incrustar manifiesto** controla este comportamiento en el cuadro de diálogo **Propiedades del proyecto**.  Para establecer esta propiedad, abra el nodo **Herramienta Manifiesto** y, a continuación, seleccione **Entrada y salida**.  Si no se incrusta el manifiesto, se genera como archivo externo y se guarda en el mismo directorio que el archivo binario final.  Si se incrusta el manifiesto, Visual Studio incrusta los manifiestos finales mediante el proceso siguiente:  
  
1.  Después de que el código fuente se compile para convertirse en archivos objeto, el vinculador recoge la información de ensamblado dependiente.  Al vincular el archivo binario final, el vinculador genera un manifiesto intermedio que se utiliza posteriormente para generar el manifiesto final.  
  
2.  Después de finalizar el manifiesto intermedio y la vinculación, se ejecuta la herramienta Manifiesto para combinar un manifiesto final y guardarlo como archivo externo.  
  
3.  El sistema de compilación de proyectos detecta a continuación si el manifiesto generado por la herramienta Manifiesto contiene información diferente a la del manifiesto ya incrustado en el archivo binario.  
  
4.  Si el manifiesto incrustado en el archivo binario es diferente del manifiesto generado por la herramienta Manifiesto, o si el archivo binario no contiene un manifiesto incrustado, Visual Studio llamará al vinculador una vez más para incrustar el archivo de manifiesto externo dentro del archivo binario como recurso.  
  
5.  Si el manifiesto incrustado en el archivo binario es el mismo que el manifiesto generado por la herramienta Manifiesto, la compilación continuará realizando los pasos siguientes de compilación.  
  
 El manifiesto se incrusta dentro del archivo binario final como recurso de texto y se puede ver abriendo el archivo binario final como archivo en Visual Studio.  Para asegurarse de que el manifiesto señala a las bibliotecas correctas, siga los pasos descritos en [Descripción de las dependencias de una aplicación de Visual C\+\+](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) o las sugerencias descritas en la sección [Solución de problemas](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
## Vea también  
 [Cómo: Incrustar un manifiesto en una aplicación de C\/C\+\+](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [Ensamblados privados](_win32_private_assemblies)   
 [Herramienta Manifiesto](http://msdn.microsoft.com/library/aa375649)   
 [Introducción a la generación de manifiestos para los programas de C\/C\+\+](../build/understanding-manifest-generation-for-c-cpp-programs.md)