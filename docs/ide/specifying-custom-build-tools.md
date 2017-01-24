---
title: "Especificar las herramientas de compilaci&#243;n personalizadas | Microsoft Docs"
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
  - "VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets"
  - "VC.Project.VCCustomBuildTool.Outputs"
  - "VC.Project.VCCustomBuildTool.Command"
  - "VC.Project.VCCustomBuildTool.CommandLine"
  - "VC.Project.VCCustomBuildTool.AdditionalDependencies"
  - "VC.Project.VCCustomBuildTool.Message"
  - "VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets"
  - "VC.Project.VCCustomBuildTool.Description"
  - "VC.Project.VCCustomBuildTool.AdditionalInputs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "herramientas de compilación (C++), especificar"
  - "compilaciones (C++), herramientas de compilación personalizadas"
  - "herramientas de compilación personalizadas (C++), especificar"
ms.assetid: e5161946-8002-418d-991e-219e6a8586f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Especificar las herramientas de compilaci&#243;n personalizadas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una *herramienta de compilación personalizada* proporciona al sistema de compilación la información que necesita para compilar archivos de entrada específicos.  Una herramienta de compilación personalizada especifica un comando que se va a ejecutar, una lista de archivos de entrada, una lista de archivos de salida que genera el comando y una descripción opcional de la herramienta.  
  
 Para obtener más información acerca de las herramientas y los pasos de compilación personalizados, vea [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md).  
  
### Para especificar una herramienta de compilación personalizada  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../ide/working-with-project-properties.md).  
  
2.  Haga clic en **Propiedades de configuración** para habilitar el cuadro **Configuración**.  En el cuadro **Configuración**, seleccione la configuración para la que desee especificar una herramienta de compilación personalizada.  
  
3.  En el **Explorador de soluciones**, seleccione el archivo de entrada para la herramienta de compilación personalizada.  
  
     Si no aparece la carpeta **Herramienta de compilación personalizada**, significa que la extensión de archivo del archivo seleccionado está asociada a una herramienta predeterminada.  Por ejemplo, la herramienta predeterminada de los archivos .c y .cpp es el compilador.  Para reemplazar una configuración de herramienta predeterminada, en el nodo **Propiedades de configuración**, en la carpeta **General**, en la propiedad **Tipo de elemento**, haga clic en **Herramienta de compilación personalizada**.  Haga clic en **Aplicar** para que se muestre el nodo **Herramienta de compilación personalizada**.  
  
4.  En el nodo **Herramienta de compilación personalizada**, en la carpeta **General**, especifique las propiedades asociadas a la herramienta de compilación personalizada:  
  
    -   En **Dependencias adicionales**, especifique los archivos adicionales además del archivo para el que se esté definiendo la herramienta de compilación personalizada \(el archivo asociado a la herramienta de compilación personalizada se considera implícitamente una entrada de la herramienta\).  Los archivos de entrada adicionales no son necesarios para especificar una herramienta de compilación personalizada.  Si hay varias entradas adicionales, deberá separarlas con punto y coma.  
  
         Si la fecha de un archivo de **Dependencias adicionales** es posterior a la del archivo de entrada, se ejecuta la herramienta de compilación personalizada.  Si todos los archivos de **Dependencias adicionales** son anteriores al archivo de entrada y este es anterior al archivo de propiedades **Resultados**, no se ejecuta la herramienta de compilación personalizada.  
  
         Por ejemplo, suponga tiene una herramienta de compilación personalizada que toma MyInput.x como entrada y genera MyInput.cpp, que incluye un archivo de encabezado, MyHeader.h.  Puede especificar MyHeader.h como una dependencia de entrada para MyInput.x y el sistema de compilación compilará MyInput.cpp cuando esté anticuado con respecto a MyInput.x o MyHeader.h.  
  
         Las dependencias de entrada también pueden asegurar la ejecución de las herramientas de compilación personalizadas en el orden necesario.  En el ejemplo anterior, suponga que MyHeader.h es, en realidad, el resultado de una herramienta de compilación personalizada.  Dado que MyHeader.h es una dependencia de MyInput.x, el sistema de compilación, antes de ejecutar la herramienta de compilación personalizada en MyInput.x, compilará Myheader.h.  
  
    -   En **Línea de comandos**, especifique un comando como si estuviera especificándolo en el símbolo del sistema.  Especifique un comando o un archivo por lotes válido y los archivos de entrada o salida necesarios.  Especifique el comando por lotes **call** delante del nombre de un archivo por lotes para garantizar la ejecución de todos los comandos posteriores.  
  
         Se pueden especificar varios archivos de entrada y salida simbólicamente con macros MSBuild.  Para obtener información sobre [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)] que especifica la ubicación de archivos o los nombres de conjuntos de archivos, vea [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md).  
  
         Dado que MSBuild tiene reservado el carácter '%', si especifica una variable de entorno, reemplace cada carácter de escape **%** con la secuencia de escape hexadecimal **%25**.  Por ejemplo, reemplace **%WINDIR%** por **%25WINDIR%25**.  MSBuild reemplaza cada secuencia **%25** con el carácter **%** antes de tener acceso a la variable de entorno.  
  
    -   En **Descripción**, escriba un mensaje descriptivo sobre esta herramienta de compilación personalizada.  Cuando el sistema de compilación procesa la herramienta, este mensaje aparece en la **Ventana de salida**.  
  
    -   En **Resultados**, especifique el nombre del archivo de salida.  Esta entrada es obligatoria; si esta propiedad no tiene un valor, la herramienta de compilación personalizada no se ejecutará.  Si una herramienta de compilación personalizada tiene varios resultados, deberá separar los nombres de los archivos con punto y coma.  
  
         El nombre del archivo de salida debe ser el mismo que se especificó en la propiedad **Línea de comandos**.  El sistema de compilación del proyecto buscará el archivo y comprobará su fecha.  Si el archivo de salida es más reciente que el archivo de entrada o no se encuentra, se ejecuta la herramienta de compilación personalizada.  Si todos los archivos de **Dependencias adicionales** son anteriores al archivo de entrada y este es anterior al archivo especificado en la propiedad **Resultados**, no se ejecuta la herramienta de compilación personalizada.  
  
 Si desea que el sistema de compilación actúe en un archivo de salida generado por la herramienta de compilación personalizada, deberá agregarlo manualmente al proyecto.  La herramienta de compilación personalizada actualizará el archivo durante la compilación.  
  
## Ejemplo  
 Suponga que desea incluir en su proyecto un archivo denominado parser.l.  Desea que un analizador léxico procese parser.l para generar un archivo .c que tenga el mismo nombre base \(parser.c\).  
  
 En primer lugar, agregue parser.l y parser.c al proyecto.  Si los archivos todavía no existen, simplemente agregue una referencia a ellos.  Cree una herramienta de compilación personalizada para parser.l y escriba lo siguiente en la propiedad **Comandos**:  
  
```  
lexer %(FullPath) .\%(Filename).c  
```  
  
 Este comando ejecuta el analizador léxico sobre parser.l y produce parser.c en el directorio del proyecto.  
  
 En la propiedad **Resultados**, escriba lo siguiente:  
  
```  
.\%(Filename).c  
```  
  
 Al compilar el proyecto, el sistema de compilación compara las marcas de tiempo de parser.l y parser.c.  Si parser.l es más reciente, o si parser.c no existe, el sistema de compilación ejecuta el valor de propiedad **Línea de comandos** para actualizar parser.c.  Al estar parser.c también agregado al proyecto, el sistema de compilación lo compila.  
  
## Vea también  
 [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)   
 [Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md)