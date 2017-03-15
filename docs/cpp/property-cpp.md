---
title: "propiedad (C++) | Microsoft Docs"
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
  - "property_cpp"
  - "Property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], propiedad"
  - "__declspec (palabra clave) de propiedad"
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# propiedad (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Este atributo se puede aplicar a los "miembros de datos virtuales" no estáticos en una definición de clase o estructura.  El compilador trata a estos "miembros de datos virtuales" como miembros de datos y cambia sus referencias en las llamadas de función.  
  
## Sintaxis  
  
```  
  
      __declspec( property( get=get_func_name ) ) declarator  
__declspec( property( put=put_func_name ) ) declarator  
__declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## Comentarios  
 Cuando el compilador consulta un miembro de datos declarado con este atributo en el lado derecho de un operador de selección de miembros \("**.**" o "**\-\>**"\), convierte la operación a una función **get** o **put**, en función de que la expresión sea un valor L o un valor R.  En contextos más complicados, como "`+=`", se realiza una reescritura y se usan ambos, **get** y **put**.  
  
 Este atributo se puede utilizar también en la declaración de una matriz vacía en una definición de clase o estructura.  Por ejemplo:  
  
```  
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 La instrucción anterior indica que `x[]` se puede utilizar con uno o más índices de matriz.  En este caso, `i=p->x[a][b]` se convertirá en `i=p->GetX(a, b)` y `p->x[a][b] = i` se convertirá en `p->PutX(a, b, i);`  
  
 **FIN de Específicos de Microsoft**  
  
## Ejemplo  
  
```  
// declspec_property.cpp  
struct S {  
   int i;  
   void putprop(int j) {   
      i = j;  
   }  
  
   int getprop() {  
      return i;  
   }  
  
   __declspec(property(get = getprop, put = putprop)) int the_prop;  
};  
  
int main() {  
   S s;  
   s.the_prop = 5;  
   return s.the_prop;  
}  
```  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)