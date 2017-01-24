---
title: "CanAddNonAttributed | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CanAddNonAttributed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddNonAttributed (método)"
ms.assetid: a2b0143e-f84b-40f3-8f51-23a492f651f8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CanAddNonAttributed
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica que el proyecto ATL es compatible con objetos sin atributos.  
  
## Sintaxis  
  
```  
  
function CanAddNonAttributed( );  
  
```  
  
## Valor devuelto  
 **true** si el proyecto es compatible con objetos ATL con y sin atributos; **false** si el proyecto sólo es compatible con proyectos con atributos.  
  
## Comentarios  
 Se llama a esta función para indicar si el proyecto admite objetos tanto con atributos como sin ellos.  
  
## Ejemplo  
  
```  
// Check if attributed project using CanAddNonAttributed  
window.external.Load(document);  
if (IsAttributedProject(window.external))  
{  
   ATTRIBUTED.checked = true;  
   if (!CanAddNonAttributed())  
      ATTRIBUTED.disabled = true;  
}  
```  
  
## Vea también  
 [Personalizar los asistentes de C\+\+ con funciones comunes de JScript](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Funciones de JScript para los asistentes de C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)   
 [Concepts](../windows/attributed-programming-concepts.md)   
 [CanAddClass](../ide/canaddclass.md)