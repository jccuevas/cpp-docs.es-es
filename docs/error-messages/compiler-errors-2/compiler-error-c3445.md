---
title: C3445 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: c89d7f1f13829422a330960ac319531fc551fb97
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3445"></a>C3445 de Error del compilador
lista de inicialización de copia de '*tipo*' no se puede utilizar un constructor explícito  
  
Según el estándar C ++ 17 ISO, el compilador es necesario tener en cuenta un constructor explícito para la resolución de sobrecarga en la inicialización de la lista de copia, pero debe generar un error si se elige esa sobrecarga.  
  
A partir de Visual Studio de 2017, el compilador no encuentra errores relacionados con la creación de objetos mediante el uso de una lista de inicializadores que no se encontraron mediante Visual Studio 2015. Estos errores pudieron provocar errores o un comportamiento indefinido en tiempo de ejecución.

## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3445.  
  
```cpp  
// C3445.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of 
                      //     'A' cannot use an explicit constructor
}
```  
  
Para corregir el error, utilice en su lugar la inicialización directa:  
  
```cpp  
// C3445b.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1{ 1 };
}  
```  
  
