---
title: Referencias parciales y ruptura de ciclos (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a98dc4dd43b40f378a91713770c4c5500c790d0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Referencias parciales y ruptura de ciclos (C++/CX)
En cualquier sistema de tipos basado en el recuento de referencias, las referencias a tipos pueden formar *ciclos*(es decir, un objeto hace referencia a un segundo objeto, el segundo objeto hace referencia a un tercer objeto, etc.), hasta que un objeto final vuelve a hacer referencia al primer objeto. En un ciclo, los objetos no se pueden eliminar correctamente cuando el recuento de referencias de un objeto se convierte en cero. Para resolver este problema, C++ / CX proporciona el [WeakReference (clase)](../cppcx/platform-weakreference-class.md) clase. Un objeto `WeakReference` admite el método [Resolve](../cppcx/platform-weakreference-class.md#resolve) , que devuelve null si el objeto ya no existe o produce una excepción [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) si el objeto está activo pero no es de tipo `T`.  
  
 Un escenario en el que `WeakReference` debe utilizarse es cuando el puntero `this` se captura en una expresión lambda que se utiliza para definir un controlador de eventos. Te recomendamos que utilices métodos con nombre cuando definas controladores de eventos, pero si deseas utilizar una expresión lambda para tu controlador de eventos (o si tienes que interrumpir un ciclo de recuento de referencias en alguna otra situación), utiliza `WeakReference`. Por ejemplo:  
  
```  
  
using namespace Platform::Details;  
using namespace Windows::UI::Xaml;  
using namespace Windows::UI::Xaml::Input;  
using namespace Windows::UI::Xaml::Controls;  
  
Class1::Class1()  
{  
    // Class1 has a reference to m_Page  
    m_Page = ref new Page();  
  
    // m_Page will have a reference to this Class1  
    // so create a weak reference to this  
    WeakReference wr(this);  
    m_Page->DoubleTapped += ref new DoubleTappedEventHandler(   
        [wr](Object^ sender, DoubleTappedRoutedEventArgs^ args)  
    {  
       // Use the weak reference to get the object  
       Class1^ c = wr.Resolve<Class1>();  
       if (c != nullptr)  
       {  
           c->m_eventFired = true;  
       }  
       else  
       {  
           // Inform the event that this handler should be removed  
           // from the subscriber list  
           throw ref new DisconnectedException();  
       }  
    });   
}  
  
}  
```  
  
 Cuando un controlador de eventos produce una excepción `DisconnectedException`, hace que el evento quite el controlador de la lista de suscriptores.  
  
## <a name="see-also"></a>Vea también  


