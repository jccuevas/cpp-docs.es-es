---
title: "Pasos para dise&#241;ar un asistente | Microsoft Docs"
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
  - "asistentes personalizados, diseñar"
ms.assetid: dc22746b-99e3-4569-a8b4-b3d7cbabf8f2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Pasos para dise&#241;ar un asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un asistente puede utilizarse para crear y configurar los archivos iniciales comunes de un proyecto.  Como con cualquier proyecto, crear un asistente requiere planeación.  Los siguientes pasos le ayudarán a familiarizarse con el Asistente personalizado de Visual C\+\+ y a aplicarlo a sus propios proyectos.  
  
1.  Examine los [ejemplos de asistentes personalizados](http://msdn.microsoft.com/es-es/6afa2143-062c-4a68-81ca-66cbf4b95261) incluidos en Visual Studio.  
  
2.  Realice el trabajo preliminar para diseñar el tipo de proyecto que deberá crear el asistente.  Como ocurre con la creación de todas las aplicaciones, este proceso puede pasar por diferentes personas e iteraciones.  
  
3.  Cree el proyecto con el [Asistente personalizado](../ide/creating-a-custom-wizard.md) de Visual C\+\+, especificando las opciones de la interfaz de usuario y del número de páginas.  
  
    > [!NOTE]
    >  Si no indica ninguna interfaz de usuario \(es decir, si desactiva **Interfaz de usuario** en [Configuración de la aplicación, Asistente personalizado](../ide/application-settings-custom-wizard.md) del Asistente personalizado\), el asistente utilizará el parámetro personalizado WIZARD\_UI\=**FALSE** y creará los archivos de plantilla del proyecto sin datos proporcionados por el usuario y sin archivos .htm.  Como consecuencia de ello, no se especificarán números de página.  Vea [El archivo .vsz \(control del proyecto\)](../ide/dot-vsz-file-project-control.md) para obtener más información.  
  
4.  [Examine el proyecto básico](../ide/examining-the-basic-wizard-project.md) creado por el Asistente personalizado.  
  
5.  Si el asistente tiene una interfaz de usuario, ejecútelo para [obtener información adicional sobre los aspectos básicos del asistente personalizado](../ide/examining-the-mechanics-of-a-wizard.md).  
  
6.  [Personalice el asistente básico](../ide/customizing-your-wizard.md).  
  
7.  [Agregue ayuda contextual](../ide/providing-context-sensitive-help.md).  
  
8.  [Proporcione control de errores](../ide/handling-errors-in-wizards.md) para los códigos JScript y HTML.  
  
9. Compile y pruebe el asistente.  
  
10. Depure el asistente.  Vea [Depurar script y aplicaciones Web](../Topic/Debugging%20Web%20Applications%20and%20Script.md) para obtener más información.  
  
    > [!NOTE]
    >  Al depurar Jscript, no se puede llevar a cabo una depuración en modo mixto con código nativo.  
  
## Vea también  
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)