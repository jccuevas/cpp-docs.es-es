---
title: "Par&#225;metros personalizados en el archivo .vsz del asistente | Microsoft Docs"
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
  - "ABSOLUTE_PATH (macro)"
  - "asistentes personalizados, .vsz (archivo)"
  - "HTML_FILTER (macro)"
  - "HTML_PATH (macro)"
  - "IMAGE_FILTER (macro)"
  - "IMAGES_PATH (macro)"
  - "MISC_FILTER (macro)"
  - "PRODUCT (macro)"
  - "PRODUCT_INSTALLATION_DIR (macro)"
  - "PROJECT_TEMPLATE_NAME (macro)"
  - "PROJECT_TEMPLATE_PATH (macro)"
  - "RELATIVE_PATH (macro)"
  - "SCRIPT_COMMON_PATH (macro)"
  - "SCRIPT_FILTER (macro)"
  - "SCRIPT_PATH (macro)"
  - "START_PATH (macro)"
  - "TEMPLATE_FILTER (macro)"
  - "TEMPLATES_PATH (macro)"
  - "WIZARD_NAME (macro)"
  - "WIZARD_UI (macro)"
ms.assetid: 560dd5c0-7cff-4974-b856-5ca25b0669b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Par&#225;metros personalizados en el archivo .vsz del asistente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En las dos primeras líneas, el archivo .vsz identifica la versión del asistente y el id. de programa o CLSID del asistente que se va a crear.  Este archivo también puede incluir parámetros de contexto y parámetros personalizados opcionales que se agregan a la tabla de símbolos \(junto con los símbolos suministrados en la sección de símbolos HTML\).  
  
 El método <xref:Microsoft.VisualStudio.VsWizard.VsWizardClass.Execute%2A> muestra el asistente que toma una matriz del contexto y los parámetros personalizados definidos en el archivo .vsz como sus parámetros.  
  
 Los siguientes símbolos de uso común se especifican como parámetros personalizados en el [archivo .vsz](../ide/dot-vsz-file-project-control.md) o en los archivos .htm y pueden utilizarse en los archivos HTML, de script o de plantilla del asistente.  
  
## Ejemplo  
 Como indican las siguientes entradas del archivo .vsz, el asistente denominado MyProjWiz contiene una interfaz de usuario:  
  
```  
VSWIZARD 7.0  
Wizard=VsWizard.VsWizardEngine  
Param="WIZARD_NAME = MyProjWiz"  
Param="WIZARD_UI = TRUE"  
```  
  
### Símbolos de los parámetros personalizados del archivo .vsz del asistente  
  
