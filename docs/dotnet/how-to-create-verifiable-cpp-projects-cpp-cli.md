---
title: "C&#243;mo: Crear proyectos de C++ comprobables (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conversiones, proyectos de C++"
  - "ensamblados comprobables [C++], crear"
  - "proyectos de Visual C++"
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear proyectos de C++ comprobables (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los asistentes para aplicaciones de Visual C\+\+ no crean proyectos comprobables, pero estos proyectos se pueden convertir en comprobables.  En este tema se describe cómo establecer las propiedades de un proyecto y modificar archivos de código fuente del proyecto para transformar los proyectos de Visual C\+\+ y generar aplicaciones comprobables.  
  
## Configuración del compilador y vinculador  
 De forma predeterminada, los proyectos de .NET utilizan el marcador de compilador \/clr y configuran el vinculador para hardware x86.  Por lo que respecta al código comprobable, se debe utilizar el marcador \/clr:safe e indicar al vinculador que genere MSIL en lugar de instrucciones máquina nativas.  
  
#### Para cambiar la configuración del compilador y el vinculador  
  
1.  Abra la página de propiedades del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md).  
  
2.  En la página **General**, en el nodo **Propiedades de configuración**, establezca la propiedad **Compatibilidad con Common Language Runtime** en **Compatible con Common Language Runtime de MSIL seguro \(\/clr:safe\)**.  
  
3.  En la página **Avanzadas**, en el nodo **Vinculador**, establezca la propiedad **Tipo de imagen de CLR** en **Forzar imagen de IL segura \(\/CLRIMAGETYPE:SAFE\)**.  
  
## Quitar tipos de datos nativos  
 Puesto que los tipos de datos nativos no son comprobables, aunque no se utilicen realmente, debe quitar todos los archivos de encabezado con tipos nativos.  
  
> [!NOTE]
>  El procedimiento siguiente es válido para proyectos de Aplicación de Windows Forms \(.NET\) y Aplicación de consola \(.NET\).  
  
#### Para quitar las referencias a tipos de datos nativos  
  
1.  Marque como comentario todo el archivo Stdafx.h.  
  
## Configurar un punto de entrada  
 Puesto que las aplicaciones comprobables no pueden utilizar bibliotecas en tiempo de ejecución de C \(CRT\), no pueden depender de CRT para llamar a la función principal como punto de entrada estándar.  Es decir, se debe proporcionar explícitamente el nombre de la función que se va a llamar inicialmente al vinculador. \(En este caso, se utiliza Main\(\) en lugar de main\(\) o \_tmain\(\) para representar un punto de entrada ajeno a CRT, pero como el punto de entrada se debe especificar explícitamente, este nombre es arbitrario.\)  
  
> [!NOTE]
>  Los procedimientos siguientes se aplican a proyectos de Aplicación de consola \(.NET\).  
  
#### Para configurar un punto de entrada  
  
1.  Cambie \_tmain\(\) por Main\(\) en el archivo .cpp principal del proyecto.  
  
2.  Abra la página de propiedades del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../misc/how-to-open-project-property-pages.md).  
  
3.  En la página **Avanzadas**, en el nodo **Vinculador**, escriba `Main` como valor de propiedad **Punto de entrada**.  
  
## Vea también  
 [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md)