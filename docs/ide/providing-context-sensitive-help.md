---
title: "Proporcionar ayuda contextual | Microsoft Docs"
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
  - "Ayuda contextual"
  - "Ayuda contextual, asistente personalizado"
  - "asistentes personalizados, implementar la Ayuda"
ms.assetid: c6c4d961-29d3-4d16-9f39-b12545aba540
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proporcionar ayuda contextual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando el [Asistente personalizado](../ide/application-settings-custom-wizard.md) crea un asistente, inserta en él un botón **Ayuda**.  
  
 Cada archivo .htm del proyecto incluirá el siguiente código para permitir la utilización del botón **Ayuda** en el asistente.  
  
```  
<BUTTON CLASS="BUTTONS" ID="HelpBtn" ACCESSKEY="H"  
 onClick="window.external.OnHelp('vc.appwiz.custom.overview');">  
```  
  
 El método <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.OnHelp%2A> especifica la palabra clave del archivo de Ayuda HTML asociado a esa página del asistente.  Para obtener más información sobre la creación de archivos de ayuda HTML asociados a una página, vea [Página principal de la Ayuda HTML](vsconhh1start).  Para proporcionar su propia ayuda a la página, deberá reemplazar la cadena `'vc.appwiz.custom.overview'` con la palabra clave que identifique el tema de la Ayuda HTML para la página.  
  
 **Nota** Este archivo .htm no puede integrarse en la Ayuda MSDN compilada.  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)