---
title: Acceso con seguridad de tipos a los controles con Asistentes para código
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: b49c1b6f21dfe5270e40649241812320303ad411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370916"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Acceso con seguridad de tipos a los controles con Asistentes para código

Si está familiarizado con las características de DDX, puede usar la propiedad Control en el [Asistente para agregar](../ide/add-member-variable-wizard.md) variables miembro para crear acceso con seguridad de tipos. Este enfoque es más fácil que crear controles sin asistentes de código.

Si simplemente desea tener acceso al valor de un control, DDX lo proporciona. Si desea hacer más que tener acceso al valor de un control, utilice el Asistente para agregar variables miembro para agregar una variable miembro de la clase adecuada a la clase de cuadro de diálogo. Asocie esta variable miembro a la Control propiedad.

Las variables miembro pueden tener un Control propiedad en lugar de un Value propiedad. El Value propiedad hace referencia al tipo de `CString` datos devueltos desde el control, como o **int**. El Control propiedad habilita el acceso directo al control a través de un `CButton` `CEdit`miembro de datos cuyo tipo es una de las clases de control en MFC, como o .

> [!NOTE]
> Para un control determinado, puede, si lo desea, tener varias variables miembro con el Value propiedad y como máximo una variable miembro con el Control propiedad. Solo puede tener un objeto MFC asignado a un control porque varios objetos asociados a un control, o cualquier otra ventana, daría lugar a una ambiguedad en el mapa de mensajes.

Puede utilizar este objeto para llamar a cualquier función miembro para el objeto de control. Estas llamadas afectan al control en el cuadro de diálogo. Por ejemplo, para un control de casilla de verificación representado por una variable *m_Checkbox*, de tipo `CButton`, podría llamar a:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Aquí la variable miembro *m_Checkbox* tiene el `GetMyCheckbox` mismo propósito que la función miembro que se muestra en El acceso seguro de tipo a los [controles sin asistentes de código](../mfc/type-safe-access-to-controls-without-code-wizards.md). Si la casilla de verificación no es una casilla de verificación automática, todavía necesitaría un controlador en la clase de cuadro de diálogo para el mensaje de notificación de control de BN_CLICKED cuando se hace clic en el botón.

Para obtener más información acerca de los controles, vea [Controles](../mfc/controls-mfc.md).

## <a name="see-also"></a>Consulte también

[Acceso con seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Acceso con seguridad de tipos a los controles sin Asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md)
