---
title: Declaración de un objeto de clase de referencia CLR | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- types [C++], reference types
- reference types, CLR
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 12cead3a142c69da56390ca6f5bf32cecc3b0075
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="declaration-of-a-clr-reference-class-object"></a>Declaración de un objeto de una clase de referencia de CLR
La sintaxis para declarar y crear instancias de un objeto de un tipo de clase de referencia ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En extensiones administradas, un objeto de tipo de clase de referencia se declara mediante la sintaxis de puntero de ISO C++, con el uso opcional de la `__gc` palabra clave a la izquierda de la estrella (`*`). Por ejemplo, incluimos una variedad de referencia de las declaraciones de objeto del tipo de clase en la sintaxis de extensiones administradas:  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   Button __gc *button1;  
   DataGrid __gc *myDataGrid;     
   DataSet __gc *myDataSet;  
  
   void PrintValues( Array* myArr ) {  
      System::Collections::IEnumerator* myEnumerator =   
         myArr->GetEnumerator();  
  
      Array *localArray;  
      myArr->Copy(myArr, localArray, myArr->Length);  
   }  
};  
```  
  
 En la nueva sintaxis, se declara un objeto de tipo de clase de referencia mediante un nuevo token declarativo (`^`) denominado formalmente como un *identificador de seguimiento* y más informalmente como un *hat*. (El término seguimiento significa que un tipo de referencia se encuentra dentro del montón CLR y puede, por tanto, mover de manera transparente ubicaciones durante la compactación del montón de elementos no utilizados. Un controlador de seguimiento se actualiza de forma transparente durante el tiempo de ejecución. Dos conceptos similares son la *referencia de seguimiento* (`%`) y el *puntero interior* (`interior_ptr<>`), descrito en [la semántica de tipos de valor](../dotnet/value-type-semantics.md).  
  
 Las razones principales para abandonar la sintaxis declarativa y volver a utilizar de la sintaxis de puntero de ISO C++ son los siguientes:  
  
-   El uso de la sintaxis de puntero no permitía operadores sobrecargados para aplicarse directamente a un objeto de referencia. En su lugar, se tenía que llamar al operador mediante su nombre interno, como `rV1->op_Addition(rV2)` en lugar de más intuitiva `rV1+rV2`.  
  
-   Montón restante tras un número de operaciones de puntero, como la conversión y la aritmética con punteros, que no se permite para los objetos almacenados en un elementos no utilizados. La noción de un controlador de seguimiento que mejor captura la naturaleza de un tipo de referencia CLR.  
  
 El `__gc` modificador en un controlador de seguimiento no es necesario y no se admite. El uso del propio objeto no cambia; sigue teniendo acceso a los miembros a través del operador de selección de miembro de puntero (`->`). Por ejemplo, este es el ejemplo de código anterior de extensiones administradas traducido a la nueva sintaxis:  
  
```  
public ref class Form1: public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container^ components;  
   Button^ button1;  
   DataGrid^ myDataGrid;  
   DataSet^ myDataSet;  
  
   void PrintValues( Array^ myArr ) {  
      System::Collections::IEnumerator^ myEnumerator =  
         myArr->GetEnumerator();  
  
      Array ^localArray;  
      myArr->Copy(myArr, localArray, myArr->Length);   }  
};  
```  
  
## <a name="dynamic-allocation-of-an-object-on-the-clr-heap"></a>Asignación dinámica de un objeto en el montón CLR  
 En extensiones administradas, la existencia de dos `new` expresiones para asignar entre el montón nativo y administrado era en gran medida transparente. En casi todos los casos, el compilador es capaz de utilizar el contexto para determinar si se debe asignar memoria del montón nativo o administrado. Por ejemplo,  
  
```  
Button *button1 = new Button; // OK: managed heap  
int *pi1 = new int;           // OK: native heap  
Int32 *pi2 = new Int32;       // OK: managed heap  
```  
  
 Si no desea que la asignación del montón contextuales, podría dirigir el compilador con cualquiera el `__gc` o `__nogc` (palabra clave). En la nueva sintaxis, la naturaleza independiente de las dos nuevas expresiones queda explícita con la introducción de la `gcnew` (palabra clave). Por ejemplo, las tres declaraciones anteriores ser como sigue en la nueva sintaxis:  
  
```  
Button^ button1 = gcnew Button;        // OK: managed heap  
int * pi1 = new int;                   // OK: native heap  
Int32^ pi2 = gcnew Int32; // OK: managed heap  
```  
  
 Esta es la inicialización de extensiones administradas de la `Form1` los miembros declarados en la sección anterior:  
  
```  
void InitializeComponent() {  
   components = new System::ComponentModel::Container();  
   button1 = new System::Windows::Forms::Button();  
   myDataGrid = new DataGrid();  
  
   button1->Click +=   
      new System::EventHandler(this, &Form1::button1_Click);  
}  
```  
  
 Aquí es la misma inicialización adaptada a la nueva sintaxis. Tenga en cuenta que el "Hat" no es necesario para el tipo de referencia cuando es el destino de un `gcnew` expresión.  
  
```  
void InitializeComponent() {  
   components = gcnew System::ComponentModel::Container;  
   button1 = gcnew System::Windows::Forms::Button;  
   myDataGrid = gcnew DataGrid;  
  
   button1->Click +=   
      gcnew System::EventHandler( this, &Form1::button1_Click );  
}  
```  
  
## <a name="a-tracking-reference-to-no-object"></a>Una referencia de seguimiento a ningún objeto  
 En la nueva sintaxis, `0` ya no representa una dirección nula, pero se trata como un entero, el mismo que `1`, `10`, o `100`. Un nuevo símbolo (token) especial representa un valor nulo para una referencia de seguimiento. Por ejemplo, en extensiones administradas, se inicializa un tipo de referencia para direccionar ningún objeto como sigue:  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 En la nueva sintaxis, cualquier inicialización o asignación de un valor de tipo a un `Object` hace que una conversión boxing implícita de ese tipo de valor. En la nueva sintaxis, ambos `obj` y `obj2` se inicializan para direccionar objetos Int32 que contiene los valores 0 y 1, respectivamente. Por ejemplo:  
  
```  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
```  
  
 Por lo tanto, con el fin de llevar a cabo la inicialización explícita, la asignación y la comparación de un controlador de seguimiento a null, utilice una nueva palabra clave `nullptr`.  La revisión correcta del ejemplo original tiene el siguiente aspecto:  
  
```  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to a Int32^  
Object ^ obj2 = 1;  
```  
  
 Esto complica un poco el traslado del código existente en la nueva sintaxis. Por ejemplo, considere la siguiente declaración de clase de valor:  
  
```  
__value struct Holder {  
   Holder( Continuation* c, Sexpr* v ) {  
      cont = c;  
      value = v;  
      args = 0;  
      env = 0;  
   }  
  
private:  
   Continuation* cont;  
   Sexpr * value;  
   Environment* env;  
   Sexpr * args __gc [];  
};  
```  
  
 En este caso, ambos `args` y `env` son tipos de referencia CLR. La inicialización de estos dos miembros a `0` en el constructor no puede permanecer sin cambios en la transición a la nueva sintaxis. En su lugar, debe cambiarse a `nullptr`:  
  
```  
value struct Holder {  
   Holder( Continuation^ c, Sexpr^ v )  
   {  
      cont = c;  
      value = v;  
      args = nullptr;  
      env = nullptr;  
   }  
  
private:  
   Continuation^ cont;  
   Sexpr^ value;  
   Environment^ env;  
   array<Sexpr^>^ args;  
};  
```  
  
 Del mismo modo, se comprueba con esos miembros comparándolos a `0` también debe cambiarse para comparar los miembros que se `nullptr`. Aquí se muestra la sintaxis de extensiones administradas:  
  
```  
Sexpr * Loop (Sexpr* input) {  
   value = 0;  
   Holder holder = Interpret(this, input, env);  
  
   while (holder.cont != 0) {  
      if (holder.env != 0) {  
         holder=Interpret(holder.cont,holder.value,holder.env);  
      }  
      else if (holder.args != 0) {  
         holder =   
         holder.value->closure()->  
         apply(holder.cont,holder.args);  
      }  
   }  
  
   return value;  
}  
```  
  
 Esta es la revisión, que reemplaza cada `0` instancia con un `nullptr`. La herramienta de traducción ayuda en esta transformación mediante la automatización de muchas si no todas las apariciones, incluido el uso de la `NULL` macro.  
  
```  
Sexpr ^ Loop (Sexpr^ input) {  
   value = nullptr;  
   Holder holder = Interpret(this, input, env);  
  
   while ( holder.cont != nullptr ) {  
      if ( holder.env != nullptr ) {  
         holder=Interpret(holder.cont,holder.value,holder.env);  
      }  
      else if (holder.args != nullptr ) {  
         holder =   
         holder.value->closure()->  
         apply(holder.cont,holder.args);  
      }  
   }  
  
   return value;  
}  
```  
  
 El `nullptr` se convierte en cualquier tipo de identificador de seguimiento o de puntero, pero no se promueve a un tipo entero. Por ejemplo, en el siguiente conjunto de inicializaciones, los `nullptr` sólo es válida como un valor inicial para las dos primeras.  
  
```  
// OK: we set obj and pstr to refer to no object  
Object^ obj = nullptr;  
char*   pstr = nullptr; // 0 would also work here  
  
