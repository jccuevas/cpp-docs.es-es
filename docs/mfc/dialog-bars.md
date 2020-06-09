---
title: Barras de cuadro de diálogo
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: 052e0b8a085c052f73d3c6540521f57fdfbb9c51
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624898"
---
# <a name="dialog-bars"></a>Barras de cuadro de diálogo

Una barra de cuadro de diálogo es una barra de herramientas, un tipo de [barra de controles](control-bars.md) que puede contener cualquier tipo de control. Dado que tiene las características de un cuadro de diálogo no modal, un objeto [CDialogBar](reference/cdialogbar-class.md) proporciona una barra de herramientas más eficaz.

Hay varias diferencias clave entre una barra de herramientas y un `CDialogBar` objeto. Un `CDialogBar` objeto se crea a partir de un recurso de plantilla de cuadro de diálogo, que se puede crear con el editor de cuadros de diálogo Visual C++ y que puede contener cualquier tipo de control de Windows. El usuario puede tabular de control a control. Además, puede especificar un estilo de alineación para alinear la barra de cuadro de diálogo con cualquier parte de la ventana de marco primario o incluso dejarla en su lugar si se cambia el tamaño del elemento primario. En la ilustración siguiente se muestra una barra de cuadro de diálogo con varios controles.

![Barra de cuadro de diálogo de VC](../mfc/media/vc378t1.gif "Barra de cuadro de diálogo de VC") <br/>
Una barra de cuadro de diálogo

En otros aspectos, trabajar con un `CDialogBar` objeto es como trabajar con un cuadro de diálogo no modal. Utilice el editor de cuadros de diálogo para diseñar y crear el recurso de cuadro de diálogo.

Una de las virtudes de las barras de diálogo es que pueden incluir controles distintos de los botones.

Aunque es normal derivar sus propias clases de cuadro de diálogo de `CDialog` , no se suele derivar su propia clase para una barra de cuadro de diálogo. Las barras de diálogo son extensiones de una ventana principal y los mensajes de notificación de control de la barra de cuadro de diálogo, como **BN_CLICKED** o **EN_CHANGE**, se enviarán al elemento primario de la barra de cuadro de diálogo, la ventana principal.

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)<br/>
[Ejemplo](../overview/visual-cpp-samples.md)
