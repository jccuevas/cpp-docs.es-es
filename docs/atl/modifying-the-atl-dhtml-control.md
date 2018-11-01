---
title: Modificar el Control DHTML ATL
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
ms.openlocfilehash: 2a16ad50911185c27906eee27902cee9971932c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493683"
---
# <a name="modifying-the-atl-dhtml-control"></a>Modificar el Control DHTML ATL

El Asistente para controles ATL proporciona código de inicio para que pueda compilar y ejecutar el control, por lo que puede ver cómo se escriben los métodos en los archivos de proyecto y cómo DHTML llama al código de C++ del control mediante los métodos de envío. Puede agregar cualquier método de envío a la interfaz. A continuación, puede llamar a los métodos en el recurso de HTML.

## <a name="to-modify-the-atl-dhtml-control"></a>Para modificar el control DHTML ATL

1. En **vista de clases**, expanda el proyecto de control.

   Tenga en cuenta que la interfaz que termina en "UI" tiene un método, `OnClick`. La interfaz que no terminan en "Interfaz de usuario" no tiene ningún método.

1. Agregue un método llamado `MethodInvoked` a la interfaz que no termina en "Interfaz de usuario".

   Este método se agregarán a la interfaz que se usa en el contenedor del control de interacción de contenedor, no a la interfaz utilizada por DHTML para interactuar con el control. Solo el contenedor puede invocar este método.

1. Busque el método auxiliar en el archivo .cpp y agregue código para mostrar un cuadro de mensaje, por ejemplo:

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

1. Agregue otro método denominado `HelloHTML`, pero esta vez, agréguelo a la interfaz que termina en "Interfaz de usuario". Busque la salida se procesó con stub `HelloHTML` método en el cpp archivo y agregue código para mostrar un cuadro de mensaje, por ejemplo:

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

1. Agregue un tercer método `GoToURL`, a la interfaz que no termina en "Interfaz de usuario". Implemente este método mediante una llamada a [IWebBrowser2:: Navigate](https://msdn.microsoft.com/library/aa752133.aspx), como sigue:

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   Puede usar el `IWebBrowser2` métodos porque ATL proporciona un puntero a la interfaz en el archivo. h.

A continuación, modifique el recurso HTML para invocar los métodos que ha creado. Agregará tres botones para invocar estos métodos.

## <a name="to-modify-the-html-resource"></a>Para modificar el recurso HTML

1. En **el Explorador de soluciones**, haga doble clic en el archivo .htm para mostrar el recurso HTML.

   Examine el código HTML, especialmente las llamadas a los métodos de envío externos de Windows. El código HTML llama el proyecto `OnClick` método y los parámetros indican el cuerpo del control (`theBody`) y el color que se asigne ("`red`"). El texto que sigue a la llamada al método es la etiqueta que aparece en el botón.

1. Agregue otro `OnClick` método, solo cambie el color. Por ejemplo:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   Este método creará un botón, **actualizar**, que el usuario puede hacer clic para devolver el control al fondo blanco, original.

1. Agregue la llamada a la `HelloHTML` método creado. Por ejemplo:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>
    ```

   Este método creará un botón, **HelloHTML**, que el usuario puede hacer clic para mostrar el `HelloHTML` cuadro de mensaje.

Ahora puede compilar y [probar el control DHTML modificado](../atl/testing-the-modified-atl-dhtml-control.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con controles DHTML](../atl/atl-support-for-dhtml-controls.md)
