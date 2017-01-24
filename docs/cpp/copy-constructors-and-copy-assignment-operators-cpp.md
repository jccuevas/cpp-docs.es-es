---
title: "Constructores de copia y operadores de asignaci&#243;n de copia (C++) | Microsoft Docs"
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
helpviewer_keywords: 
  - "= (operador), copiar objetos"
  - "asignar valores para copiar objetos"
  - "operadores de asignación, para copiar objetos"
  - "instrucciones de asignación, copiar objetos"
  - "copiar objetos"
  - "inicializar objetos, mediante copia de objetos"
  - "objetos [C++], copiar"
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Constructores de copia y operadores de asignaci&#243;n de copia (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  A partir de C\+\+ 11, se admiten dos tipos de asignación en el lenguaje: *asignación de copia* y *asignación de movimiento*.  En este artículo, "asignación" significa asignación de copia a menos que se establezca explícitamente lo contrario.  Para obtener información sobre la asignación de movimiento, consulte [Operadores de constructores de movimiento y asignaciones de movimiento \(C\+\+\)](http://msdn.microsoft.com/es-es/1442de5f-37a5-42a1-83a6-ec9cfe0414db).  
>   
>  Tanto la operación de asignación como la operación de inicialización provocan que los objetos se copien.  
  
-   **Asignación**: cuando se asigna el valor de un objeto a otro objeto, el primer objeto se copia en el segundo objeto.  Por lo tanto,  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     hace que el valor de `b` se copie en `a`.  
  
-   **Inicialización**: La inicialización se produce cuando se declara un nuevo objeto, cuando los argumentos se pasan a las funciones por valor o cuando los valores se devuelven de las funciones por valor.  
  
 Puede definir la semántica de “copy” para los objetos de tipo de clase.  Por ejemplo, considere este código:  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 El código anterior podría significar “copiar el contenido de FILE1.DAT en FILE2.DAT” o podría significar “omitir FILE2.DAT y convertir `b` en un segundo identificador para FILE1.DAT”. Debe asociar la semántica de copia correspondiente a cada clase, de la manera siguiente.  
  
-   Mediante el operador de asignación `operator=`, junto con una referencia al tipo de clase como tipo de valor devuelto y el parámetro que se pasa por referencia `const`; por ejemplo, `ClassName& operator=(const ClassName& x);`.  
  
-   Utilizando el constructor de copias.  Para obtener más información sobre el constructor de copias, vea [Reglas para la declaración de constructores](../misc/rules-for-declaring-constructors.md).  
  
 Si no declara un constructor de copias, el compilador genera uno automáticamente miembro a miembro.  Si no declara una asignación de copia, el compilador genera una automáticamente miembro a miembro. Declarar un constructor de copias no suprime el operador de asignación de copias generado por el compilador, ni viceversa.  Si se implementa cualquiera de ellos, es recomendable implementar también el otro de modo que el significado del código esté claro.  
  
 La asignación miembro a miembro se trata con más detalle en [\(NOTINBUILD\) Memberwise Assignment and Initialization](http://msdn.microsoft.com/es-es/94048213-8b49-4416-8069-b1b7a6f271f9).  
  
 El constructor de copias toma un argumento de tipo *class\-name***&**, donde *class\-name* es el nombre de la clase para la que se define el constructor.  Por ejemplo:  
  
```cpp  
// spec1_copying_class_objects.cpp  
class Window  
{  
public:  
    Window( const Window& ); // Declare copy constructor.  
    // ...  
};  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  Haga que el tipo del argumento del constructor de copias sea *const class\-name***&** siempre que sea posible.  Esto evita que el constructor de copias modifique accidentalmente el objeto del que se está copiando.  También permite copiar de objetos **const**.  
  
## Constructores de copias generados por el compilador  
 Los constructores de copias generados por el compilador, como los constructores de copias definidos por el usuario, tienen un único argumento de tipo "referencia a *class\-name*". La excepción es cuando todas las clases base y las clases de miembro tienen constructores de copias declarados de modo que toman un solo argumento de tipo **const** *class\-name***&**.  En ese caso, el argumento del constructor de copias generado por el compilador también es **const**.  
  
 Cuando el tipo de argumento al constructor de copias no es **const**, la inicialización que se realiza copiando un objeto **const** genera un error.  Lo contrario no es cierto: si el argumento es **const**, puede inicializar copiando un objeto que no sea **const**.  
  
 Los operadores de asignación generados por el compilador siguen el mismo patrón con respecto a **const**. Toman un solo argumento de tipo *class\-name***&** a menos que los operadores de asignaciones de todas las clases base y clases de miembro tomen argumentos de tipo **const** *class\-name&*. En este caso, el operador de asignación generado de la clase toma un argumento **const**.  
  
> [!NOTE]
>  Cuando los constructores de copias, generados por el compilador o definidos por el usuario, inicializan las clases base virtuales, estas se inicializan solo una vez: en el momento en que se construyen.  
  
 Las implicaciones son similares a las del constructor de copias.  Cuando el tipo del argumento no es **const**, la asignación de un objeto **const** genera un error.  Lo contrario no es cierto: si un valor **const** se asigna a un valor que no es **const**, la asignación se realiza correctamente.  
  
 Para obtener más información sobre los operadores de asignaciones sobrecargados, vea [Asignación](../cpp/assignment.md).  
  
## Vea también  
 [Funciones miembro especiales](../misc/special-member-functions-cpp.md)