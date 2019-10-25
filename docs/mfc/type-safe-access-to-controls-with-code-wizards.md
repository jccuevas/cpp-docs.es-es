---
title: Acceso con seguridad de tipos a los controles con Asistentes para código
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: fefa722209d37e2612201c4471e5764f9d71f27a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685044"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Acceso con seguridad de tipos a los controles con Asistentes para código

Si está familiarizado con las características de DDX, puede usar la propiedad control del [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para crear acceso con seguridad de tipos. Este enfoque es más fácil que crear controles sin asistentes para código.

Si simplemente desea tener acceso al valor de un control, DDX lo proporciona. Si desea hacer más que el acceso al valor de un control, use el Asistente para agregar variables miembro para agregar una variable miembro de la clase adecuada a la clase de cuadro de diálogo. Adjunte esta variable miembro a la propiedad del control.

Las variables de miembro pueden tener una propiedad de control en lugar de una propiedad Value. La propiedad Value hace referencia al tipo de datos devueltos por el control, como `CString` o **int**. La propiedad control permite el acceso directo al control a través de un miembro de datos cuyo tipo es una de las clases de control de MFC, como `CButton` o `CEdit`.

> [!NOTE]
>  Para un control determinado, puede, si lo desea, tener varias variables miembro con la propiedad Value y, como máximo, una variable miembro con la propiedad control. Solo puede tener un objeto MFC asignado a un control porque varios objetos adjuntos a un control, o cualquier otra ventana, provocaría una ambigüedad en el mapa de mensajes.

Puede utilizar este objeto para llamar a cualquier función miembro para el objeto de control. Dichas llamadas afectan al control en el cuadro de diálogo. Por ejemplo, para un control de casilla representado por una variable *m_Checkbox*, de tipo `CButton`, podría llamar a:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Aquí, la variable miembro *M_Checkbox* tiene el mismo propósito que la función miembro `GetMyCheckbox` que se muestra en [acceso con seguridad de tipos a los controles sin asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md). Si la casilla no es una casilla automática, seguirá necesitando un controlador en la clase de cuadro de diálogo para el mensaje de notificación de control BN_CLICKED cuando se haga clic en el botón.

Para obtener más información sobre los controles, consulte [controles](../mfc/controls-mfc.md).

## <a name="see-also"></a>Vea también

[Acceso con seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Acceso con seguridad de tipos a los controles sin Asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md)