// Error: no conversion of nullptr to 0  
int ival = nullptr;  
```  
  
 De forma similar, dado un conjunto sobrecargado de métodos como los siguientes:  
  
```  
void f( Object^ ); // (1)  
void f( char* );   // (2)  
void f( int );     // (3)  
```  
  
 Una invocación con `nullptr` literal, como la siguiente,  
  
```  
// Error: ambiguous: matches (1) and (2)  
f(  nullptr );  
```  
  
 es ambigua porque el `nullptr` coincide con un identificador de seguimiento y un puntero y no hay ninguna preferencia otorgado a un tipo frente a otra. (Esta situación requiere una conversión explícita para eliminar la ambigüedad).  
  
 Una invocación con `0` exactamente coincidencias instancia (3):  
  
```  
// OK: matches (3)  
f( 0 );  
```  
  
 Dado que `0` es de tipo entero. Estaban `f(int)` inequívocamente coincidiría con no está presente, la llamada `f(char*)` a través de una conversión estándar. Las reglas de coincidencia dar prioridad de una coincidencia exacta sobre una conversión estándar. En ausencia de una coincidencia exacta, una conversión estándar tiene prioridad sobre una conversión boxing implícita de un tipo de valor. Que es la razón por la que no hay ninguna ambigüedad.  
  
## <a name="see-also"></a>Vea también  
 [Tipos administrados (C++ / CL)](../dotnet/managed-types-cpp-cl.md)   
 [Clases y estructuras](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Identificador a un operador de objeto (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)