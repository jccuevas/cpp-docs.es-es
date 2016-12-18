---
title: "noreturn | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noreturn_cpp"
  - "noreturn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], noreturn"
  - "noreturn __declspec (palabra clave)"
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noreturn
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Este atributo `__declspec` indica al compilador que una función no devuelve resultados.  Como consecuencia, el compilador sabe que no se puede tener acceso al código que sigue a una llamada a una función **\_\_declspec\(noreturn\)**.  
  
 Si el compilador encuentra una función con una ruta de acceso de control que no devuelve un valor, genera una advertencia \(C4715\) o un mensaje de error \(C2202\).  Si no se puede tener acceso a la ruta de acceso de control debido a una función que nunca devuelve resultados, puede utilizar **\_\_declspec\(noreturn\)** para evitar esta advertencia o este error.  
  
> [!NOTE]
>  La adición de **\_\_declspec\(noreturn\)** a una función que se espera que devuelva resultados puede dar lugar a un comportamiento indefinido.  
  
## Ejemplo  
 En el ejemplo siguiente, la cláusula **else** no contiene una instrucción return.  La declaración de `fatal` como **\_\_declspec\(noreturn\)** evita un mensaje de error o de advertencia.  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)