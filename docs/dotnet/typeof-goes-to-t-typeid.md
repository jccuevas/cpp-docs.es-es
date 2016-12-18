---
title: "T::typeid reemplaza typeof | Microsoft Docs"
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
  - "__typeof (palabra clave)"
  - "typeid (palabra clave) [C++]"
  - "typeid (operador)"
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# T::typeid reemplaza typeof
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `typeid` ha suplantado al operador `typeof` utilizado en Extensiones administradas para C\+\+ en [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En Extensiones administradas, el operador `__typeof()` devuelve el objeto `Type*` asociado cuando se pasa el nombre de un tipo administrado.  Por ejemplo:  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 En la nueva sintaxis, un formulario adicional de `typeid` que devuelve `Type^` ha reemplazado a `__typeof` cuando se especifica un tipo administrado.  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## Vea también  
 [Cambio general en el lenguaje](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md)