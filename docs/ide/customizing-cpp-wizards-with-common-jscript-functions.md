---
title: "Personalizar los asistentes de C++ con funciones comunes de JScript | Microsoft Docs"
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
  - "métodos de JScript para asistentes, crear asistentes de C++"
ms.assetid: c602978f-a2c4-462f-85c3-50b5897bec46
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Personalizar los asistentes de C++ con funciones comunes de JScript
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando crea un proyecto de asistente con el [Asistente personalizado](../ide/creating-a-custom-wizard.md), su proyecto incluye Common.js.  Si especifica una interfaz de usuario para el asistente, el proyecto también contiene páginas HTML que especifican el lenguaje de script JScript e incluye el archivo Common.js, de la manera siguiente:  
  
```  
<SCRIPT ID="INCLUDE_COMMON" LANGUAGE ="JSCRIPT"></SCRIPT>  
```  
  
 El asistente también crea un archivo único denominado Default.js.  Puede personalizar sus propias funciones de JScript en Default.js.  Vea [El archivo JScript](../ide/jscript-file.md) para obtener más información.  
  
 Common.js contiene funciones a las que puede llamar desde las páginas HTML de cada asistente y desde Default.js.  Si tiene las mismas funciones que desea usar en distintos asistentes, puede colocar estas funciones en Common.js.  
  
## Vea también  
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)