---
title: "marshal_context::~marshal_context | Microsoft Docs"
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
  - "marshal_context::~marshal_context"
  - "msclr.interop.marshal_context.~marshal_context"
  - "marshal_context.~marshal_context"
  - "msclr::interop::marshal_context::~marshal_context"
  - "~marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context (clase) [C++], operaciones"
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_context::~marshal_context
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Destruye un objeto `marshal_context`.  
  
## Sintaxis  
  
```  
~marshal_context();  
```  
  
## Comentarios  
 Algunas conversiones de datos requieren un contexto de cálculo de referencias.  Vea [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de las traducciones requieren un contexto y la que tiene que incluir el archivo de cálculo de referencias en la aplicación.  
  
 Eliminar un objeto de `marshal_context` reemplazará los datos convertidos por ese contexto.  Si desea conservar los datos después de que se destruya un objeto de `marshal_context` , debe copiar manualmente los datos a una variable que se conserva.  
  
## Requisitos  
 **Archivo de encabezado:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, o \<msclr\\marshal\_atl.h\>  
  
 **Espacio de nombres:** msclr::interop  
  
## Vea también  
 [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context \(Clase\)](../dotnet/marshal-context-class.md)