---
title: "marshal_context::marshal_context | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::interop::marshal_context::marshal_context"
  - "marshal_context::marshal_context"
  - "msclr.interop.marshal_context.marshal_context"
  - "marshal_context.marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context (clase) [C++], operaciones"
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_context::marshal_context
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto de `marshal_context` necesarios para la conversión de datos entre los tipos de datos administrados y nativos.  
  
## Sintaxis  
  
```  
marshal_context();  
```  
  
## Comentarios  
 Algunas conversiones de datos requieren un contexto de cálculo de referencias.  Vea [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de las traducciones requieren un contexto y la que tiene que incluir el archivo de cálculo de referencias en la aplicación.  
  
## Ejemplo  
 Consulte el ejemplo de [marshal\_context::marshal\_as](../dotnet/marshal-context-marshal-as.md).  
  
## Requisitos  
 **Archivo de encabezado:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, o \<msclr\\marshal\_atl.h\>  
  
 **Espacio de nombres:** msclr::interop  
  
## Vea también  
 [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context \(Clase\)](../dotnet/marshal-context-class.md)