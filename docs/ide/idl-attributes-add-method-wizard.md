---
title: "Atributos IDL, Asistente para agregar m&#233;todos | Microsoft Docs"
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
  - "vc.codewiz.method.idlattrib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para agregar métodos [C++]"
  - "Atributos IDL, Asistente para agregar métodos"
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Atributos IDL, Asistente para agregar m&#233;todos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta página del Asistente para agregar métodos se utiliza para especificar la configuración del lenguaje de definición de interfaz \(IDL\) del método.  
  
 **id**  
 Permite especificar el identificador numérico del método.  Vea [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  
  
 Este cuadro no está disponible con las interfaces personalizadas o las dispinterfaces de MFC.  
  
 **call\_as**  
 Especifica el nombre de un método remoto con el que se puede asociar el método local.  Vea [call\_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  
  
 No están disponibles para dispinterfaces de MFC.  
  
 **helpcontext**  
 Especifica un identificador de contexto que le permite al usuario ver información sobre el método en el archivo de Ayuda.  Vea [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  
  
 No están disponibles para dispinterfaces de MFC.  
  
 **helpstring**  
 Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica.  De forma predeterminada, toma el valor "method *Nombre de método*". Vea [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.  
  
 No están disponibles para dispinterfaces de MFC.  
  
 **Atributos adicionales**  
 No están disponibles para dispinterfaces de MFC.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|**hidden**|Indica que, aunque el método existe, no deberá mostrarse en exploradores orientados al usuario.  Vea [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**source**|Indica que un miembro del método es un origen de eventos.  Vea [source](http://msdn.microsoft.com/library/windows/desktop/aa367166) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|`local`|Le especifica al compilador MIDL que el método no es remoto.  Vea [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**restricted**|Especifica que no se puede llamar al método arbitrariamente.  Vea [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) en *MIDL Reference* \(Referencia del lenguaje MIDL\).|  
|**vararg**|Especifica que el método toma un número variable de argumentos.  Para ello, el último argumento deberá ser una matriz segura de tipo **VARIANT** que contenga todos los argumentos restantes.  Vea [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) en *MIDL Reference \(*Referencia del lenguaje MIDL*\)*.|  
  
## Vea también  
 [Agregar un método](../ide/adding-a-method-visual-cpp.md)   
 [Asistente para agregar métodos](../ide/add-method-wizard.md)