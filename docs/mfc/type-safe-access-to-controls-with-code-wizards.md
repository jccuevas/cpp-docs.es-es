---
title: Acceso con seguridad de tipos a los controles con Asistentes para código
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: bf3ecf3016fcc15bd4ada7a15208acd9a04ca0a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180868"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Acceso con seguridad de tipos a los controles con Asistentes para código

Si está familiarizado con las características DDX, puede usar la propiedad del Control en el [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) para crear el acceso de seguridad de tipos. Este enfoque es más sencillo que crear controles sin asistentes para código.

Si simplemente desea tener acceso al valor de un control, DDX lo proporciona. Si desea tener acceso a más de un valor del control, utilice al Asistente para agregar variables miembro para agregar una variable miembro de la clase correspondiente a la clase de cuadro de diálogo. Conecte esta variable miembro a la propiedad del Control.

Las variables de miembro pueden tener una propiedad de Control en lugar de una propiedad de valor. La propiedad Value hace referencia al tipo de datos devueltos desde el control, como `CString` o **int**. La propiedad de Control permite el acceso directo al control a través de un miembro de datos cuyo tipo es una de las clases de control en MFC, como `CButton` o `CEdit`.

> [!NOTE]
>  Para un control determinado, puede, si lo desea, tendrá varias variables de miembro con la propiedad de valor y, a lo sumo, una variable miembro con la propiedad del Control. Puede tener solo un objeto MFC asignado a un control porque varios objetos que se adjunta a un control o cualquier otra ventana, daría lugar a una ambigüedad en el mapa de mensajes.

Puede utilizar este objeto para llamar a funciones miembro para el objeto de control. Tales llamadas afectan al control en el cuadro de diálogo. Por ejemplo, para un control de casilla de verificación representado por una variable *m_Checkbox*, del tipo `CButton`, se podría llamar:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Aquí la variable miembro *m_Checkbox* tiene la misma finalidad que la función miembro `GetMyCheckbox` se muestra en [acceso con seguridad de tipos a los controles sin asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md). Si la casilla de verificación no es una casilla de verificación automática, todavía necesitaría un controlador en la clase de cuadro de diálogo para el mensaje de notificación de control BN_CLICKED cuando se hace clic en el botón.

Para obtener más información acerca de los controles, vea [controles](../mfc/controls-mfc.md).

## <a name="see-also"></a>Vea también

[Acceso con seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Acceso con seguridad de tipos a los controles sin Asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md)
