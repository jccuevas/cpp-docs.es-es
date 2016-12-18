---
title: "Declaraciones y definiciones (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Declaraciones y definiciones (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las [declaraciones](http://msdn.microsoft.com/es-es/2fd0cddb-b64c-4c9f-9aac-9f8e7ef892f4) introducen nombres en un programa, por ejemplo, nombres de variables, espacios de nombres, funciones y clases.  Las declaraciones también especifican información de tipos y otras características del objeto que se declara.  Antes de poder usar un nombre, hay que declararlo; en C\+\+, el punto en el que se declara un nombre determina si es visible para el compilador.  No se puede hacer referencia a una función o clase que se declara en algún punto posterior de la unidad de compilación; para superar esta limitación, pueden usarse *declaraciones adelantadas*.  
  
 Las [definiciones](http://msdn.microsoft.com/es-es/f96e2c0d-abb5-4414-9ea1-4d5b4048d50a) especifican qué código o datos describe el nombre.  El compilador necesita la definición a fin de asignar espacio de almacenamiento para el elemento que se declara.  
  
## Declaraciones  
 Una declaración introduce uno o más nombres en un programa.  Las declaraciones pueden aparecer varias veces en un programa.  Por tanto, las clases, estructuras, tipos enumerados y otros tipos definidos por el usuario se pueden declarar para cada unidad de compilación.  La restricción de esta declaración múltiple es que todas las declaraciones deben ser idénticas.  Las declaraciones también actúan como definiciones, excepto cuando la declaración:  
  
1.  Es un prototipo de función \(una declaración de función sin cuerpo de función\).  
  
2.  Contiene el especificador `extern` pero ningún inicializador \(objetos y variables\) o cuerpo de función \(funciones\).  Esto significa que la definición no está necesariamente en la unidad de traducción actual y proporciona al nombre vinculación externa.  
  
3.  Es de un miembro de datos estático en una declaración de clase.  
  
     Como los miembros de datos estáticos de clase son variables discretas compartidas por todos los objetos de la clase, se deben definir e inicializar fuera de la declaración de clase.  \(Para obtener más información sobre las clases y miembros de clase, vea [Clases](../cpp/classes-and-structs-cpp.md)\).  
  
4.  Es una declaración de nombre de clase sin la siguiente definición, como `class T;`.  
  
5.  Es una instrucción `typedef`.  
  
 Estos son algunos ejemplos de declaraciones que también son definiciones:  
  
```  
// Declare and define int variables i and j.  
int i;  
int j = 10;  
  
// Declare enumeration suits.  
enum suits { Spades = 1, Clubs, Hearts, Diamonds };  
  
// Declare class CheckBox.  
class CheckBox : public Control  
{  
public:  
            Boolean IsChecked();  
    virtual int     ChangeState() = 0;  
};  
```  
  
 Algunas declaraciones que no son definiciones son:  
  
```  
  
extern int i;  
char *strchr( const char *Str, const char Target );  
```  
  
 Se considera que un nombre se declara inmediatamente después de su declarador pero antes de su inicializador \(opcional\).  Para más información, vea [Punto de declaración](../cpp/point-of-declaration-in-cpp.md).  
  
 Las declaraciones tienen lugar en un *ámbito*.  El ámbito controla la visibilidad del nombre declarado y la duración del objeto definido, si existe.  Para obtener más información sobre la interacción entre las reglas de ámbito y las declaraciones, vea [Ámbito](../cpp/scope-visual-cpp.md).  
  
 Una declaración de objeto es también una definición a menos que contenga el especificador de clase de almacenamiento `extern` que se describe en [Especificadores de clase de almacenamiento](http://msdn.microsoft.com/es-es/10b3d22d-cb40-450b-994b-08cf9a211b6c).  Una declaración de función es también una definición a menos que sea un prototipo.  Un prototipo es un encabezado de función sin un cuerpo de definición de la función.  La definición de un objeto provoca la asignación del almacenamiento y las inicializaciones adecuadas para ese objeto.  
  
## Definiciones  
 Una definición es una especificación única de un objeto o una variable, función, clase o enumerador.  Como las definiciones deben ser únicas, un programa solo puede contener una definición para un determinado elemento de programa.  Puede haber una correspondencia varios a uno entre las declaraciones y definiciones.  Hay dos casos en los que un elemento de programa puede estar declarado y no definido:  
  
1.  Se declara una función pero nunca se hace referencia a ella con una llamada de función o una expresión que tome la dirección de la función.  
  
2.  Una clase solo se utiliza de forma que no sea necesario conocer su definición.  Sin embargo, la clase debe declararse.  En el código siguiente se muestra este caso:  
  
    ```  
    // definitions.cpp  
    class WindowCounter;   // Forward declaration; no definition  
  
    class Window  
    {  
       // Definition of WindowCounter not required  
       static WindowCounter windowCounter;  
    };  
  
    int main()  
    {  
    }  
    ```  
  
## Vea también  
 [Conceptos básicos](../cpp/basic-concepts-cpp.md)   
 [Punto de declaración](../cpp/point-of-declaration-in-cpp.md)