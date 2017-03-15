---
title: "Archivos de plantilla | Microsoft Docs"
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
  - "asistentes personalizados, archivos de plantilla"
  - "archivos [C++], creado mediante un asistente personalizado"
  - "plantillas [C++], para asistentes"
ms.assetid: 48fae3d8-3a53-4f62-8010-144c5ffe334e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Archivos de plantilla
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las plantillas que constituyen un asistente son un conjunto de archivos de texto con algunas [directivas simples](../ide/template-directives.md) que se analizan y representan según los datos proporcionados por el usuario para después agregarse al proyecto inicial.  La información adecuada para analizar las plantillas se obtiene directamente de la tabla de símbolos del control del asistente.  
  
 El siguiente ejemplo es un archivo de plantilla muy sencillo de un asistente que le pide al usuario que seleccione A o B.  
  
## Ejemplo  
  
```  
This file has been created by My Custom wizard.  
You selected:  
[!if TYPE_A]  
Type A  
[!else]  
Type B  
[!endif]  
The name of this project is [!output PROJECT_NAME].root.cpp:  
```  
  
 Si el usuario elige "Type B", la plantilla anterior se presentará de la siguiente forma:  
  
  **El asistente personalizado creó este archivo.  Seleccionó:**  
**Tipo B**  
**El nombre de este proyecto es MyApp8.**    
## Output  
  
```  
This file has been created by My Custom wizard.  
You selected:  
Type B  
The name of this project is MyApp8.  
```  
  
 **Nota** La sintaxis anterior es nueva en Visual C\+\+ .NET.  La sintaxis de versiones anteriores de Visual C\+\+ no es compatible con Visual C\+\+ .NET.  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [Archivo Templates.inf](../ide/templates-inf-file.md)