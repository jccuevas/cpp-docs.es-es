---
title: "Sem&#225;ntica de pila de C++ para los tipos de referencia | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de referencia, semántica de pila de C++ para"
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Sem&#225;ntica de pila de C++ para los tipos de referencia
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Antes de Visual C\+\+ 2005, una instancia de un tipo de referencia se podría crear solo mediante el operador de `new` , que creó el objeto en el montón de recolección.  Sin embargo, ahora puede crear una instancia de un tipo de referencia utilizando la misma sintaxis que utilizaría para crear una instancia de un tipo nativo en la pila.  Por tanto, no necesita utilizar [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) para crear un objeto de un tipo de referencia.  Y cuando el objeto salga del ámbito, el compilador de llama al destructor del objeto.  
  
## Comentarios  
 Cuando se crea una instancia de un tipo de referencia mediante la semántica de la pila, el compilador crea internamente la instancia en la pila de recolección \(mediante `gcnew`\).  
  
 Cuando la firma o tipo de valor devuelto de una función incluye una instancia de un tipo de referencia de por\- valor, la función se marcará en metadatos como requiriendo especial \(con el modreq\).  El este tratamiento especial proporcionado actualmente sólo por los clientes de Visual C\+\+; otros lenguajes no admiten actualmente consumir funciones o datos que utilizan los tipos de referencia creados con la semántica de la pila.  
  
 Una razón para utilizar `gcnew` \(creación dinámica\) en lugar de la semántica de la pila sería si el tipo no tiene ningún destructor.  Además, mediante los tipos de referencia creados con la semántica de la pila en firmas de la función no es posible si desea que las funciones que se consumirán por otros lenguajes distintos de Visual C\+\+.  
  
 El compilador no generará un constructor de copias para un tipo de referencia.  Por consiguiente, si se define una función que utilice una referencia de por\- valor escribir en la firma, debe definir un constructor de copias para el tipo de referencia.  Un constructor de copias para un tipo de referencia tiene una firma de la forma siguiente: `R(R%){}`.  
  
 El compilador no generará un operador de asignación predeterminado para un tipo de referencia.  Un operador de asignación permite crear un objeto mediante la semántica de la pila y inicializarlo ésta con un objeto existente creado mediante la semántica de la pila.  Un operador de asignación para un tipo de referencia tiene una firma de la forma siguiente: `void operator=( R% ){}`.  
  
 Si los recursos críticos y el del destructor del tipo usan semántica de pila para los tipos de referencia, no es necesario llamar explícitamente a un destructor \(o llamar a `delete`\).  Para obtener más información sobre los destructores en los tipos de referencia, vea [Destructores y finalizadores de Visual C\+\+](../misc/destructors-and-finalizers-in-visual-cpp.md).  
  
 Un operador de asignación compilador\- generado seguirá las reglas estándar habituales de C\+\+ con las siguientes adiciones:  
  
-   Cualquier miembro de datos no estático cuyo tipo es un identificador a un tipo de referencia se bajo copiado \(tratará como un miembro de datos no estático cuyo tipo es un puntero\).  
  
-   Cualquier miembro de datos no estático cuyo tipo es un tipo de valor se bajo copiado.  
  
-   Cualquier miembro de datos no estático cuyo tipo es una instancia de un tipo de referencia invoque una llamada al constructor de copias de tipo de referencia.  
  
 El compilador también proporciona un operador unario de `%` para convertir una instancia de un tipo de referencia creado mediante la semántica de la pila a su tipo subyacente del identificador.  
  
 Los tipos de referencia siguientes no están disponibles para su uso con la semántica del montón:  
  
-   [delegado](../windows/delegate-cpp-component-extensions.md)  
  
-   [Matrices](../windows/arrays-cpp-component-extensions.md)  
  
-   <xref:System.String>  
  
## Ejemplo  
  
### Descripción  
 El ejemplo de código siguiente muestra cómo declarar instancias de tipos de referencia con la semántica de la pila, cómo funciona el constructor del operador de asignación y copiar, y cómo inicializar una referencia de seguimiento con el tipo de referencia creado mediante la semántica de la pila.  
  
### Código  
  
```  
// stack_semantics_for_reference_types.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
   R(){}  
  
   // assignment operator  
   void operator=(R% r) {  
      i = r.i;  
   }  
  
   // copy constructor  
   R(R% r) : i(r.i) {}  
};  
  
void Test(R r) {}   // requires copy constructor  
  
int main() {  
   R r1;  
   r1.i = 98;  
  
   R r2(r1);   // requires copy constructor  
   System::Console::WriteLine(r1.i);  
   System::Console::WriteLine(r2.i);  
  
   // use % unary operator to convert instance using stack semantics  
   // to its underlying handle  
   R ^ r3 = %r1;  
   System::Console::WriteLine(r3->i);  
  
   Test(r1);  
  
   R r4;  
   R r5;  
   r5.i = 13;  
   r4 = r5;   // requires a user-defined assignment operator  
   System::Console::WriteLine(r4.i);  
  
   // initialize tracking reference  
   R % r6 = r4;  
   System::Console::WriteLine(r6.i);  
}  
```  
  
### Resultados  
  
```  
98  
98  
98  
13  
13  
```  
  
## Vea también  
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)