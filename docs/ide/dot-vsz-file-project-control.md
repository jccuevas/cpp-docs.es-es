---
title: "Archivo .vsz (Control del proyecto) | Microsoft Docs"
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
  - ".vsz (archivos)"
  - "asistentes personalizados, .vsz (archivo)"
  - "asistentes personalizados, archivos de control de proyecto"
  - "archivos [C++], creado mediante un asistente personalizado"
  - "vsz (archivos)"
ms.assetid: b8678fee-6795-46d1-9338-48b22d5e9207
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivo .vsz (Control del proyecto)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El punto de inicio de todo asistente es el archivo .vsz.  El archivo .vsz es un archivo de texto que determina a qué asistente se ha de llamar y qué información se le ha de pasar.  Este archivo contiene un encabezado de dos líneas, seguido de diversos parámetros opcionales para pasarle al asistente.  Para obtener una lista de los parámetros opcionales, vea [Símbolos predefinidos del Asistente personalizado](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md).  
  
 En el siguiente ejemplo se muestra el encabezado de un archivo .vsz:  
  
```  
VSWIZARD 7.0  
Wizard=VsWizard.VsWizardEngine.10.0  
Param="WIZARD_NAME = My AppWizard"  
```  
  
-   La primera línea del encabezado especifica el número de versión del formato de archivo de plantilla.  Se puede especificar este número como `6.0`, `7.0` o `7.1`.  Ningún otro número será válido; de utilizarse, se producirá el error "Formato no válido".  
  
-   La segunda línea asigna a la variable **Wizard** el id. de programa del asistente creado por Visual Studio.  Un id. de programa es una representación de cadena de un CLSID, tal como `VsWizard.VsWizardEngine.10.0`.  
  
     Si el asistente posee interfaz de usuario, el id. de programa especifica automáticamente al asistente que implemente <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI>.  De forma predeterminada, los métodos de esta interfaz se utilizan en los [archivos .htm](../ide/html-files.md) del proyecto.  El comportamiento del asistente puede cambiarse utilizando los métodos para esta interfaz incluidos en los archivos .htm.  Para obtener más información, vea <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl>, que es la coclase para <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI>.  
  
-   Tras estas dos líneas, aparece una lista opcional de parámetros que le permiten al archivo .vsz pasar parámetros personalizados adicionales al asistente.  Cada valor se pasa como un elemento de cadena de una matriz de variantes en el método <xref:Microsoft.VisualStudio.VsWizard.VsWizardClass.Execute%2A> del control del asistente.  De forma predeterminada, un asistente con interfaz de usuario proporciona los siguientes parámetros predeterminados:  
  
    ```  
    Param="START_PATH = <path to the wizard>"  
    Param="HTML_PATH = <path to the wizard's HTML file>"  
    Param="TEMPLATES_PATH = <path to the wizard's template file>"  
    Param="SCRIPT_PATH = <path to the wizard's script files>"  
    Param="IMAGES_PATH = <path to the wizard's images>"  
    ```  
  
     Si el asistente no posee interfaz de usuario, no presentará ningún parámetro `IMAGES_PATH` y, en su lugar, contendrá los siguientes parámetros:  
  
    ```  
    Param="WIZARD_UI = FALSE"  
    Param="SOURCE_FILTER = txt"  
    ```  
  
-   El archivo .vsz puede contener los siguientes parámetros, los cuales especifican funciones incluidas en el archivo [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md):  
  
    ```  
    Param="PREPROCESS_FUNCTION = CanAddATLClass"  
    Param="PREPROCESS_FUNCTION = CanAddMFCClass"  
    Param="PREPROCESS_FUNCTION = CanAddClass"  
    ```  
  
 El asistente llama a las funciones [CanAddATLClass](../ide/canaddatlclass.md), [CanAddMFCClass](../ide/canaddmfcclass.md) y [CanAddClass](../ide/canaddclass.md) para confirmar que el [modelo de código de Visual C\+\+](http://msdn.microsoft.com/es-es/dd6452c2-1054-44a1-b0eb-639a94a1216b) está disponible.  Si una de las funciones devuelve **false**, el asistente no se iniciará.  
  
 Colocando el archivo .vsz en el directorio vcprojects, podrá agregarse el asistente al panel Plantillas del cuadro de diálogo **Nuevo proyecto** de Visual Studio.  De forma predeterminada, el Asistente personalizado escribirá el archivo .vsz en este directorio.  
  
> [!NOTE]
>  Si elimina los archivos y directorios del asistente, también deberá eliminar del directorio vcprojects los archivos del proyecto .vsz, .vsdir e .ico.  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Visual C\+\+ Wizard Model](http://msdn.microsoft.com/es-es/159395ac-33c7-47bf-ad42-4e1435ddc758)   
 [Agregar asistentes a los cuadros de diálogo Agregar elemento y Nuevo proyecto mediante el uso de archivos .Vsdir](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)