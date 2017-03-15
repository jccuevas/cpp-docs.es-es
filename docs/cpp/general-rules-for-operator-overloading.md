---
title: "Reglas generales para la sobrecarga de operadores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sobrecarga de operadores, reglas"
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Reglas generales para la sobrecarga de operadores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las reglas siguientes restringen la forma en que se implementan los operadores sobrecargados.  Sin embargo, no se aplican a los operadores [new](../cpp/new-operator-cpp.md) y [delete](../cpp/delete-operator-cpp.md), que se tratan por separado.  
  
-   No se pueden definir operadores nuevos, por ejemplo \*\*.  
  
-   No se puede volver a definir el significado de los operadores cuando se aplican a los tipos de datos integrados.  
  
-   Los operadores sobrecargados deben ser una función miembro de clase no estática o una función global.  Una función global que necesita acceso a miembros de clase privados o protegidos se debe declarar como friend de esa clase.  Una función global debe tomar al menos un argumento que sea de clase o de tipo enumerado, o que sea una referencia a una clase o a un tipo enumerado.  Por ejemplo:  
  
    ```  
    // rules_for_operator_overloading.cpp  
    class Point  
    {  
    public:  
        Point operator<( Point & );  // Declare a member operator   
                                     //  overload.  
        // Declare addition operators.  
        friend Point operator+( Point&, int );  
        friend Point operator+( int, Point& );  
    };  
  
    int main()  
    {  
    }  
    ```  
  
     En el ejemplo de código anterior se declara el operador "menos que" como función miembro; sin embargo, los operadores de suma se declaran como funciones globales con acceso de confianza.  Observe que se puede proporcionar más de una implementación para un operador determinado.  En el caso del operador de suma anterior, las dos implementaciones se proporcionan para facilitar la propiedad conmutativa.  También es probable que puedan implementarse operadores que agregan `Point` a `Point`, `int` a `Point`, etc.  
  
-   Los operadores obedecen a la prioridad, la agrupación y el número de operandos dictados por su uso típico con los tipos integrados.  Por consiguiente, no hay ninguna forma de expresar el concepto "sumar 2 y 3 a un objeto de tipo `Point`" con la expectativa de que 2 se sume a la coordenada *X* y 3 se sume a la coordenada *Y*.  
  
-   Los operadores unarios declarados como funciones miembro no toman ningún argumento; si se declaran como funciones globales, toman un argumento.  
  
-   Los operadores binarios declarados como funciones miembro toman un argumento; si se declaran como funciones globales, toman dos argumentos.  
  
-   Si un operador puede utilizarse como operador unario u operador binario \(**&**, **\***, **\+** y **\-**\), se puede sobrecargar cada uso por separado.  
  
-   Los operadores sobrecargados no pueden tener argumentos predeterminados.  
  
-   Las clases derivadas heredan todos los operadores sobrecargados, excepto el de asignación \(`operator=`\).  
  
-   El primer argumento para los operadores sobrecargados de función miembro siempre es del tipo de clase del objeto para el que se invoca el operador \(la clase en la que se declara el operador o una clase derivada de ella\).  No se proporciona ninguna conversión para el primer argumento.  
  
 Observe que el significado de cualquiera de los operadores se puede cambiar por completo.  Esto incluye el significado de los operadores address\-of \(**&**\), de asignación \(**\=**\) y de llamada a función.  Además, las identidades en las que se puede confiar para los tipos integrados pueden cambiarse mediante la sobrecarga de operadores.  Por ejemplo, las cuatro instrucciones siguientes suelen ser equivalentes cuando se evalúan completamente:  
  
```  
var = var + 1;  
var += 1;  
var++;  
++var;  
```  
  
 No se puede confiar en esta identidad para los tipos de clase que sobrecargan operadores.  Además, algunos requisitos implícitos en el uso de estos operadores para los tipos básicos se relajan para los operadores sobrecargados.  Por ejemplo, el operador de suma o asignación, `+=`, requiere que el operando izquierdo sea un valor L cuando se aplica a los tipos básicos; este requisito no existe cuando se sobrecarga el operador.  
  
> [!NOTE]
>  Por coherencia, a menudo es mejor seguir el modelo de los tipos integrados al definir operadores sobrecargados.  Si la semántica de un operador sobrecargado difiere mucho de su significado en otros contextos, puede ser más confusa que útil.  
  
## Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)