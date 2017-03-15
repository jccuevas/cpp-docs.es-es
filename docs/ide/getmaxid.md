---
title: "GetMaxID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetMaxID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMaxID (método)"
ms.assetid: a155ec2e-6132-4e40-9b85-d710538778a1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetMaxID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el identificador de envío \(dispid\) más alto de los miembros de la interfaz, así como todas sus bases.  
  
## Sintaxis  
  
```  
  
      function GetMaxID(   
   ointerface    
);  
```  
  
#### Parámetros  
 *ointerface*  
 Objeto <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeInterface>.  
  
## Valor devuelto  
 El identificador de envío \(dispid\) más alto de los miembros de *oInterface*, así como todas sus bases.  
  
## Comentarios  
 Se llama a esta función para obtener el identificador de envío \(dispid\) más alto de los miembros de la interfaz especificada, así como todas sus bases.  
  
## Ejemplo  
  
```  
if (strInterfaceType == "custom")  
      window.external.AddSymbol("DISPID_DISABLED", true);  
   else  
   {  
      var nDispID = window.external.FindSymbol("DISPID");  
      if (!nDispID.length)  
      {  
         nDispID = GetMaxID(oInterface) + 1;  
         window.external.AddSymbol("DISPID", nDispID);  
      }  
   }  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)