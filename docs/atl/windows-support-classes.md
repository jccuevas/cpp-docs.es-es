---
title: Clases de soporte técnico de Windows (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
ms.openlocfilehash: 5880fd970d885da84edd94f9f2c7a47ec326ebe1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814181"
---
# <a name="windows-support-classes"></a>Clases de soporte técnico de Windows

Las clases siguientes proporcionan compatibilidad para windows:

- [_U_MENUorID](../atl/reference/u-menuorid-class.md) proporciona contenedores para `CreateWindow` y `CreateWindowEx`.

- [CWindow](../atl/reference/cwindow-class.md) contiene métodos para manipular una ventana. `CWindow` es la clase base de `CWindowImpl`, `CDialogImpl` y `CContainedWindow`.

- [CWindowImpl](../atl/reference/cwindowimpl-class.md) implementa una ventana basada en una nueva clase de ventana. También permite a la subclase o superclase la ventana.

- [CDialogImpl](../atl/reference/cdialogimpl-class.md) implementa un cuadro de diálogo.

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) implementa un cuadro de diálogo (modal o no modal) que hospeda los controles ActiveX.

- [CSimpleDialog](../atl/reference/csimpledialog-class.md) implementa un cuadro de diálogo (modal o no modal) con la funcionalidad básica.

- [CAxWindow](../atl/reference/caxwindow-class.md) manipula una ventana que hospeda un control ActiveX.

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md) proporciona métodos para manipular una ventana que hospeda un control ActiveX y también tiene compatibilidad para hospedar controles ActiveX con licencia.

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) implementa una ventana dentro de otro objeto.

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) administra la información de una nueva clase de ventana.

- [CDynamicChain](../atl/reference/cdynamicchain-class.md) admite el encadenamiento dinámico de mapas de mensajes.

- [CMessageMap](../atl/reference/cmessagemap-class.md) permite que un objeto exponga su mensaje se asigna a otros objetos.

- [CWinTraits](../atl/reference/cwintraits-class.md) proporciona un método sencillo de estandarizar los rasgos de un objeto de ventana ATL.

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) proporciona valores predeterminados para los estilos de ventana y estilos extendidos utilizados para crear una ventana. Estos valores se agregan, mediante el operador OR lógico, para los valores proporcionados durante la creación de una ventana.

## <a name="related-articles"></a>Artículos relacionados

[Clases de ventana ATL](../atl/atl-window-classes.md)

[Tutorial de ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)<br/>
[Macros de mapa de mensajes](../atl/reference/message-map-macros-atl.md)<br/>
[Macros de clase de ventana](../atl/reference/window-class-macros.md)
