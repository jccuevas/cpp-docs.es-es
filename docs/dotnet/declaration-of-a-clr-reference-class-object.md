---
title: "Declaraci&#243;n de un objeto de una clase de referencia de CLR | Microsoft Docs"
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
  - "tipos de referencia, CLR"
  - "tipos [C++], tipos de referencia"
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Declaraci&#243;n de un objeto de una clase de referencia de CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sintaxis para declarar y crear instancias de un objeto de un tipo de clase de referencia ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En Extensiones administradas, un objeto de tipo de clase de referencia se declaraba mediante la sintaxis de puntero de ISO\-C\+\+, con el uso opcional de la palabra clave `__gc` a la izquierda del asterisco \(`*`\).  Por ejemplo, a continuación se muestra una serie de declaraciones de objeto de tipo de clase de referencia bajo la sintaxis de Extensiones administradas:  
  
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
  
 En la nueva sintaxis, un objeto de tipo de clase de referencia se declara mediante un nuevo símbolo \(token\) declarativo \(`^`\) denominado formalmente *controlador de seguimiento* y, más informalmente, *sombrero*. El término seguimiento significa que un tipo de referencia se encuentra dentro del montón CLR y, por lo tanto, puede trasladar ubicaciones de forma transparente durante la compactación del montón de recolección de elementos no utilizados.  Un controlador de seguimiento se actualiza de forma transparente durante el tiempo de ejecución.  Dos conceptos similares son la *referencia del seguimiento* \(`%`\) y el *puntero interior* \(`interior_ptr<>`\), que se explican en [Semántica de los tipos de valor](../dotnet/value-type-semantics.md).  
  
 Las razones principales para abandonar la sintaxis declarativa y volver a utilizar la sintaxis de puntero de ISO\-C\+\+ son las siguientes:  
  
-   El uso de la sintaxis de puntero no permitía aplicar los operadores de sobrecarga directamente a un objeto de referencia.  En lugar de ello, se tenía que llamar al operador utilizando su nombre interno como, por ejemplo, `rV1->op_Addition(rV2)` en lugar de `rV1+rV2`, que resulta mucho más intuitivo.  
  
-   Hay una serie de operaciones de puntero, como la conversión y la aritmética con punteros, que no están permitidas para los objetos almacenados en una pila de recolección de elementos no utilizados.  La noción de un controlador de seguimiento define mejor la naturaleza de un tipo de referencia CLR.  
  
 El modificador `__gc` en un controlador de seguimiento es innecesario y no se admite.  El uso del propio objeto no ha cambiado; todavía tiene acceso a los miembros a través del operador de selección de miembro de puntero \(`->`\).  Por ejemplo, a continuación se muestra el ejemplo de código anterior de Extensiones administradas traducido a la nueva sintaxis:  
  
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
  
## Asignación dinámica de un objeto en el montón CLR  
 En Extensiones administradas, la existencia de dos expresiones `new` que se debían asignar entre el montón nativo y el administrado era bastante transparente.  En casi todas instancias, el compilador puede utilizar el contexto para determinar si hay que asignar memoria del montón nativo o del administrado.  Por ejemplo,  
  
```  
Button *button1 = new Button; // OK: managed heap  
int *pi1 = new int;           // OK: native heap  
Int32 *pi2 = new Int32;       // OK: managed heap  
```  
  
 Si no desea que se lleve a cabo una asignación contextual del montón, puede dirigir el compilador con la palabra clave `__gc` o `__nogc`.  En la nueva sintaxis, la naturaleza independiente de las dos nuevas expresiones queda explícita con la inclusión de la palabra clave `gcnew`.  Por ejemplo, las tres declaraciones anteriores tienen el siguiente aspecto en la nueva sintaxis:  
  
```  
Button^ button1 = gcnew Button;        // OK: managed heap  
int * pi1 = new int;                   // OK: native heap  
Int32^ pi2 = gcnew Int32; // OK: managed heap  
```  
  
 A continuación se incluye la inicialización de Extensiones administradas de los miembros `Form1` declarados en la sección anterior:  
  
```  
void InitializeComponent() {  
   components = new System::ComponentModel::Container();  
   button1 = new System::Windows::Forms::Button();  
   myDataGrid = new DataGrid();  
  
   button1->Click +=   
      new System::EventHandler(this, &Form1::button1_Click);  
}  
```  
  
 Y esta es la misma inicialización adaptada a la nueva sintaxis:  Observe que el sombrero no es necesario para el tipo de referencia cuando es el destino de una expresión `gcnew`.  
  
