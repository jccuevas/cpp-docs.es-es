---
title: "Examinar los aspectos pr&#225;cticos de un asistente | Microsoft Docs"
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
  - "asistentes personalizados, proyectos de asistente"
ms.assetid: 79917075-a843-40f6-abf8-64d98e5f6bdc
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Examinar los aspectos pr&#225;cticos de un asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No es necesario compilar un proyecto de asistente para que los usuarios puedan empezar a utilizarlo.  Una vez creados los elementos necesarios, el archivo VSDIR indica al cuadro de diálogo `New Project` que muestre el icono del asistente y al cuadro de diálogo `Add New Item` que muestre el nombre del asistente en el menú contextual.  De ese modo, el usuario podrá iniciar el asistente inmediatamente con tan sólo seleccionarlo.  
  
 Cuando el usuario inicia el asistente, el shell del entorno participa en la creación del motor del asistente y busca la interfaz <xref:EnvDTE.IDTWizard>.  A continuación, llama al método <xref:EnvDTE.IDTWizard.Execute%2A> para que inicie el asistente.  
  
> [!NOTE]
>  Si el asistente no tiene interfaz, el proyecto se creará con los valores predeterminados suministrados y se mostrará en el Explorador de soluciones con la estructura de nodos especificada en el archivo .vsz.  A partir de este momento, supondremos que el asistente sí tiene una interfaz de usuario.  
  
 Si el asistente tiene una interfaz de usuario en formato HTML, éste podrá utilizarla para aceptar o cambiar los valores predeterminados de cada control.  A medida que el usuario navegar por las páginas del asistente y efectúa cambios, se realizan llamadas a funciones como <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.Navigate%2A> y <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.Next%2A> en la sección de script del código HTML.  
  
 Conforme el usuario va seleccionando las distintas opciones del asistente, éstas quedan capturadas en la tabla de símbolos del control del asistente.  La tabla de símbolos compara los identificadores de los controles de la página HTML del asistente para mantener una correspondencia uno a uno entre las selecciones del usuario y la tabla de símbolos.  
  
 Cuando el usuario hace clic en el botón **Finalizar** de la interfaz del asistente, se llama a la función **OnFinish** de JScript desde el script HTML.  
  
> [!NOTE]
>  Se puede personalizar **OnFinish** en el archivo Default.js para realizar cualquier tarea adicional que resulte necesaria.  
  
 A continuación, el motor del asistente recorre los archivos de plantilla, analizándolos y representándolos en función de las opciones seleccionadas por el usuario.  Agrega al proyecto los archivos representados copiándolos en su directorio.  El proyecto recién creado se carga en el entorno de Visual Studio, al tiempo que los archivos y los nodos del proyecto se muestran en el Explorador de soluciones.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl>   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Pasos para diseñar un asistente](../ide/steps-to-designing-a-wizard.md)   
 [Personalizar un asistente](../ide/customizing-your-wizard.md)