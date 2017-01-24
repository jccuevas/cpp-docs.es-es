---
title: "Especificar eventos de compilaci&#243;n | Microsoft Docs"
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
  - "VC.Project.IVCEventTool.CommandLine"
  - "VC.Project.IVCEventTool.ExcludedFromBuild"
  - "VC.Project.IVCEventTool.Description"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "eventos de compilación [C++]"
  - "eventos de compilación [C++], especificar"
  - "compilaciones [C++], personalizar C++"
  - "compilaciones [C++], eventos"
  - "pasos de compilación personalizada [C++], eventos de compilación"
  - "eventos [C++], build"
  - "eventos posteriores a la compilación"
  - "Evento anterior a la vinculación"
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Especificar eventos de compilaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los eventos de compilación pueden utilizarse para especificar comandos que se ejecuten antes de iniciarse la generación, antes del proceso de vinculación o al terminarse la generación.  
  
 Los eventos de compilación sólo se ejecutarán si se han alcanzado correctamente dichos puntos en el proceso de compilación.  Si ocurre un error durante la compilación, no se producirán los eventos *posteriores a la compilación*; si el error se produce antes de la fase de vinculación, no tendrán lugar los eventos *anteriores a la vinculación* ni los *posteriores a la compilación*.  Asimismo, si no es necesario vincular archivos, no se producirán los eventos *anteriores a la vinculación*.  Los eventos *anteriores a la vinculación* tampoco estarán disponibles en los proyectos que no contengan un paso de vinculación.  
  
 Si no es necesario generar archivos, no se producirán eventos de compilación.  
  
 Para obtener información general sobre los eventos de compilación, vea [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md).  
  
### Para especificar un evento de compilación  
  
1.  En el **Explorador de soluciones**, seleccione el proyecto para el que desee especificar el evento de compilación.  
  
2.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
3.  En la carpeta **Eventos de compilación**, seleccione la página de propiedades de un evento de compilación.  
  
4.  Especifique las propiedades asociadas al evento de compilación.  
  
    -   En **Línea de comandos**, especifique un comando como si estuviera especificándolo en el símbolo del sistema.  Especifique un comando o un archivo por lotes válido y los archivos de entrada o salida necesarios.  Especifique el comando por lotes **call** delante del nombre de un archivo por lotes para garantizar la ejecución de todos los comandos posteriores.  
  
         Se pueden especificar varios archivos de entrada y salida simbólicamente con macros MSBuild.  Para obtener información sobre [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)] que especifica la ubicación de archivos o los nombres de conjuntos de archivos, vea [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md).  
  
         Dado que MSBuild tiene reservado el carácter '%', si especifica una variable de entorno, reemplace cada carácter de escape **%** con la secuencia de escape hexadecimal **%25**.  Por ejemplo, reemplace **%WINDIR%** por **%25WINDIR%25**.  MSBuild reemplaza cada secuencia **%25** con el carácter **%** antes de tener acceso a la variable de entorno.  
  
    -   En **Descripción**, escriba una descripción para el evento.  Cuando se produzca el evento, la descripción aparecerá en la **Ventana de salida**.  
  
    -   En **Excluir de la compilación**, especifique **Sí** si no desea que se ejecute el evento.  
  
## Vea también  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)   
 [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)   
 [Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md)