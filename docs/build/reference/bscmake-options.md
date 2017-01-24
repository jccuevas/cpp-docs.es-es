---
title: "Opciones de BSCMAKE | Microsoft Docs"
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
  - "VC.Project.VCBscMakeTool.OutputFile"
  - "VC.Project.VCBscMakeTool.SuppressStartupBanner"
  - "VC.Project.VCBscMakeTool.PreserveSBR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/v: opción de BSCMAKE"
  - "Iu: opción de BSCMAKE"
  - "archivos de información de examen (.bsc), contenido"
  - "/Er: opción de BSCMAKE"
  - "NOLOGO: opción de BSCMAKE"
  - "/s: opción de BSCMAKE"
  - "/Ei: opción de BSCMAKE"
  - "/o: opción de BSCMAKE"
  - "/NOLOGO: opción de BSCMAKE"
  - "/Iu: opción de BSCMAKE"
  - "s: opción de BSCMAKE (/s)"
  - "/Em: opción de BSCMAKE"
  - "Em: opción de BSCMAKE"
  - "Es: opción de BSCMAKE"
  - "archivos [C++], BSCMAKE"
  - "Er: opción de BSCMAKE"
  - "BSCMAKE, opciones para controlar archivos"
  - "controlar opciones de BSCMAKE"
  - "El: opción de BSCMAKE"
  - "/El: opción de BSCMAKE"
  - "/Es: opción de BSCMAKE"
  - "Ei: opción de BSCMAKE"
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Opciones de BSCMAKE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En esta sección se describen las opciones disponibles para controlar BSCMAKE.  Varias opciones controlan el contenido del archivo de información de examen mediante la exclusión o inclusión de cierta información.  Las opciones de exclusión pueden permitir que BSCMAKE se ejecute con mayor rapidez y que se genere un archivo .bsc menor.  Los nombres de opción distinguen entre mayúsculas y minúsculas \(excepto en el caso de **\/HELP** y **\/NOLOGO**\).  
  
 Solo **\/NOLOGO** y **\/o** están disponibles dentro del entorno de desarrollo de Visual Studio.  Vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md) para obtener información sobre el acceso a las páginas de propiedades de un proyecto.  
  
 \/Ei \( `filename`...\)  
 Excluye del archivo de información de examen el contenido de los archivos de inclusión especificados.  Para especificar varios archivos, separe los nombres con un espacio y encierre la lista entre paréntesis.  Los paréntesis no son necesarios si solo se especifica un argumento `filename`.  Utilice **\/Ei** junto con la opción **\/Es** para excluir los archivos no excluidos mediante **\/Es**.  
  
 \/El  
 Excluye los símbolos locales.  La opción predeterminada es incluir los símbolos locales.  Para obtener más información sobre los símbolos locales, vea [Crear un archivo .sbr](../../build/reference/creating-an-dot-sbr-file.md).  
  
 \/Em  
 Excluye los símbolos en el cuerpo de las macros.  Utilice **\/Em** para incluir solo los nombres de macros en el archivo de información de examen.  La opción predeterminada es incluir tanto los nombres de macros como el resultado de las expansiones de macros.  
  
 \/Er \(`symbol`...\)  
 Excluye los símbolos especificados del archivo de información de examen.  Para especificar varios nombres de símbolos, separe los nombres con un espacio y encierre la lista entre paréntesis.  Los paréntesis no son necesarios si solo se especifica un argumento `symbol`.  
  
 \/Es  
 Excluye del archivo de información de examen todos los archivos de inclusión especificados con una ruta de acceso absoluta o que se encuentran en una ruta de acceso absoluta especificada en la variable de entorno INCLUDE. \(Normalmente, estos son los archivos de inclusión del sistema, que contienen gran cantidad de información posiblemente innecesaria en el archivo de información de examen\). Esta opción no excluye los archivos especificados sin una ruta de acceso, los especificados con rutas de acceso relativas ni los que se encuentran en una ruta de acceso relativa en INCLUDE.  Se puede usar la opción **\/Ei** junto con **\/Es** para excluir los archivos que **\/Es** no excluye.  Si solo desea excluir algunos de los archivos que **\/Es** excluye, use **\/Ei** en lugar de **\/Es** y haga una lista de los archivos que se desea excluir.  
  
 \/errorreport:\[none &#124; prompt &#124; queue &#124; send\]  
 Permite enviar información a Microsoft sobre errores internos de bscmake.exe.  
  
 Para obtener más información sobre **\/errorreport**, vea [\/errorReport \(Informar de los errores del compilador\)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 \/HELP  
 Muestra un resumen de la sintaxis de línea de comandos de BSCMAKE.  
  
 \/Iu  
 Incluye los símbolos sin referencia.  De forma predeterminada, BSCMAKE no registra los símbolos definidos a los que no se hace referencia.  Si se ha empaquetado un archivo .sbr, esta opción no afecta a ese archivo de entrada porque el compilador ya ha quitado los símbolos sin referencia.  
  
 \/n  
 Fuerza una compilación no incremental.  Use **\/n** para forzar una compilación completa del archivo de información de examen, ya exista o no un archivo .bsc, y para impedir el truncamiento de los archivos .sbr.  Vea [Cómo compila BSCMAKE un archivo .bsc](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md).  
  
 \/NOLOGO  
 Suprime el mensaje de copyright de BSCMAKE.  
  
 \/o `filename`  
 Especifica un nombre para el archivo de información de examen.  De forma predeterminada, BSCMAKE asigna al archivo de información de examen el mismo nombre base del primer archivo .sbr y una extensión .bsc.  
  
 \/S \( `filename`...\)  
 Indica a BSCMAKE que procese el archivo de inclusión especificado la primera vez que lo encuentre y que lo excluya en otro caso.  Esta opción se utiliza para ahorrar tiempo de procesamiento cuando un archivo \(por ejemplo, un archivo de encabezado o .h para un archivo de código fuente .c o .cpp\) se incluye en varios archivos de código fuente, pero no lo modifican las directivas de preprocesamiento cada vez.  También puede ser conveniente usar esta opción si un archivo sufre cambios que no son importantes para el archivo de información de examen que se está creando.  Para especificar varios archivos, separe los nombres con un espacio y encierre la lista entre paréntesis.  Los paréntesis no son necesarios si solo se especifica un argumento `filename`.  Si se desea excluir el archivo cada vez que se incluye, use la opción **\/Ei** o **\/Es**.  
  
 \/v  
 Proporciona un resultado detallado que incluye el nombre de cada uno de los archivos .sbr que se están procesando e información sobre la ejecución completa de BSCMAKE.  
  
 \/?  
 Muestra un breve resumen de la sintaxis de línea de comandos de BSCMAKE.  
  
 La siguiente línea de comandos indica a BSCMAKE que realice una compilación completa de MAIN.bsc a partir de tres archivos .sbr.  También indica a BSCMAKE que excluya las instancias duplicadas de TOOLBOX.h:  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## Vea también  
 [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)