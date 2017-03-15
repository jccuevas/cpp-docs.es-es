---
title: "Personalizar un asistente | Microsoft Docs"
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
  - "asistentes personalizados"
  - "asistentes personalizados, crear en proyectos de Visual C++"
ms.assetid: a3ff1c81-3eef-41e7-a6bc-2f98e4bf423f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Personalizar un asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para personalizar el asistente creado con el [Asistente personalizado](../ide/application-settings-custom-wizard.md), deberá tener en cuenta las siguientes tareas comunes:  
  
-   En el archivo .vsz, especifique los parámetros personalizados necesarios para que el asistente funcione.  Vea [El archivo .vsz \(control del proyecto\)](../ide/dot-vsz-file-project-control.md) y [Símbolos predefinidos del Asistente personalizado](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md) para obtener más información.  
  
     Si va a traducirse el asistente a varios idiomas, agregue los parámetros de tales idiomas al archivo .vsz.  Vea [Traducir un asistente a varios idiomas](../ide/localizing-a-wizard-to-multiple-languages.md) para obtener más información.  
  
-   Personalice los [archivos de plantilla](../ide/template-files.md) \(y el archivo [Templates.inf](../ide/templates-inf-file.md)\) para especificar las directivas de las selecciones del usuario.  
  
-   Personalice el [archivo Default.js](../ide/jscript-file.md) para especificar cualquier procedimiento especial de control que pueda necesitar el asistente.  Puede escribir sus propias funciones, así como utilizar las funciones incluidas en el archivo [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md).  
  
-   Diseñe los iconos y las demás imágenes que aparecerán en la interfaz de usuario HTML.  
  
-   Diseñe la interfaz de usuario HTML.  
  
-   Agregue símbolos a la tabla de símbolos HTML que se correspondan con los botones, controles, cuadros de texto y demás elementos que utilice el asistente.  
  
     A continuación, se muestra un fragmento de código HTML generado por el Asistente personalizado:  
  
    ```  
    <SYMBOL NAME="WIZARD_DIALOG_TITLE" TYPE=text VALUE="MyCustomWiz">  
          </SYMBOL>  
    <SYMBOL NAME="SAMPLE_CHECKBOX" TYPE=checkbox VALUE=true>  
          </SYMBOL>  
    ```  
  
     Este asistente, denominado MyCustomWiz, muestra una casilla que aparece seleccionada de forma predeterminada.  
  
-   En la sección de los archivos HTML marcada como `<SCRIPT LANGUAGE="JSCRIPT">`, agregue las llamadas a funciones de JScript y obtenga acceso al modelo de objetos de Visual Studio para personalizar el comportamiento del asistente.  Deberá llamar a estas funciones utilizando `window.external`, según se indica a continuación:  
  
    ```  
    window.external.AddSymbol("MAIN_FRAME_DEFAULT_STYLES", true);  
    window.external.AddSymbol("MAIN_FRAME_STYLE_FLAGS", "");  
    ```  
  
    > [!NOTE]
    >  Los métodos, propiedades y eventos expuestos mediante [Automatización y extensibilidad en Visual Studio](../Topic/Automation%20and%20Extensibility%20for%20Visual%20Studio.md), el [modelo de código de Visual C\+\+](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b), el [modelo de proyecto](http://msdn.microsoft.com/es-es/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f) y el [modelo de asistente](http://msdn.microsoft.com/es-es/159395ac-33c7-47bf-ad42-4e1435ddc758) permiten administrar mediante programación todos los aspectos del proyecto de asistente, desde la creación a la generación, tanto en archivos JScript como en .htm.  
  
-   En caso necesario, personalice el [archivo .vsdir](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md) para que el shell pueda comprender la información sobre el archivo .vsz y el resto de plantillas.  Por ejemplo, indique los identificadores de recursos de los iconos, los marcadores, los nombres traducidos, etc.  
  
-   Cree archivos .htm y archivos de plantilla en todos los idiomas a los que se desee traducir el asistente.  Agréguelos a los directorios correspondientes del proyecto.  
  
-   [Proporcione ayuda contextual](../ide/providing-context-sensitive-help.md) para el asistente.  
  
## Vea también  
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Pasos para diseñar un asistente](../ide/steps-to-designing-a-wizard.md)   
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [Proporcionar ayuda contextual](../ide/providing-context-sensitive-help.md)   
 [Controlar errores de los asistentes](../ide/handling-errors-in-wizards.md)