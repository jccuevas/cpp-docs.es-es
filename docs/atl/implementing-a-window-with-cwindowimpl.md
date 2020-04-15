---
title: Implementación de una ventana con CWindowImpl
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: e5fdbf15ddd7edc69f0667a9b7e08c7c5e531a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319451"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>Implementación de una ventana con CWindowImpl

Para implementar una ventana, `CWindowImpl`derive una clase de . En la clase derivada, declare un mapa de mensajes y las funciones del controlador de mensajes. Ahora puede utilizar su clase de tres maneras diferentes:

- [Crear una ventana basada en una nueva clase de Windows](#_atl_creating_a_window_based_on_a_new_windows_class)

- [Superclase una clase de Windows existente](#_atl_superclassing_an_existing_windows_class)

- [Subclase de una ventana existente](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a>Creación de una ventana basada en una nueva clase de Windows

`CWindowImpl`contiene la macro [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) para declarar información de clase de Windows. Esta macro implementa `GetWndClassInfo` la función, que usa [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) para definir la información de una nueva clase de Windows. Cuando `CWindowImpl::Create` se llama, esta clase de Windows se registra y se crea una nueva ventana.

> [!NOTE]
> `CWindowImpl`pasa NULL a `DECLARE_WND_CLASS` la macro, lo que significa que ATL generará un nombre de clase de Windows. Para especificar su propio nombre, pase `CWindowImpl`una cadena a DECLARE_WND_CLASS en la clase derivada.

## <a name="example"></a>Ejemplo

A continuación se muestra un ejemplo de una clase que implementa una ventana basada en una nueva clase de Windows:

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

Para crear una ventana, `CMyWindow` cree una `Create` instancia de y, a continuación, llame al método.

> [!NOTE]
> Para invalidar la información de `GetWndClassInfo` clase predeterminada de Windows, `CWndClassInfo` implemente el método en la clase derivada estableciendo los miembros en los valores adecuados.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a>Superclase de una clase de Windows existente

La macro [DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) le permite crear una ventana que superclase sin una clase de Windows existente. Especifique esta macro `CWindowImpl`en la clase derivada. Al igual que cualquier otra ventana ATL, los mensajes se controlan mediante un mapa de mensajes.

Cuando utilice DECLARE_WND_SUPERCLASS, se registrará una nueva clase de Windows. Esta nueva clase será la misma que la clase existente que `CWindowImpl::WindowProc` especifique, pero reemplazará el procedimiento de ventana con (o con la función que invalida este método).

## <a name="example"></a>Ejemplo

A continuación se muestra un ejemplo de una clase que superclase sin la clase Edit estándar:

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Para crear la ventana Edit superclase, `CMyEdit` cree una `Create` instancia de y, a continuación, llame al método.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a>Subclase de una ventana existente

Para subclase una ventana existente, `CWindowImpl` derive una clase y declare un mapa de mensajes, como en los dos casos anteriores. Tenga en cuenta, sin embargo, que no se especifica ninguna información de clase de Windows, ya que se subclase una ventana ya existente.

En lugar `Create`de `SubclassWindow` llamar a , llame y pásele el identificador a la ventana existente que desea subclase. Una vez que la ventana está `CWindowImpl::WindowProc` subclase, usará (o la función que invalida este método) para dirigir los mensajes al mapa de mensajes. Para separar una ventana subclase del `UnsubclassWindow`objeto, llame a . A continuación, se restaurará el procedimiento de ventana original de la ventana.

## <a name="see-also"></a>Consulte también

[Implementación de una ventana](../atl/implementing-a-window.md)