```  
void InitializeComponent() {  
   components = gcnew System::ComponentModel::Container;  
   button1 = gcnew System::Windows::Forms::Button;  
   myDataGrid = gcnew DataGrid;  
  
   button1->Click +=   
      gcnew System::EventHandler( this, &Form1::button1_Click );  
}  
```  
  
## Una referencia de seguimiento a ningún objeto  
 En la nueva sintaxis, `0` ya no representa una dirección nula, simplemente se trata como un número entero, lo mismo que `1`, `10` o `100`.  Un nuevo símbolo \(token\) especial representa un valor nulo para una referencia de seguimiento.  Por ejemplo, en Extensiones administradas, se inicializa un tipo de referencia para no direccionar ningún objeto como sigue:  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 En la nueva sintaxis, cualquier inicialización o asignación de un tipo de valor a `Object` produce una conversión boxing implícita de ese tipo de valor.  En la nueva sintaxis, `obj` y `obj2` se inicializan para direccionar objetos Int32 convertidos que tienen los valores 0 y 1, respectivamente.  Por ejemplo:  
  
```  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
```  
  
 Por lo tanto, para realizar la inicialización, asignación y comparación explícitas de un controlador de seguimiento a null, utilice una nueva palabra clave: `nullptr`.  La revisión correcta del ejemplo original será la siguiente:  
  
```  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to a Int32^  
Object ^ obj2 = 1;  
```  
  
 Esto complica un poco el traslado del código existente a la nueva sintaxis.  Por ejemplo, considere la siguiente declaración de clase de valor:  
  
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
  
 Aquí, `args` y `env` son los tipos de referencia CLR.  La inicialización de estos dos miembros a `0` en el constructor no puede permanecer intacta en la transición a la nueva sintaxis.  Más bien, se debe cambiar a `nullptr`:  
  
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
  
 De igual forma, las comprobaciones de esos miembros comparados con `0` también se deben cambiar para comparar los miembros con `nullptr`.  A continuación se muestra la sintaxis de Extensiones administradas:  
  
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
  
 A continuación se muestra la revisión, que reemplaza cada instancia `0` por `nullptr`.  La herramienta de traducción sirve de ayuda en esta transformación, ya que automatiza muchos de los casos, si no todos, incluso el uso de la macro `NULL`.  
  
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
  
 `nullptr` se convierte en cualquier tipo de puntero o controlador de seguimiento pero no se promueve a un tipo entero.  Por ejemplo, en el siguiente conjunto de inicializaciones, `nullptr` sólo es válido como un valor inicial para las dos primeras.  
  
```  
// OK: we set obj and pstr to refer to no object  
Object^ obj = nullptr;  
char*   pstr = nullptr; // 0 would also work here  
  
// Error: no conversion of nullptr to 0 …  
int ival = nullptr;  
```  
  
 De igual forma, si existe un conjunto de métodos sobrecargado como el siguiente:  
  
```  
void f( Object^ ); // (1)  
void f( char* );   // (2)  
void f( int );     // (3)  
```  
  
 Una invocación con el literal `nullptr`, como la siguiente,  
  
```  
// Error: ambiguous: matches (1) and (2)  
f(  nullptr );  
```  
  
 es ambigua porque `nullptr` coincide con un puntero y un controlador de seguimiento y no se concede ninguna preferencia a ningún tipo sobre otro. \(Esta situación requiere una conversión de tipos explícita para eliminar la ambigüedad.\)  
  
 Una invocación con `0` coincide exactamente con la instancia \(3\):  
  
```  
// OK: matches (3)  
f( 0 );  
```  
  
 dado que `0` es de tipo entero.  Si `f(int)` no estuviera presente, la llamada coincidiría inequívocamente con `f(char*)` a través de una conversión estándar.  Las reglas de coincidencia dan prioridad a una coincidencia exacta sobre una conversión estándar.  En ausencia de una coincidencia exacta, una conversión estándar tiene prioridad sobre una conversión boxing implícita de un tipo de valor.  Ésta es la razón por la que no hay ninguna ambigüedad.  
  
## Vea también  
 [Tipos administrados \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Identificador a un operador de objeto \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)