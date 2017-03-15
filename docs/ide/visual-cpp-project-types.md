---
title: "Tipos de proyecto de Visual C++ | Microsoft Docs"
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
  - "programas [C++], proyectos"
  - "plantillas de proyecto [Visual Studio], C++"
  - "TODO (comentarios) [C++]"
  - "proyectos [C++], tipos"
  - "plantillas [C++], proyectos"
  - "aplicaciones [C++], proyectos"
  - "proyectos de Visual C++, tipos"
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipos de proyecto de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede usar una plantilla de proyecto para crear la estructura básica de programa, menús, barras de herramientas, iconos, referencias e instrucciones `#include` adecuados para el tipo de proyecto que quiera crear. Visual Studio incluye diversos tipos de plantilla de proyecto de Visual C\+\+, muchos de ellos con su correspondiente asistente para que pueda personalizar sus proyectos mientras los va creando. Justo después de crear un proyecto, este se puede compilar y ejecutar la aplicación; de hecho, un procedimiento recomendado es compilar cada cierto tiempo mientras desarrolla la aplicación.  
  
 No es necesario usar una plantilla para crear un proyecto, pero muchas veces es lo más eficaz, dado que es más fácil modificar los archivos de proyecto y la estructura existentes que crearlos desde cero.  
  
> [!NOTE]
>  Puede crear un proyecto de lenguaje C con plantillas de proyecto de C\+\+. En el proyecto generado, busque los archivos que tengan la extensión de nombre de archivo .cpp y cámbiela por .c. Luego, en la página **Propiedades del proyecto** del proyecto \(no de la solución\), expanda **Propiedades de configuración** y **C\/C\+\+** y seleccione **Avanzadas**. Cambie la opción **Compilar como** por **Compilar como código de C \(\/TC\)**.  
  
## Plantillas de proyecto  
 Visual Studio incluye las siguientes plantillas de proyecto de Visual C\+\+.  
  
### Aplicaciones de la Tienda  
  
||  
|-|  
|[Plantillas de proyecto de C\#, VB y C\+\+ para aplicaciones de la Tienda](http://go.microsoft.com/fwlink/p/?LinkID=262279)|  
  
### ATL  
  
|Plantilla de proyecto|Cómo crear un proyecto|  
|---------------------------|----------------------------|  
|Proyecto ATL|[Crear un proyecto ATL](../atl/reference/creating-an-atl-project.md)|  
  
### CLR  
  
|Plantilla de proyecto|  
|---------------------------|  
|[\(NOTINBUILD\) Plantilla Biblioteca de clases \(C\+\+\)](http://msdn.microsoft.com/es-es/0d779bfa-5c5a-4b10-a9d5-a6791764a78f)|  
|[Cómo: Crear aplicaciones de consola CLR](../dotnet/how-to-create-clr-console-applications-cpp-cli.md)|  
|[NOTINBUILD Plantilla Proyecto vacío de CLR \(C\+\+\)](http://msdn.microsoft.com/es-es/f57c5572-5581-440f-b684-eec646764f08)|  
  
### General  
  
|Plantilla de proyecto|Cómo crear un proyecto|  
|---------------------------|----------------------------|  
|Proyecto vacío|[Crear soluciones y proyectos](../Topic/Creating%20Solutions%20and%20Projects.md)|  
|Asistente personalizado|[Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)|  
|Proyecto de archivos Make|[Crear un proyecto de archivos MAKE](../ide/creating-a-makefile-project.md)|  
  
### MFC  
  
|Plantilla de proyecto|Cómo crear un proyecto|  
|---------------------------|----------------------------|  
|Control ActiveX MFC|[Crear un control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)|  
|Aplicación MFC|[Crear una aplicación MFC](../mfc/reference/creating-an-mfc-application.md)|  
|MFC DLL|[Crear un proyecto DLL de MFC](../mfc/reference/creating-an-mfc-dll-project.md)|  
  
### Prueba  
  
|Plantilla de proyecto|Cómo crear un proyecto|  
|---------------------------|----------------------------|  
|Proyecto de prueba administrado|[Crear un proyecto de prueba unitaria](../Topic/Create%20a%20unit%20test%20project.md)|  
|Proyecto de prueba unitaria de tipo nativo|[Pruebas unitarias de código nativo con el Explorador de pruebas](http://msdn.microsoft.com/es-es/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
  
### Win32  
  
|Plantilla de proyecto|Cómo crear un proyecto|  
|---------------------------|----------------------------|  
|Proyecto de consola Win32|[Crear una aplicación de consola](../windows/creating-a-console-application.md)|  
|Proyecto Win32|[Cómo: crear una aplicación de escritorio de Windows](../Topic/How%20to:%20Create%20a%20Windows%20Desktop%20Application.md)|  
  
## Comentarios TODO  
 Muchos de los archivos que se generan mediante una plantilla de proyecto contienen comentarios TODO que ayudan a saber dónde puede incluir su propio código fuente. Para más información sobre cómo agregar código, vea [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md) y [Working with Resource Files](../mfc/working-with-resource-files.md).  
  
## Vea también  
 [Crear proyectos de escritorio con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Usar proyectos para crear aplicaciones](http://msdn.microsoft.com/es-es/3339fa90-bac2-4b95-8361-662a2e0e7dfe)   
 [Proyectos de CLR](../ide/files-created-for-clr-projects.md)