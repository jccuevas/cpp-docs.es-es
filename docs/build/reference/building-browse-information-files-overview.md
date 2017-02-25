---
title: "Compilar archivos de informaci&#243;n de examen: informaci&#243;n general | Microsoft Docs"
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
  - ".bsc (archivos), acerca de los archivos .bsc"
  - "archivos de información de examen (.bsc)"
  - "archivos de información de examen (.bsc), crear"
  - "bsc (archivos), acerca de los archivos bsc"
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Compilar archivos de informaci&#243;n de examen: informaci&#243;n general
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para crear información de examen con la finalidad de examinar símbolos, el compilador crea un archivo .sbr para cada archivo de código fuente del proyecto y, después, BSCMAKE.EXE concatena los archivos .sbr en un archivo .bsc.  
  
 La generación de archivos .sbr y .bsc lleva tiempo y, por tanto, Visual C\+\+ desactiva estas funciones de forma predeterminada.  Para examinar la información de exploración actual se deben activar las opciones de exploración y compilar de nuevo el proyecto.  
  
 Utilice [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) o [\/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) para indicar al compilador que cree archivos .sbr.  Para crear archivos .bsc, puede llamar a [BSCMAKE](../../build/reference/bscmake-command-line.md) desde la línea de comandos.  El uso de BSCMAKE desde la línea de comandos permite controlar con mayor precisión la manipulación de los archivos de información de examen.  Vea [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md) para obtener más información.  
  
> [!TIP]
>  Se puede activar la generación de archivos .sbr y dejar desactivada la generación de archivos .bsc.  De este modo, no sólo se proporcionan generaciones rápidas, sino que también se puede crear rápidamente un archivo .bsc nuevo activando la generación de archivos .bsc y generando el proyecto.  
  
 Se puede reducir el tiempo, la memoria y el espacio de disco necesarios para compilar un archivo .bsc reduciendo el tamaño del archivo .bsc.  
  
 Vea [Página de propiedades General \(Proyecto\)](../../ide/general-property-page-project.md) para obtener información sobre cómo compilar un archivo de explorador en el entorno de desarrollo.  
  
### Para crear un archivo .bsc más pequeño  
  
1.  Utilice [Opciones de la línea de comandos de BSCMAKE](../../build/reference/bscmake-options.md) para excluir información del archivo de información de examen.  
  
2.  Omita los símbolos locales en uno o más archivos .sbr al compilar o ensamblar.  
  
3.  Si un archivo objeto no tiene la información necesaria para la etapa actual de depuración, omita su archivo .sbr del comando BSCMAKE cuando recompile el archivo de información de examen.  
  
### Para combinar la información de examen de varios proyectos en un archivo del explorador \(.bsc\)  
  
1.  No compile el archivo .bsc en el nivel de proyecto ni utilice el modificador \/n para impedir el truncamiento de los archivos .sbr.  
  
2.  Después de compilar todos los proyectos, ejecute BSCMAKE con todos los archivos .sbr como entrada.  Se aceptan caracteres comodín.  Por ejemplo, si dispone de los directorios de proyecto C:\\X, C:\\Y y C:\\Z con archivos .sbr y desea combinar todos ellos en un archivo .bsc, utilice BSCMAKE C:\\X\\\*.sbr C:\\Y\\\* .sbr C:\\Z\\\* \/o c:\\cualquier\_directorio\\combined.bsc para compilar el archivo .bsc combinado.  
  
## Vea también  
 [Herramientas de compilación de C\/C\+\+](../../build/reference/c-cpp-build-tools.md)   
 [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)