---
title: "Clase is_default_constructible | Microsoft Docs"
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
  - "is_default_constructible"
  - "std.is_default_constructible"
  - "std::is_default_constructible"
  - "type_traits/std::is_default_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_default_constructible"
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
caps.latest.revision: 14
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase is_default_constructible
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si un tipo tiene un constructor predeterminado.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_default_constructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` es una clase que tiene un constructor predeterminado; en caso contrario, es false. Es equivalente al elemento `is_constructible<T>` del predicado. El tipo `T` debe ser un tipo completo, `void`, o una matriz de límite desconocido.  
  
## Ejemplo  
  
```cpp  
  
#include <type_traits>   
#include <iostream>   
  
struct Simple  
{  
    Simple() : val(0) {}  
    int val;  
};  
  
struct Simple2  
{  
    Simple2(int v) : val(v) {}  
    int val;  
};  
  
int main()  
{  
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha  
        << std::is_default_constructible<Simple>::value << std::endl;  
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha  
        << std::is_default_constructible<Simple2>::value << std::endl;  
  
    return (0);  
}  
  
```  
  
```Output  
is_default_constructible<Simple> == true is_default_constructible<Simple2> == false  
```  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)