---
title: Referencias parciales y ruptura de ciclos (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 1acb6402-05f0-4951-af94-0e9dab41c53e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a262b608bef9ba2e1393337660f58b7f14fb05c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108972"
---
# <a name="weak-references-and-breaking-cycles-ccx"></a>Referencias parciales y ruptura de ciclos (C++/CX)

En cualquier sistema de tipos basado en el recuento de referencias, las referencias a tipos pueden formar *ciclos*(es decir, un objeto hace referencia a un segundo objeto, el segundo objeto hace referencia a un tercer objeto, etc.), hasta que un objeto final vuelve a hacer referencia al primer objeto. En un ciclo, los objetos no se pueden eliminar correctamente cuando el recuento de referencias de un objeto se convierte en cero. Para ayudarle a resolver este problema, C++ / c++ / CX proporciona el [WeakReference (clase)](../cppcx/platform-weakreference-class.md) clase. Un objeto `WeakReference` admite el método [Resolve](../cppcx/platform-weakreference-class.md#resolve) , que devuelve null si el objeto ya no existe o produce una excepción [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) si el objeto está activo pero no es de tipo `T`.

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

