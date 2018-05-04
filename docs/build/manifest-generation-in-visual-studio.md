---
title: Generación de manifiestos en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73b5cbe631d078dd6ee27b4f7e0a97503c36638b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="manifest-generation-in-visual-studio"></a>Generación de manifiestos en Visual Studio
Generación de un archivo de manifiesto para un proyecto concreto puede controlarse en el proyecto **páginas de propiedades** cuadro de diálogo. En el **propiedades de configuración** , haga clic en **vinculador**, a continuación, **archivo de manifiesto**, a continuación, **Generar manifiesto**. De forma predeterminada, las propiedades del proyecto de los nuevos proyectos se establecen para generar un archivo de manifiesto. Sin embargo es posible deshabilitar la generación del manifiesto para un proyecto mediante el **Generar manifiesto** propiedad del proyecto. Cuando esta propiedad se establece en **Sí**, se genera el manifiesto para este proyecto. En caso contrario, el vinculador omite la información de ensamblado al resolver dependencias del código de aplicación y no genera el manifiesto.  
  
 El sistema de compilación en Visual Studio permite que el manifiesto se incrusta en el archivo de aplicación binario final, o se genera como un archivo externo. Este comportamiento se controla mediante la **incrustar manifiesto** opción en el **propiedades del proyecto** cuadro de diálogo. Para establecer esta propiedad, abra el **herramienta manifiesto** nodo, a continuación, seleccione **de entrada y salida**. Si no se incrusta el manifiesto, se genera como un archivo externo y se guarda en el mismo directorio que el archivo binario final. Si el manifiesto está incrustado, Visual Studio incrusta los manifiestos finales mediante el proceso siguiente:  
  
1.  Una vez compilado el código fuente en los archivos objeto, el vinculador recopila información de ensamblado dependiente. Al vincular el archivo binario final, el vinculador genera un manifiesto intermedio que se utilizará posteriormente para generar el manifiesto final.  
  
2.  Una vez finalizadas el manifiesto intermedio y la vinculación, se ejecutará la herramienta manifiesto para combinar un manifiesto final y guardarlo como un archivo externo.  
  
3.  El proyecto de sistema de compilación, a continuación, se detecta si el manifiesto generado por la herramienta manifiesto contiene información diferente que el manifiesto ya incrustado en el archivo binario.  
  
4.  Si el manifiesto incrustado en el archivo binario es diferente del manifiesto generado por la herramienta manifiesto, o el archivo binario no contiene un manifiesto incrustado, Visual Studio llamará al vinculador una vez más para incrustar el archivo de manifiesto externo dentro del archivo binario como un recurso.  
  
5.  Si el manifiesto incrustado en el archivo binario es el mismo que el manifiesto generado por la herramienta manifiesto, la compilación continuará con los siguientes pasos de compilación.  
  
 El manifiesto está incrustado en el archivo binario final como un recurso de texto y se puede ver abriendo el archivo binario final como un archivo en Visual Studio. Para asegurarse de que el manifiesto señala a las bibliotecas correctas, siga los pasos descritos en [descripción de las dependencias de una aplicación de Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) o siga las sugerencias que se describe en el [desolucióndeproblemas](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) sección.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: incrustar un manifiesto en una aplicación de C/C ++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [Acerca de ensamblados privados](http://msdn.microsoft.com/library/ff951638)   
 [Herramienta manifiesto](http://msdn.microsoft.com/library/aa375649)   
 [Introducción a la generación de manifiestos para los programas de C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)