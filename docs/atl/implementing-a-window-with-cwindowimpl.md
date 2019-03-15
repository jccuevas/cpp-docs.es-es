---
title: Implementar una ventana con CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: 265c3145d8ceacae540286f72939dc046e7c8b35
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818081"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementar una ventana con CWindowImpl

Para implementar una ventana, derive una clase de `CWindowImpl`. En la clase derivada, declare un mapa de mensajes y las funciones de controlador de mensaje. Ahora puede usar la clase de tres maneras diferentes:

- [Crear una ventana basada en una nueva clase de Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Superclase de una clase existente de Windows](#_atl_superclassing_an_existing_windows_class)

- [Subclase de una ventana existente](#_atl_subclassing_an_existing_window)

##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> Creación de una ventana basada en una nueva clase de Windows

`CWindowImpl` contiene el [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) macro para declarar la información de la clase de Windows. Esta macro implementa la `GetWndClassInfo` función, que usa [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) para definir la información de una nueva clase de Windows. Cuando `CWindowImpl::Create` se llama, este Windows clase se registra y se crea una nueva ventana.

> [!NOTE]
>  `CWindowImpl` pasa NULL para el `DECLARE_WND_CLASS` macro, lo que significa que ATL generará un nombre de clase de Windows. Para especificar su propio nombre, pase una cadena a DECLARE_WND_CLASS en su `CWindowImpl`-clase derivada.

## <a name="example"></a>Ejemplo

Este es un ejemplo de una clase que implementa una ventana basada en una nueva clase de Windows:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Para crear una ventana, cree una instancia de `CMyWindow` y, a continuación, llame a la `Create` método.

> [!NOTE]
>  Para invalidar la información de clase de Windows de forma predeterminada, implemente el `GetWndClassInfo` método en su clase derivada estableciendo el `CWndClassInfo` miembros en los valores adecuados.

##  <a name="_atl_superclassing_an_existing_windows_class"></a> Crear superclases de una clase existente de Windows

El [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) macro le permite crear una ventana que convierte en superclase un Windows existente clase. Especifique esta macro en su `CWindowImpl`-clase derivada. Al igual que cualquier otra ventana ATL, los mensajes se controlan mediante un mapa de mensajes.

Cuando usas DECLARE_WND_SUPERCLASS, se registrará una nueva clase de Windows. Esta nueva clase será igual que la clase existente que se especifica, pero reemplazará el procedimiento de ventana con `CWindowImpl::WindowProc` (o con la función que reemplaza este método).

## <a name="example"></a>Ejemplo

Siguiente es un ejemplo de una clase de la edición estándar superclase clase:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Para crear la ventana Edición, cree una instancia de `CMyEdit` y, a continuación, llame a la `Create` método.

##  <a name="_atl_subclassing_an_existing_window"></a> Creación de subclases de una ventana existente

Para subclasificar una ventana existente, derive una clase de `CWindowImpl` y declare un mapa de mensajes, como se muestra en los dos casos anteriores. Sin embargo, tenga en cuenta que no se especifica ninguna información de clase de Windows, puesto que se creará una subclase una ventana ya existente.

En lugar de llamar `Create`, llame a `SubclassWindow` y pasar el identificador a la ventana existente que desea crear una subclase. Una vez que la ventana es una subclase, usará `CWindowImpl::WindowProc` (o la función que reemplaza este método) para dirigir los mensajes para el mapa de mensajes. Para desasociar una ventana con subclases de su objeto, llame a `UnsubclassWindow`. A continuación, se restaurará el procedimiento de ventana original de la ventana.

## <a name="see-also"></a>Vea también

[Implementar una ventana](../atl/implementing-a-window.md)
