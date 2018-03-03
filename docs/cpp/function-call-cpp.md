---
title: "Función de llamada (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C++ functions
- functions [C++], calling
- operator overloading [C++], function calls
- function overloading [C++], function-call operator
- function calls, operator
- operators [C++], overloading
- operator overloading [C++], examples
- function call operator ()
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6d130f087f635306083e58faf7c77b252fc9360
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="function-call-c"></a>Llamada de función (C++)
El operador de llamada a función, invocado mediante paréntesis, es un operador binario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
primary-expression ( expression-list )  
```  
  
## <a name="remarks"></a>Comentarios  
 En este contexto, `primary-expression` es el primer operando, y `expression-list` (una lista de argumentos que posiblemente esté vacía) es el segundo operando. El operador de llamada a función se utiliza para las operaciones que requieren varios parámetros. Esto funciona porque `expression-list` es una lista en lugar de un solo operando. El operador de llamada a función debe ser una función miembro no estática.  
  
 El operador de llamada a función, cuando está sobrecargado, no modifica la forma de llamar a las funciones; en su lugar, modifica cómo debe interpretarse el operador cuando se aplica a objetos de un tipo de clase especificado. Por ejemplo, el código siguiente normalmente no tendría sentido:  
  
```  
Point pt;  
pt( 3, 2 );  
```  
  
 Pero, con un operador sobrecargado de llamada a función adecuado, esta sintaxis se puede usar para desplazar 3 unidades la coordenada `x` y 2 unidades la coordenada `y`. En el código siguiente se muestra esa definición:  
  
```  
// function_call.cpp  
class Point  
{  
public:  
    Point() { _x = _y = 0; }  
    Point &operator()( int dx, int dy )  
        { _x += dx; _y += dy; return *this; }  
private:  
    int _x, _y;  
};  
  
int main()  
{  
   Point pt;  
   pt( 3, 2 );  
}  
```  
  
 Tenga en cuenta que el operador de llamada a función se aplica al nombre de un objeto, no al nombre de una función.  
  
 También puede sobrecargar el operador de llamada de función mediante un puntero a una función (en lugar de a la función en sí).  
  
```cpp  
typedef void(*ptf)();  
void func()  
{  
}  
struct S  
{  
   operator ptf()  
   {  
      return func;  
   }  
};  
  
int main()  
{  
   S s;  
   s();//operates as s.operator ptf()()  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)