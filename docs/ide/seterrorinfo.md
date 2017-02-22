---
title: "SetErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetErrorInfo (método)"
ms.assetid: 78bca763-3f90-4e04-b566-b4b7fe2431b1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# SetErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[OnWizFinish](../ide/onwizfinish.md) y [CanUseFileName](../ide/canusefilename.md) llaman a esta opción para obtener información actual sobre errores.  
  
## Sintaxis  
  
```  
  
      function SetErrorInfo(   
   oErrorObj   
);  
```  
  
#### Parámetros  
 *oErrorObj*  
 Objeto de error.  
  
## Comentarios  
 [OnWizFinish](../ide/onwizfinish.md) y [CanUseFileName](../ide/canusefilename.md) llaman a esta opción para obtener información actual sobre errores.  Consulte <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.SetErrorInfo%2A> en la documentación del modelo de código de Visual C\+\+ para obtener más información.  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)