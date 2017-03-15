---
title: "AddATLSupportToProject | Microsoft Docs"
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
  - "AddATLSupportToProject (método)"
ms.assetid: 26708f22-1e9b-4432-83b2-ed94c765b753
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# AddATLSupportToProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega compatibilidad con ATL a un proyecto MFC.  
  
## Sintaxis  
  
```  
  
      function AddATLSupportToProject(   
   oProj   
);  
```  
  
#### Parámetros  
 `oProj`  
 Proyecto seleccionado.  
  
## Valor devuelto  
 **true** si se agregó correctamente la compatibilidad con ATL al proyecto MFC.  
  
## Comentarios  
 Esta función se utiliza para agregar compatibilidad de ATL a un proyecto MFC creado por el asistente.  
  
 El asistente muestra un cuadro de mensaje para confirmar la adición de compatibilidad con ATL al proyecto MFC.  Tras recibir la confirmación, el asistente comprueba la compatibilidad existente y agrega todos los GUID, las plantillas, los encabezados y la funcionalidad adicional necesarios para que el proyecto MFC creado por el asistente sea compatible con ATL.  
  
## Ejemplo  
  
```  
var oCM = selProj.CodeModel;  
var L_TRANSACTION_Text = "Add ATL Support To Project";  
oCM.StartTransaction(L_TRANSACTION_Text);  
var bRet = AddATLSupportToProject(selProj);  
if (bRet)  
   oCM.CommitTransaction();  
else  
   oCM.AbortTransaction();  
return bRet;  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [CanAddATLClass](../ide/canaddatlclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)   
 [Introducción a ATL](../atl/introduction-to-atl.md)