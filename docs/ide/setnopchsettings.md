---
title: "SetNoPchSettings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetNoPchSettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetNoPchSettings (método)"
ms.assetid: 52373c98-ad5e-4e9b-9e0f-9f58ddb2a636
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SetNoPchSettings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Establece las propiedades de configuración de un proyecto cuando no se utiliza ningún encabezado precompilado.  
  
## Sintaxis  
  
```  
  
      function SetNoPchSettings(   
   oProj    
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
## Comentarios  
 Se llama a esta función para configurar el proyecto cuando éste no utiliza configuración de encabezado precompilado.  
  
## Ejemplo  
 Vea [SetCommonPchSettings](../ide/setcommonpchsettings.md).  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [SetCommonPchSettings](../ide/setcommonpchsettings.md)   
 [AddCommonConfig](../ide/addcommonconfig.md)