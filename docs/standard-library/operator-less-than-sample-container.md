---
title: "operator&lt; (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std::operator<"
  - "operator<"
  - "std.<"
  - "<"
  - "std.operator<"
  - "std::<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< (operador)"
  - "< (operador), comparar objetos específicos"
  - "operador <, valarrays"
  - "operator<, valarrays"
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator&lt; (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este tema está en la documentación de Visual C\+\+ como ejemplo no funcional de contenedores utilizados en la biblioteca estándar de C\+\+.  Para obtener más información, vea [Contenedores STL](../standard-library/stl-containers.md).  
  
 Overload **operador ?\<** para comparar dos objetos de clase de plantilla [Contenedor](../standard-library/sample-container-class.md).  
  
## Sintaxis  
  
```  
  
   template<class Ty>  
bool operator<(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## Valor devuelto  
 Devuelve `lexicographical_compare`\(\_Left.  [inicio](../standard-library/container-class-begin.md), \_Left.  [final](../standard-library/container-class-end.md), \_Right**.begin**, \_Right.**end**\).  
  
## Vea también  
 [\<sample container\>](../standard-library/sample-container.md)