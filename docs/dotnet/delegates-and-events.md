---
title: Delegados y eventos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __event keyword [C++]
- delegate keyword [C++]
- delegates [C++], upgrading from Managed Extensions for C++
- __delegate keyword
- events [C++], upgrading from Managed Extensions for C++
- event keyword [C++]
ms.assetid: 3505c626-7e5f-4492-a947-0e2248f7b84a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 26b67cdce8d52cba7d02f182f0582e20d0303c33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373313"
---
# <a name="delegates-and-events"></a>Delegados y eventos

La manera de declarar delegados y eventos ha cambiado de extensiones administradas para C++ a Visual C++.

Ya no se necesita el carácter de subrayado doble, como se muestra en el ejemplo siguiente. Este es un código de ejemplo en extensiones administradas:

```
__delegate void ClickEventHandler(int, double);
__delegate void DblClickEventHandler(String*);

__gc class EventSource {
   __event ClickEventHandler* OnClick;
   __event DblClickEventHandler* OnDblClick;
};
```

El mismo código en la nueva sintaxis tiene el aspecto siguiente:

```
delegate void ClickEventHandler( int, double );
delegate void DblClickEventHandler( String^ );

ref class EventSource {
   event ClickEventHandler^ OnClick;
   event DblClickEventHandler^ OnDblClick;
};
```

Eventos (y delegados) son tipos de referencia, que es claro en la nueva sintaxis debido al uso de hat (`^`).  Los eventos admiten una sintaxis de declaración explícita y la forma trivial que se muestra en el código anterior. En el formulario explícito, el usuario especifica la `add`, `raise`, y `remove` métodos asociados con el evento. (Solo la `add` y `remove` métodos son necesarios; el `raise` método es opcional.)

En extensiones administradas, si proporciona estos métodos, no se proporciona también una declaración de evento explícito, pero debe decidir un nombre para el evento que no está presente. Cada método se especifica en el formulario `add_EventName`, `raise_EventName`, y `remove_EventName`, como en el ejemplo siguiente, tomado de la especificación de extensiones administradas:

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

La nueva sintaxis simplifica la declaración, como se muestra en la siguiente traducción. Un evento especifica los dos o tres métodos entre un par de llaves y se colocan inmediatamente después de la declaración del evento y su tipo de delegado asociado, como se muestra aquí:

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

## <a name="see-also"></a>Vea también

[Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[delegate (Extensiones de componentes de C++)](../windows/delegate-cpp-component-extensions.md)<br/>
[event](../windows/event-cpp-component-extensions.md)