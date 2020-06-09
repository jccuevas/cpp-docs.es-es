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
ms.openlocfilehash: 54e43c8445bb6b8db4c6a7a4b28890e81be52d6c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616957"
---
# <a name="deriving-controls-from-a-standard-control"></a>Derivar controles de un control estándar

Al igual que con cualquier clase derivada de [CWnd](reference/cwnd-class.md), puede modificar el comportamiento de un control derivando una nueva clase de una clase de control existente.

### <a name="to-create-a-derived-control-class"></a>Para crear una clase de control derivada

1. Derive la clase de una clase de control existente y, opcionalmente, reemplace la `Create` función miembro para que proporcione los argumentos necesarios para la función de clase base `Create` .

1. Proporcionar funciones miembro de controlador de mensajes y entradas de mapa de mensajes para modificar el comportamiento del control en respuesta a mensajes de Windows específicos. Vea [asignar mensajes a funciones](reference/mapping-messages-to-functions.md).

1. Proporcionar nuevas funciones miembro para extender la funcionalidad del control (opcional).

El uso de un control derivado en un cuadro de diálogo requiere trabajo adicional. Los tipos y las posiciones de los controles en un cuadro de diálogo se especifican normalmente en un recurso de plantilla de cuadro de diálogo. Si crea una clase de control derivada, no puede especificarla en una plantilla de cuadro de diálogo, ya que el compilador de recursos no sabe nada sobre la clase derivada.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Para colocar el control derivado en un cuadro de diálogo

1. Inserte un objeto de la clase de control derivada en la declaración de la clase de cuadro de diálogo derivada.

1. Invalide la `OnInitDialog` función miembro en la clase de cuadro de diálogo para llamar a la `SubclassDlgItem` función miembro para el control derivado.

`SubclassDlgItem`"subclases dinámicamente" un control creado a partir de una plantilla de cuadro de diálogo. Cuando un control se subclase dinámicamente, se enlaza a Windows, se procesan algunos mensajes dentro de su propia aplicación y, a continuación, se pasan los mensajes restantes a Windows. Para obtener más información, vea la función miembro [SubclassDlgItem](reference/cwnd-class.md#subclassdlgitem) de `CWnd` la clase en la *referencia de MFC*. En el ejemplo siguiente se muestra cómo se puede escribir una invalidación de `OnInitDialog` para llamar a `SubclassDlgItem` :

[!code-cpp[NVC_MFCControlLadenDialog#3](codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Dado que el control derivado se incrusta en la clase de cuadro de diálogo, se construirá cuando se construya el cuadro de diálogo y se destruirá cuando se destruya el cuadro de diálogo. Compare este código con el ejemplo de [Agregar controles a mano](adding-controls-by-hand.md).

## <a name="see-also"></a>Consulte también

[Creación y uso de controles](making-and-using-controls.md)<br/>
[Permite](controls-mfc.md)
