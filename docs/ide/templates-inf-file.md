---
title: "Archivo Templates.inf | Microsoft Docs"
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
  - "asistentes personalizados, archivos de plantilla"
ms.assetid: 93d60d27-2402-4dc8-a829-e97417ccea49
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivo Templates.inf
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Templates.inf es un archivo de texto que contiene una lista de plantillas que se van a representar para el proyecto.  
  
 Al ser Templates.inf un [archivo de plantilla](../ide/template-files.md), se pueden utilizar directivas para indicar qué archivos se incluirán en el proyecto en función de las selecciones del usuario.  Vea [Directivas de plantilla](../ide/template-directives.md) para obtener una lista de las directivas que se pueden utilizar en este archivo.  
  
## Ejemplo  
  
```  
Template1.txt  
Template2.txt  
  [!if TYPE_A]  
TemplateOptionA.h  
TemplateOptionA.cpp  
  [!else]  
TemplateOptionB.h  
TemplateOptionB.cpp  
  [!endif]  
```  
  
 **CreateCustomInfFile** representa Templates.inf como un archivo de texto temporal que deberá eliminarse una vez procesados los archivos.  
  
## Ejemplo  
  
```  
var InfFile = CreateCustomInfFile();  
AddFilesToProject(selProj, strProjectName, InfFile);  
InfFile.Delete();  
```  
  
 Vea [El archivo JScript](../ide/jscript-file.md) para obtener más información.  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)