---
title: Las plantillas de función | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71bb3985fe870b29d06ebc01d0b7dab4712f1797
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941072"
---
# <a name="function-templates"></a>Plantillas de función
Las plantillas de clase definen una familia de clases relacionadas que se basan en los argumentos de tipo pasados a la clase al crear instancias. Las plantillas de función son similares a las plantillas de clase, pero definen una familia de funciones. Con las plantillas de función, puede especificar un conjunto de funciones que se basen en el mismo código pero que actúen en diferentes tipos o clases. La siguiente plantilla de función intercambia dos elementos:  
  
```cpp
// function_templates1.cpp  
template< class T > void MySwap( T& a, T& b ) {  
   T c(a);   
   a = b;   
   b = c;  
}  
int main() {  
}  
```  
  
 Este código define una familia de funciones que intercambian los valores de los argumentos. En esta plantilla, puede generar funciones que intercambien **int** y **largo** tipos y también tipos definidos por el usuario. `MySwap` intercambiará incluso las clases si el constructor de copias y el operador de asignación de la clase se definen correctamente.  
  
 Además, la plantilla de función, no podrá intercambien objetos de tipos diferentes, porque el compilador conoce los tipos de la *un* y *b* parámetros en tiempo de compilación.  
  
 Aunque esta función se puede ejecutar mediante una función sin plantilla, usando punteros void, la versión de plantilla proporciona seguridad de tipos. Observe las siguientes llamadas:  
  
```cpp
int j = 10;  
int k = 18;  
CString Hello = "Hello, Windows!";  
MySwap( j, k );          //OK  
MySwap( j, Hello );      //error  
```  
  
 La segunda llamada de `MySwap` origina un error en tiempo de compilación, porque el compilador no puede generar una función `MySwap` con parámetros de tipos diferentes. Si se usaran punteros void, ambas llamadas de función se compilarían correctamente, pero la función no funcionaría adecuadamente en tiempo de ejecución.  
  
 Se permite la especificación explícita de los argumentos de plantilla para una plantilla de función. Por ejemplo:  
  
```cpp
// function_templates2.cpp  
template<class T> void f(T) {}  
int main(int j) {  
   f<char>(j);   // Generate the specialization f(char).  
   // If not explicitly specified, f(int) would be deduced.  
}  
```  
  
 Cuando el argumento de plantilla se especifica explícitamente, se realizan las conversiones implícitas normales para convertir el argumento de la función al tipo de los parámetros de la plantilla de función correspondientes. En el ejemplo anterior, el compilador convertirá `char j` escriba **int**.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas](../cpp/templates-cpp.md)   
 [Crear instancias de plantillas de función](../cpp/function-template-instantiation.md)   
 [Creación de instancias explícita](../cpp/explicit-instantiation.md)   
 [Especialización explícita de las plantillas de función](../cpp/explicit-specialization-of-function-templates.md)
