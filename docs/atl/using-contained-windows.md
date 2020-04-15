---
title: Uso de Ventanas contenidas
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 5da765eae28d411c98e79af5b9173f48ea66ef8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329302"
---
# <a name="using-contained-windows"></a>Uso de Ventanas contenidas

ATL implementa ventanas contenidas con [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Una ventana contenida representa una ventana que delega sus mensajes en un objeto contenedor en lugar de controlarlos en su propia clase.

> [!NOTE]
> No es necesario derivar una `CContainedWindowT` clase de para utilizar ventanas contenidas.

Con las ventanas contenidas, puede superclase de una clase de Windows existente o subclase una ventana existente. Para crear una ventana que superclase una clase de Windows existente, `CContainedWindowT` especifique primero el nombre de clase existente en el constructor para el objeto. A `CContainedWindowT::Create`continuación, llame a . Para subclase una ventana existente, no es necesario especificar un nombre de clase de Windows (pasar NULL al constructor). Simplemente llame `CContainedWindowT::SubclassWindow` al método con el identificador de la ventana que se va a subclases.

Normalmente se usan ventanas contenidas como miembros de datos de una clase contenedora. El contenedor no necesita ser una ventana; sin embargo, debe derivar de [CMessageMap](../atl/reference/cmessagemap-class.md).

Una ventana contenida puede utilizar mapas de mensajes alternativos para controlar sus mensajes. Si tiene más de una ventana contenida, debe declarar varios mapas de mensajes alternativos, cada uno correspondiente a una ventana independiente contenida.

## <a name="example"></a>Ejemplo

A continuación se muestra un ejemplo de una clase contenedora con dos ventanas contenidas:

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Para obtener más información acerca de las ventanas contenidas, consulte el [subEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) ejemplo.

## <a name="see-also"></a>Consulte también

[Clases de ventanas](../atl/atl-window-classes.md)
