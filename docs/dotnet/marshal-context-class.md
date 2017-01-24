---
title: "marshal_context (Clase) | Microsoft Docs"
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
  - "marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context (clase) [C++]"
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_context (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta clase convierte los datos entre los entornos nativo y administrado.  
  
## Sintaxis  
  
```  
class marshal_context  
```  
  
## Comentarios  
 Utilice la clase de `marshal_context` para las conversiones de datos que requieren un contexto.  Vea [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md) para obtener más información acerca de las conversiones requieren un contexto y la que tiene que incluir el archivo de cálculo de referencias.  El resultado del cálculo cuando usa un contexto solo es válido hasta que se destruye el objeto de `marshal_context` .  Para mantener el resultado, debe copiar los datos.  
  
 Mismo `marshal_context` se puede utilizar para las conversiones de datos.  Reutilizar el contexto de esta manera no afecta a los resultados de llamadas anteriores de cálculo de referencias.  
  
## Requisitos  
 **Archivo de encabezado:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, o \<msclr\\marshal\_atl.h\>  
  
 **Espacio de nombres:** msclr::interop  
  
## Vea también  
 [Información general del cálculo de referencias en C\+\+](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)