|Símbolo|Definición|  
|-------------|----------------|  
|ABSOLUTE\_PATH|Ubicación de los archivos del asistente.|  
|HTML\_FILTER|\(Símbolo especificado en el archivo .vsz\).  Tipos de archivos que se colocan en la carpeta Archivos HTML del **Explorador de soluciones**.  Normalmente se especifican como "htm".|  
|HTML\_PATH|\(Símbolo especificado en el archivo .vsz\).  Ubicación de los [archivos HTML](../ide/html-files.md) del asistente.  De forma predeterminada, es START\_PATH\\HTML\\*IDIOMA* \(*IDIOMA* se refiere a la configuración regional especificada por el Registro del sistema\). **Note:**  Se puede especificar un idioma distinto si se asigna a \<LangID\> el valor decimal de HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\7.0\\General\\UILanguage.  Vea [Traducir un asistente a varios idiomas](../ide/localizing-a-wizard-to-multiple-languages.md) para obtener más información.  Para obtener una lista de los valores decimales de idioma, vea [Compatibilidad del Asistente con otros idiomas](../ide/wizard-support-for-other-languages.md).|  
|IMAGE\_FILTER|\(Símbolo especificado en el archivo .vsz\).  Tipos de archivos que se colocan en la carpeta Archivos de imagen del Explorador de soluciones.  Normalmente se especifican como "bmp;gif".|  
|IMAGES\_PATH|\(Símbolo especificado en el archivo .vsz\).  Ubicación de los archivos de imagen utilizados en los archivos .html.  De forma predeterminada, es START\_PATH\\Images.|  
|MISC\_FILTER|\(Símbolo especificado en el archivo .vsz\).  Tipos de archivos que se colocan en la carpeta Misc del Explorador de soluciones.  Normalmente se especifican como "vsz;vsdir;ico;vcproj;csproj;css;inf".|  
|PRODUCT|De forma predeterminada, toma el valor "Visual C\+\+"; no obstante, también se puede utilizar el valor "Visual Basic" para crear asistentes de Visual Basic, y así sucesivamente.|  
|PRODUCT\_INSTALLATION\_DIR|Directorio indicado en el Registro, en HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\\<Product\>\\ ProductDir.|  
|PROJECT\_TEMPLATE\_NAME|\(Símbolo especificado en el archivo .vsz\).  Archivo de plantilla del proyecto utilizado por el asistente para crear proyectos.  Normalmente se especifican como "txt".|  
|PROJECT\_TEMPLATE\_PATH|Directorio que contiene los [archivos de plantilla](../ide/template-files.md) del proyecto.  En Visual C\+\+, es PRODUCT\_INSTALLATION\_DIR\\VCWizards de forma predeterminada.|  
|RELATIVE\_PATH|Si ABSOLUTE\_PATH no se encuentra, se utilizará RELATIVE\_PATH.  Esta es la ruta de acceso relativa a PRODUCT\_INSTALLATION\_DIR.  Para Visual C\+\+, RELATIVE\_PATH es PRODUCT\_INSTALLATION\_DIR\\VCWizards.|  
|SCRIPT\_COMMON\_PATH|Nombre de directorio, relativo a la ruta de acceso PRODUCT\_INSTALLATION\_DIR, donde se encuentra el archivo de script común.  Por ejemplo, en Visual C\+\+, este directorio es VCWizards.|  
|SCRIPT\_FILTER|\(Símbolo especificado en el archivo .vsz\).  Tipos de archivos que se colocan en la carpeta Archivos de script del Explorador de soluciones.  Normalmente se especifican como "js" \(JScript\) o "vbs" \(VBScript\).|  
|SCRIPT\_PATH|Ubicación del [archivo JScript](../ide/jscript-file.md) del asistente.  De forma predeterminada, es START\_PATH\\Scripts.|  
|START\_PATH|\(Símbolo especificado en el archivo .vsz\).  Este símbolo no lo establece el usuario, sino que se utiliza internamente para identificar RELATIVE\_PATH o ABSOLUTE\_PATH.  El nombre del asistente \(WIZARD\_NAME\) se anexa a este valor.|  
|TEMPLATE\_FILTER|\(Símbolo especificado en el archivo .vsz\).  Tipos de archivos que se colocan en la carpeta Archivos de plantilla del Explorador de soluciones.  Normalmente se especifican como "txt".|  
|TEMPLATES\_PATH|\(Símbolo especificado en el archivo .vsz\).  Ubicación de los archivos de plantilla del asistente.  De forma predeterminada, es START\_PATH\\Templates\\\<LangID\>. **Note:**  Vea HTML\_PATH para obtener más información sobre LangID.|  
|WIZARD\_NAME|Símbolo que especifica el nombre del asistente.  Se encuentra en el archivo .vsz y lo utilizan el resto de los símbolos.|  
|WIZARD\_UI|\(Símbolo especificado en el archivo .vsz\).  Valor booleano que indica si el asistente posee una interfaz de usuario.  Se deberá especificar **TRUE** si existe una interfaz de usuario o **FALSE** en caso contrario.|  
  
## Vea también  
 <xref:EnvDTE.IDTWizard.Execute%2A>   
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)