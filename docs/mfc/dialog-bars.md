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
ms.openlocfilehash: 800cc208df7299cf440508c2705b0b0ddb9ae665
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175358"
---
# <a name="dialog-bars"></a>Barras de cuadro de diálogo

Una barra de cuadro de diálogo es una barra de herramientas, un tipo de [barra de control](../mfc/control-bars.md) que puede contener cualquier tipo de control. Porque tiene las características de un cuadro de diálogo no modal, un [CDialogBar](../mfc/reference/cdialogbar-class.md) objeto proporciona una barra de herramientas más eficaces.

Hay varias diferencias claves entre una barra de herramientas y un `CDialogBar` objeto. Un `CDialogBar` objeto se crea a partir de un recurso de plantilla de cuadro de diálogo, que puede crear con el editor de cuadro de diálogo de Visual C++ y que puede contener cualquier tipo de control de Windows. El usuario puede tabular desde el control al control. Y puede especificar un estilo de alineación para alinear la barra de cuadro de diálogo con cualquier parte de la ventana de marco principal o incluso a dejarlo en su lugar, si se cambia el tamaño del elemento primario. La siguiente ilustración muestra una barra de cuadro de diálogo con una variedad de controles.

![Barra de cuadro de diálogo VC](../mfc/media/vc378t1.gif "barra de cuadro de diálogo VC") <br/>
Una barra de cuadro de diálogo

En otros aspectos, trabajar con un `CDialogBar` objeto es similar a trabajar con un cuadro de diálogo no modal. Usar el editor de cuadro de diálogo para diseñar y crear el recurso de cuadro de diálogo.

Una de las virtudes de las barras de cuadro de diálogo es que pueden incluir controles diferentes de los botones.

Aunque es normal para derivar sus propias clases de cuadro de diálogo de `CDialog`, normalmente no derive su propia clase de una barra de cuadro de diálogo. Barras de cuadro de diálogo son extensiones de ventana principal y los mensajes de notificación de control de barra de cuadro de diálogo, como **BN_CLICKED** o **EN_CHANGE**, se enviará con el elemento primario del cuadro de diálogo de la barra, la ventana principal.

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)<br/>
[Ejemplo](../visual-cpp-samples.md)

