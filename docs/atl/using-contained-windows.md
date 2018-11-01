---
title: Uso de Windows independiente
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 800ae7cab5fd99bfa140b481f87b1615ff5b2a13
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485376"
---
# <a name="using-contained-windows"></a>Uso de Windows independiente

ATL implementa las ventanas independientes con [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Una ventana contenida representa una ventana que delega sus mensajes en un objeto contenedor en lugar de controlarlos en su propia clase.

> [!NOTE]
>  No es necesario derivar una clase de `CContainedWindowT` para poder usar ventanas contenidas.

Con windows independientes, puede superclase de una clase existente de Windows o una subclase de una ventana existente. Para crear una ventana que convierte en superclase un Windows existente de clases, especifique primero el nombre de clase existente en el constructor para la `CContainedWindowT` objeto. A continuación, llamar a `CContainedWindowT::Create`. Para subclasificar una ventana existente, no es necesario especificar un nombre de clase de Windows (pase NULL al constructor). Basta con llamar a la `CContainedWindowT::SubclassWindow` método con el identificador de la ventana que se va a crear subclase.

Independientes windows se utilizan normalmente como miembros de datos de una clase de contenedor. El contenedor no necesita ser una ventana; Sin embargo, debe derivar de [CMessageMap](../atl/reference/cmessagemap-class.md).

Una ventana contenida puede utilizar mapas de mensajes alternativos para controlar sus mensajes. Si tiene más de una ventana independiente, debe declarar que varias alternan de mapas de mensajes, cada uno correspondiente a una ventana contenida independiente.

## <a name="example"></a>Ejemplo

Este es un ejemplo de una clase de contenedor con dos ventanas independientes:

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Para obtener más información acerca de windows independientes, consulte el [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) ejemplo.

## <a name="see-also"></a>Vea también

[Clases de ventana](../atl/atl-window-classes.md)

