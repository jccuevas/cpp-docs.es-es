---
title: "C&#243;mo: Declarar controladores en tipos nativos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "gcroot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gcroot (palabra clave) [C++]"
  - "identificadores, declarar"
  - "tipos [C++], declarar identificadores"
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Declarar controladores en tipos nativos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No se puede declarar un controlador en un tipo nativo. vcclr.h proporciona la plantilla tipo\- segura `gcroot` de contenedor para hacer referencia a un objeto CLR del montón de C\+\+.  Esta plantilla permite incrustar un identificador virtual en un tipo nativo y tratarlo como si fuera el tipo subyacente.  En la mayoría de los casos, puede utilizar el objeto `gcroot` como el tipo incrustado sin ninguna conversión.  Sin embargo, con [for each, in](../dotnet/for-each-in.md), tiene que utilizar `static_cast` para recuperar la referencia administrada subyacente.  
  
 La plantilla `gcroot` se implementa mediante los servicios de la clase de valor System::Runtime::InteropServices::GCHandle, que proporciona "controladores" en el montón de recolección de elementos no utilizados.  Observe que los propios controladores no se recolectan como elementos no utilizados y se liberan cuando ya no los usa el destructor en la clase `gcroot` \(este destructor no se puede llamar manualmente\).  Si crea instancias de un objeto `gcroot` en el montón nativo, deberá llamar a delete en ese recurso.  
  
 El tiempo de ejecución mantendrá una asociación entre el identificador y el objeto CLR, a los que hace referencia.  Si el objeto CLR se desplaza con la pila de recolección de elementos no utilizados, el identificador devolverá la nueva dirección del objeto.  No se debe anclar una variable antes de asignarla a una plantilla `gcroot`.  
  
## Ejemplo  
 En este ejemplo se muestra cómo crear un objeto `gcroot` en la pila nativa.  
  
```  
// mcpp_gcroot.cpp  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
class CppClass {  
public:  
   gcroot<String^> str;   // can use str as if it were String^  
   CppClass() {}  
};  
  
int main() {  
   CppClass c;  
   c.str = gcnew String("hello");  
   Console::WriteLine( c.str );   // no cast required  
}  
```  
  
  **hello**   
## Ejemplo  
 En este ejemplo se muestra cómo crear un objeto `gcroot` en el montón nativo.  
  
```  
// mcpp_gcroot_2.cpp  
// compile with: /clr  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
struct CppClass {  
   gcroot<String ^> * str;  
   CppClass() : str(new gcroot<String ^>) {}  
  
   ~CppClass() { delete str; }  
  
};  
  
int main() {  
   CppClass c;  
   *c.str = gcnew String("hello");  
   Console::WriteLine( *c.str );  
}  
```  
  
  **hello**   
## Ejemplo  
 En este ejemplo se muestra cómo usar `gcroot` para mantener referencias a tipos de valor \(no tipos de referencia\) en un tipo nativo mediante `gcroot` en el tipo al que se le ha aplicado una conversión boxing.  
  
```  
// mcpp_gcroot_3.cpp  
// compile with: /clr  
#include < vcclr.h >  
using namespace System;  
  
public value struct V {  
   String^ str;  
};  
  
class Native {  
public:  
   gcroot< V^ > v_handle;  
};  
  
int main() {  
   Native native;  
   V v;  
   native.v_handle = v;  
   native.v_handle->str = "Hello";  
   Console::WriteLine("String in V: {0}", native.v_handle->str);  
}  
```  
  
  **Cadena en V: Hello**   
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)