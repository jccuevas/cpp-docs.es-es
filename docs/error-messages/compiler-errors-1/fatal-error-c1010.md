---
title: "Error irrecuperable C1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1010"
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error irrecuperable C1010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

final de archivo inesperado al buscar la directiva de encabezado precompilado.Compruebe si olvidó agregar '\#include nombre' al código fuente?  
  
 Un archivo de inclusión especificado con [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) no aparece enumerado en el archivo de código fuente.  Esta opción se habilita de manera predeterminada en la mayoría de los tipos de proyectos de Visual C\+\+ y "stdafx.h" es el archivo de inclusión predeterminado especificado mediante esta opción.  
  
 En el entorno de Visual Studio, utilice uno de los métodos siguientes para resolver este error:  
  
-   Si no utiliza encabezados precompilados en su proyecto, establezca la propiedad **Crear o usar encabezado precompilado** de archivos de código fuente en **No utilizar encabezados precompilados**.  Para establecer esta opción del compilador, siga estos pasos:  
  
    1.  En el panel Explorador de soluciones del proyecto, haga clic con el botón secundario en el nombre del proyecto y, a continuación, haga clic en **Propiedades**.  
  
    2.  En el panel izquierdo, haga clic en la carpeta **C\/C\+\+**.  
  
    3.  Haga clic en el nodo **Encabezados precompilados**.  
  
    4.  En el panel derecho, haga clic en **Crear o usar encabezado precompilado** y, a continuación, haga clic en **No utilizar encabezados precompilados**.  
  
-   Asegúrese de que no ha eliminado, cambiado de nombre ni quitado accidentalmente el archivo de encabezado \(de manera predeterminada, stdafx.h\) del proyecto actual.  Este archivo también se tiene que incluir delante de cualquier otro código en los archivos de código fuente utilizando **\#include "stdafx.h"**. \(Este archivo de encabezado se especifica como la propiedad del proyecto **Crear o usar encabezado precompilado a través del archivo**\)