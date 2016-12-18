---
title: "Excepciones y desenredo de pila en C++ | Microsoft Docs"
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
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Excepciones y desenredo de pila en C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el mecanismo de excepciones de C\+\+, el control se mueve desde la instrucción throw hasta la primera instrucción catch que puede controlar el tipo producido.  Cuando se alcanza la instrucción catch, todas las variables automáticas que están en el ámbito entre las instrucciones throw y catch se destruyen en un proceso que se conoce como *desenredo de la pila*.  En el desenredo de la pila, la ejecución se desarrolla del modo siguiente:  
  
1.  El control alcanza la instrucción `try` mediante la ejecución secuencial normal.  La sección protegida en el bloque de `try` se ejecuta.  
  
2.  Si no se produce ninguna excepción durante la ejecución de la sección protegida, las cláusulas `catch` que siguen al bloque de `try` no se ejecutan.  La ejecución continúa en la instrucción después de la última cláusula `catch` que sigue al bloque de `try` asociado.  
  
3.  Si se produce una excepción durante la ejecución de la sección protegida o en cualquier rutina a la que la sección protegida llama directa o indirectamente, se crea un objeto de excepción desde el objeto creado por el operando `throw`. \(Esto supone que un constructor de copias puede estar implicado\). En este punto, el compilador busca una cláusula `catch` en un contexto de ejecución superior que pueda controlar una excepción del tipo que se produce, o un controlador de `catch` que pueda controlar cualquier tipo de excepción.  Los controladores de `catch` se examinan en orden de aparición después del bloque de `try`.  Si no se encuentra ningún controlador adecuado, se examina el siguiente bloque de `try` de inclusión dinámica.  Este proceso continúa hasta que se examina el bloque de `try` de inclusión extremo.  
  
4.  Si no se ha encontrado todavía un controlador coincidente, o si se produce una excepción durante el proceso de desenredo pero antes de que el controlador obtenga el control, se llama a la función `terminate` predefinida en tiempo de ejecución.  Si se produce una excepción después de que se produzca la excepción pero antes de que empiece el desenredo, se llama a `terminate`.  
  
5.  Si se encuentra un controlador de `catch` coincidente y detecta por valor, su parámetro formal se inicializa copiando el objeto de excepción.  Si detecta por referencia, el parámetro se inicializa para hacer referencia al objeto de excepción.  Una vez inicializado el parámetro formal, comienza el proceso de desenredo de la pila.  Esto implica la destrucción de todos los objetos automáticos que estaban construidos totalmente, pero todavía no destruidos, entre el principio del bloque de `try` asociado al controlador de `catch` y el sitio de producción de la excepción.  La destrucción se produce en orden inverso al de construcción.  Se ejecuta el controlador de `catch` y el programa reanuda la ejecución después del último controlador, es decir, en la primera instrucción o construcción que no es un controlador de `catch`.  El control solo puede entrar en un controlador de `catch` a través de una excepción producida, nunca a través de una instrucción `goto` o una etiqueta `case` en una instrucción `switch`.  
  
## Ejemplo de desenredo de la pila  
 En el ejemplo siguiente se muestra cómo se desenreda la pila cuando se produce una excepción.  La ejecución del subproceso salta de la instrucción throw de `C` a la instrucción catch de `main` y desenreda cada función a lo largo del recorrido.  Observe el orden en que se crean los objetos `Dummy` y se destruyen después cuando salen del ámbito.  Observe también que ninguna función se completa excepto `main`, que contiene la instrucción catch.  La función `A` nunca vuelve de la llamada a `B()` y `B` nunca vuelve de la llamada a `C()`.  Si quita los comentarios de la definición del puntero de `Dummy` y la correspondiente instrucción delete, y ejecuta después el programa, observe que el puntero nunca se elimina.  Esto muestra lo que puede suceder cuando las funciones no proporcionan una garantía de excepción.  Para obtener más información, vea Diseñar para excepciones.  Si marca como comentario la instrucción catch, puede observar lo que sucede cuando un programa finaliza debido a una excepción no controlada.  
  
```  
#include <string>  
#include <iostream>  
using namespace std;  
  
class MyException{};  
class Dummy  
{  
    public:  
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }  
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }  
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }  
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }  
    string MyName;   
    int level;  
};  
  
void C(Dummy d, int i)  
{   
    cout << "Entering FunctionC" << endl;  
    d.MyName = " C";  
    throw MyException();     
  
    cout << "Exiting FunctionC" << endl;  
}  
  
void B(Dummy d, int i)  
{  
    cout << "Entering FunctionB" << endl;  
    d.MyName = "B";  
    C(d, i + 1);     
    cout << "Exiting FunctionB" << endl;   
}  
  
void A(Dummy d, int i)  
{   
    cout << "Entering FunctionA" << endl;  
    d.MyName = " A" ;  
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!  
    B(d, i + 1);  
 //   delete pd;   
    cout << "Exiting FunctionA" << endl;     
}  
  
int main()  
{  
    cout << "Entering main" << endl;  
    try  
    {  
        Dummy d(" M");  
        A(d,1);  
    }  
    catch (MyException& e)  
    {  
        cout << "Caught an exception of type: " << typeid(e).name() << endl;  
    }  
  
    cout << "Exiting main." << endl;  
    char c;  
    cin >> c;  
}  
  
/* Output:  
    Entering main  
    Created Dummy: M  
    Copy created Dummy: M  
    Entering FunctionA  
    Copy created Dummy: A  
    Entering FunctionB  
    Copy created Dummy: B  
    Entering FunctionC  
    Destroyed Dummy: C  
    Destroyed Dummy: B  
    Destroyed Dummy: A  
    Destroyed Dummy: M  
    Caught an exception of type: class MyException  
    Exiting main.  
  
*/  
  
```