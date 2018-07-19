---
title: Excepciones y desenredo de pila en C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32558413dd0dc6f7288493067d7373a14e520e29
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944762"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Excepciones y desenredo de pila en C++
En el mecanismo de excepciones de C++, el control se mueve desde la instrucción throw hasta la primera instrucción catch que puede controlar el tipo producido. Cuando se alcanza la instrucción catch, todas las variables automáticas que están en ámbito entre el inicio y la instrucción catch se destruyen en un proceso que se conoce como *desenredo de pila*. En el desenredo de la pila, la ejecución se desarrolla del modo siguiente:  
  
1.  El control alcanza el **intente** instrucción mediante la ejecución secuencial normal. La sección protegida en el **intente** bloque se ejecuta.  
  
2.  Si se produce ninguna excepción durante la ejecución de la sección protegida, la **catch** cláusulas que siguen el **intente** bloque no se ejecutan. La ejecución continúa en la instrucción después del último **catch** cláusula que sigue asociado **intente** bloque.  
  
3.  Si se produce una excepción durante la ejecución de la sección protegida o en cualquier rutina de la sección protegida llama directa o indirectamente, se crea un objeto de excepción desde el objeto que se crea mediante la **throw** operando. (Esto supone que un constructor de copias puede estar implicado). En este momento, el compilador busca un **catch** cláusula en un contexto de ejecución superior que puede controlar una excepción del tipo que se produce, o para un **catch** controlador que puede controlar cualquier tipo de excepción. El **catch** controladores se examinan por orden de aparición después la **intente** bloque. Si no se encuentra ningún controlador adecuado, la siguiente inclusión dinámica **intente** examinar el bloque. Este proceso continúa hasta que la inclusión extremo **intente** examinar el bloque.  
  
4.  Si no se ha encontrado todavía un controlador coincidente, o si se produce una excepción durante el proceso de desenredo pero antes de que el controlador obtenga el control, se llama a la función `terminate` predefinida en tiempo de ejecución. Si se produce una excepción después de que se produzca la excepción pero antes de que empiece el desenredo, se llama a `terminate`.  
  
5.  Si una coincidencia **catch** se encuentra el controlador y detecta por valor, su parámetro formal se inicializa copiando el objeto de excepción. Si detecta por referencia, el parámetro se inicializa para hacer referencia al objeto de excepción. Una vez inicializado el parámetro formal, comienza el proceso de desenredo de la pila. Esto implica la destrucción de todos los objetos automáticos que estaban construidos totalmente, pero todavía no destruidos: entre el comienzo de la **intente** bloque que está asociado el **catch** controlador y el iniciar el sitio de la excepción. La destrucción se produce en orden inverso al de construcción. El **catch** se ejecuta el controlador y el programa reanuda la ejecución después del último controlador, es decir, en la primera instrucción o construcción que no es un **catch** controlador. Control sólo puede especificar un **catch** controlador a través de una excepción producida, nunca a través de un **goto** instrucción o un **caso** etiquetar en un **cambiar** instrucción.  
  
## <a name="stack-unwinding-example"></a>Ejemplo de desenredo de la pila  
 En el ejemplo siguiente se muestra cómo se desenreda la pila cuando se produce una excepción. La ejecución del subproceso salta de la instrucción throw de `C` a la instrucción catch de `main` y desenreda cada función a lo largo del recorrido. Observe el orden en que se crean los objetos `Dummy` y se destruyen después cuando salen del ámbito. Observe también que ninguna función se completa excepto `main`, que contiene la instrucción catch. La función `A` nunca vuelve de la llamada a `B()` y `B` nunca vuelve de la llamada a `C()`. Si quita los comentarios de la definición del puntero de `Dummy` y la correspondiente instrucción delete, y ejecuta después el programa, observe que el puntero nunca se elimina. Esto muestra lo que puede suceder cuando las funciones no proporcionan una garantía de excepción. Para obtener más información, vea Diseñar para excepciones. Si marca como comentario la instrucción catch, puede observar lo que sucede cuando un programa finaliza debido a una excepción no controlada.  
  
```cpp 
#include <string>  
#include <iostream>  
using namespace std;  
  
class MyException{};  
class Dummy  
{  
    public:  
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }  
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }  
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }  
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }  
    string MyName;   
    int level;  
};  
  
void C(Dummy d, int i)  
{   
    cout << "Entering FunctionC" << endl;  
    d.MyName = " C";  
    throw MyException();     
  
    cout << "Exiting FunctionC" << endl;  
}  
  
void B(Dummy d, int i)  
{  
    cout << "Entering FunctionB" << endl;  
    d.MyName = "B";  
    C(d, i + 1);     
    cout << "Exiting FunctionB" << endl;   
}  
  
void A(Dummy d, int i)  
{   
    cout << "Entering FunctionA" << endl;  
    d.MyName = " A" ;  
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!  
    B(d, i + 1);  
 //   delete pd;   
    cout << "Exiting FunctionA" << endl;     
}  
  
int main()  
{  
    cout << "Entering main" << endl;  
    try  
    {  
        Dummy d(" M");  
        A(d,1);  
    }  
    catch (MyException& e)  
    {  
        cout << "Caught an exception of type: " << typeid(e).name() << endl;  
    }  
  
    cout << "Exiting main." << endl;  
    char c;  
    cin >> c;  
}  
  
/* Output:  
    Entering main  
    Created Dummy: M  
    Copy created Dummy: M  
    Entering FunctionA  
    Copy created Dummy: A  
    Entering FunctionB  
    Copy created Dummy: B  
    Entering FunctionC  
    Destroyed Dummy: C  
    Destroyed Dummy: B  
    Destroyed Dummy: A  
    Destroyed Dummy: M  
    Caught an exception of type: class MyException  
    Exiting main.  
  
*/  
  
```  