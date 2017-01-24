---
title: "Delegados y eventos | Microsoft Docs"
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
  - "__delegate (palabra clave)"
  - "__event (palabra clave) [C++]"
  - "delegate (palabra clave) [C++]"
  - "delegados [C++], actualizar desde Extensiones administradas para C++"
  - "event (palabra clave) [C++]"
  - "eventos [C++], actualizar desde Extensiones administradas para C++"
ms.assetid: 3505c626-7e5f-4492-a947-0e2248f7b84a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Delegados y eventos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera de declarar delegados y eventos ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 Ya no es necesario el subrayado doble, tal y como se muestra en el siguiente ejemplo.  A continuación, se muestra un código de ejemplo en Extensiones administradas:  
  
```  
__delegate void ClickEventHandler(int, double);  
__delegate void DblClickEventHandler(String*);  
  
__gc class EventSource {  
   __event ClickEventHandler* OnClick;    
   __event DblClickEventHandler* OnDblClick;    
};  
```  
  
 Este mismo código presenta el siguiente aspecto en la nueva sintaxis:  
  
```  
delegate void ClickEventHandler( int, double );  
delegate void DblClickEventHandler( String^ );  
  
ref class EventSource {  
   event ClickEventHandler^ OnClick;   
   event DblClickEventHandler^ OnDblClick;   
};  
```  
  
 Los eventos \(y delegados\) son tipos de referencia, lo que queda más claro en la nueva sintaxis debido al uso del acento circunflejo \(`^`\).  Los eventos admiten una sintaxis de declaración explícita, así como el formulario trivial mostrado en el código anterior.  En el formulario explícito, el usuario especifica los métodos `add`, `raise` y `remove` asociados al evento. \(Se requieren sólo métodos `add` y `remove`; el método `raise` es opcional.\)  
  
 Si proporciona estos métodos en Extensiones administradas, no debe proporcionar una declaración de eventos explícita, pero debe decidir un nombre para el evento que no esté presente.  Cada método se especifica en el formulario `add_EventName`, `raise_EventName` y `remove_EventName`, tal y como se muestra en el siguiente ejemplo tomado de la especificación de Extensiones administradas:  
  
```  
// explicit implementations of add, remove, raise  
public __delegate void f(int);  
public __gc struct E {  
   f* _E;  
public:  
   E() { _E = 0; }  
  
   __event void add_E1(f* d) { _E += d; }  
  
   static void Go() {  
      E* pE = new E;  
      pE->E1 += new f(pE, &E::handler);  
      pE->E1(17);   
      pE->E1 -= new f(pE, &E::handler);  
      pE->E1(17);   
   }  
  
private:  
   __event void raise_E1(int i) {  
      if (_E)  
         _E(i);  
   }  
  
protected:  
   __event void remove_E1(f* d) {  
      _E -= d;  
   }  
};  
```  
  
 La nueva sintaxis simplifica la declaración, tal y como demuestra la siguiente traducción.  Un evento especifica los dos o tres métodos incluidos entre un par de llaves y colocados inmediatamente después de la declaración del evento y su tipo de delegado asociado, tal y como se muestra a continuación:  
  
```  
public delegate void f( int );  
public ref struct E {  
private:  
   f^ _E; // delegates are also reference types  
  
public:  
   E() {  // note the replacement of 0 with nullptr!  
      _E = nullptr;   
   }  
  
   // the new aggregate syntax of an explicit event declaration  
   event f^ E1 {  
   public:  
      void add( f^ d ) {  
         _E += d;  
      }  
  
   protected:  
      void remove( f^ d ) {  
         _E -= d;  
      }  
  
   private:  
      void raise( int i ) {  
         if ( _E )  
            _E( i );  
      }  
   }  
  
   static void Go() {  
      E^ pE = gcnew E;  
      pE->E1 += gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
      pE->E1 -= gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
   }  
};  
```  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [delegado](../windows/delegate-cpp-component-extensions.md)   
 [event](../windows/event-cpp-component-extensions.md)