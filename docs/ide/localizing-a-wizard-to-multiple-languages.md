---
title: "Traducir un asistente a varios idiomas | Microsoft Docs"
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
  - "asistentes personalizados, adaptar"
  - "globalización [C++], controles wizard"
  - "localización [C++], controles wizard"
  - "asistentes [C++], adaptar"
ms.assetid: 879885c2-fafd-44fd-8032-bf0c301f4f45
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Traducir un asistente a varios idiomas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es posible crear asistentes en cualquier idioma compatible con Visual Studio.  De forma predeterminada, al instalar Visual Studio, el programa identifica la configuración regional a partir del Registro y proporciona las plantillas adecuadas para dicha configuración.  
  
 Visual Studio utiliza los identificadores de idioma para conocer la compatibilidad de idioma que un asistente necesita.  De forma predeterminada, el identificador de idioma se define como el valor decimal de la entrada del Registro HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\7.0\\General\\UILanguage.  Si el asistente no encuentra ninguna entrada de idioma, tomará el inglés \(1033\) de forma predeterminada.  
  
> [!NOTE]
>  Para obtener una lista de los valores decimales de idioma, vea [Compatibilidad del Asistente con otros idiomas](../ide/wizard-support-for-other-languages.md).  
  
 En el [archivo .vsz](../Topic/Configuring%20.Vsz%20Files%20to%20Start%20Wizards.md), el identificador de idioma se especifica como un parámetro personalizado en las rutas de acceso donde residen los [archivos HTML](../ide/html-files.md) y los [archivos de plantilla](../ide/template-files.md).  
  
 Debe especificar las rutas de acceso de todos los idiomas para los que proporcione un archivo .htm.  
  
## Ejemplo  
 Los siguientes parámetros personalizados del archivo .vsz indican que se suministran archivos HTML en inglés \(1033\), japonés \(1041\) y alemán \(1031\):  
  
```  
Param="START_PATH\HTML\1033"  
Param="START_PATH\HTML\1041"  
Param="START_PATH\HTML\1031"  
Param="START_PATH\Templates\1033"  
Param="START_PATH\Templates\1041"  
Param="START_PATH\Templates\1031"  
```  
  
 Con los parámetros personalizados anteriores, la estructura de directorios del asistente queda establecida de la siguiente forma:  
  
```  
MyWizard1  
   HTML  
      1033  
         default.htm  
         myEnglishHTML.htm  
      1041  
         default.htm  
         myJapaneseHTML.htm  
      1031  
         default.htm  
         myGermanHTML.htm  
   Templates  
      1033  
         stdafx.h  
         stdafx.cpp  
      1041  
         stdafx.h  
         stdafx.cpp  
      1031  
         stdafx.h  
         stdafx.cpp  
   Images  
      HtmlPage1.bmp  
      HtmlPage2.jpg  
   Scripts  
      Default.js  
```  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [Parámetros personalizados en el archivo .vsz del asistente](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)