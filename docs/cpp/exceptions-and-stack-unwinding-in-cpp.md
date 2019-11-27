---
title: Excepciones y desenredo de pila en C++
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 11657206e86dbc81eb62c1e11b49fd87777f11d8
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246565"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Excepciones y desenredo de pila en C++

En el mecanismo de excepciones de C++, el control se mueve desde la instrucción throw hasta la primera instrucción catch que puede controlar el tipo producido. Cuando se alcanza la instrucción Catch, todas las variables automáticas que se encuentran en el ámbito entre las instrucciones Throw y Catch se destruyen en un proceso que se conoce como *desenredado*de la pila. En el desenredo de la pila, la ejecución se desarrolla del modo siguiente:

1. El control alcanza la instrucción **try** mediante la ejecución secuencial normal. Se ejecuta la sección protegida en el bloque **try** .

1. Si no se produce ninguna excepción durante la ejecución de la sección protegida, no se ejecutan las cláusulas **catch** que siguen al bloque **try** . La ejecución continúa en la instrucción después de la última cláusula **catch** que sigue al bloque **try** asociado.

1. Si se produce una excepción durante la ejecución de la sección protegida o en cualquier rutina a la que llame la sección protegida, ya sea directa o indirectamente, se creará un objeto de excepción a partir del objeto creado por el operando **Throw** . (Esto implica que un constructor de copias puede estar implicado). En este momento, el compilador busca una cláusula **catch** en un contexto de ejecución superior que pueda controlar una excepción del tipo que se produce, o para un controlador **catch** que pueda controlar cualquier tipo de excepción. Los controladores **catch** se examinan en orden de aparición después del bloque **try** . Si no se encuentra ningún controlador adecuado, se examina el siguiente bloque **try** de inclusión dinámica. Este proceso continúa hasta que se examina el bloque **try** más externo.

1. Si no se ha encontrado todavía un controlador coincidente, o si se produce una excepción durante el proceso de desenredo pero antes de que el controlador obtenga el control, se llama a la función `terminate` predefinida en tiempo de ejecución. Si se produce una excepción después de que se produzca la excepción pero antes de que empiece el desenredo, se llama a `terminate`.

1. Si se encuentra un controlador **catch** coincidente y captura por valor, su parámetro formal se inicializa copiando el objeto de excepción. Si detecta por referencia, el parámetro se inicializa para hacer referencia al objeto de excepción. Una vez inicializado el parámetro formal, comienza el proceso de desenredo de la pila. Esto implica la destrucción de todos los objetos automáticos que se han creado por completo, pero que aún no se han desestructurado, entre el principio del bloque **try** que está asociado con el controlador **catch** y el sitio Throw de la excepción. La destrucción se produce en orden inverso al de construcción. Se ejecuta el controlador **catch** y el programa reanuda la ejecución después del último controlador, es decir, en la primera instrucción o construcción que no es un controlador **catch** . El control solo puede escribir un controlador **catch** a través de una excepción producida, nunca a través de una instrucción **goto** o una etiqueta **Case** en una instrucción **Switch** .

## <a name="stack-unwinding-example"></a>Ejemplo de desenredado de la pila

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
