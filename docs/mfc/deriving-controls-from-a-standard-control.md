---
title: Derivar controles de un control estándar
ms.date: 11/04/2016
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
ms.openlocfilehash: 5abdcc87dba937938ffa3643d19ff69431f62af4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300381"
---
# <a name="deriving-controls-from-a-standard-control"></a>Derivar controles de un control estándar

Igual que con cualquier [CWnd](../mfc/reference/cwnd-class.md)-clase derivada, puede modificar el comportamiento de un control derivando una nueva clase de una clase de control existente.

### <a name="to-create-a-derived-control-class"></a>Para crear una clase derivada de control

1. Derive la clase de una clase de control existente y, opcionalmente, invalide el `Create` función miembro para que proporcione los argumentos necesarios para la clase base `Create` función.

1. Proporcione funciones de miembro de controlador de mensajes y las entradas de mapa de mensajes para modificar el comportamiento del control en respuesta a mensajes específicos de Windows. Consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).

1. Proporciona nuevas funciones de miembro para extender la funcionalidad del control (opcional).

Uso de un control derivado en un cuadro de diálogo requiere trabajo adicional. Los tipos y las posiciones de los controles en un cuadro de diálogo normalmente se especifican en un recurso de plantilla de cuadro de diálogo. Si crea una clase derivada de control, no se puede especificar en una plantilla de cuadro de diálogo, ya que el compilador de recursos no sabe nada acerca de la clase derivada.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Para colocar el control derivado en un cuadro de diálogo

1. Incrustar un objeto de la clase de control derivada en la declaración de la clase derivada de cuadro de diálogo.

1. Invalidar el `OnInitDialog` función de miembro en la clase de cuadro de diálogo para llamar a la `SubclassDlgItem` la función miembro para el control derivado.

`SubclassDlgItem` "dinámicamente las subclases" crea un control de una plantilla de cuadro de diálogo. Cuando un control dinámicamente es una subclase, enlazar en Windows, procesar algunos mensajes dentro de su aplicación y pasar los mensajes restantes a Windows. Para obtener más información, consulte el [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) función miembro de clase `CWnd` en el *referencia de MFC*. El ejemplo siguiente muestra cómo podría escribir una invalidación de `OnInitDialog` para llamar a `SubclassDlgItem`:

[!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Dado que el control derivado está incrustado en la clase de cuadro de diálogo, se construirá cuando se crea el cuadro de diálogo, y se destruye cuando se destruye el cuadro de diálogo. Compare este código en el ejemplo de [agregar controles manualmente](../mfc/adding-controls-by-hand.md).

## <a name="see-also"></a>Vea también

[Creación y uso de controles](../mfc/making-and-using-controls.md)<br/>
[Controles](../mfc/controls-mfc.md)
