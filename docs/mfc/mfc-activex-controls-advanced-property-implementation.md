---
title: 'Controles ActiveX MFC: Implementación de propiedades avanzada'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d26dbcb1c18c3c939214051d9010cb5b6db90929
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568030"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Controles ActiveX MFC: Implementación de propiedades avanzada

Este artículo describe temas relacionados con la implementación de propiedades avanzadas en un control ActiveX.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

- [Propiedades de solo lectura y de solo escritura](#_core_read2donly_and_write2donly_properties)

- [Devolver códigos de error de una propiedad](#_core_returning_error_codes_from_a_property)

##  <a name="_core_read2donly_and_write2donly_properties"></a> Propiedades de solo lectura y de solo escritura

El Asistente para agregar propiedades proporciona un método rápido y sencillo para implementar propiedades de solo lectura o solo escritura para el control.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Para implementar una propiedad de solo lectura o solo escritura

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el **nombre de la propiedad** , escriba el nombre de la propiedad.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. En el **tipo de propiedad** , seleccione el tipo adecuado para la propiedad.

1. Si desea que una propiedad de solo lectura, desactive el nombre de la función de conjunto. Si desea que una propiedad de solo escritura, desactive el nombre de la función Get.

9. Haga clic en **Finalizar**.

Al hacerlo, el Asistente para agregar propiedades inserta la función `SetNotSupported` o `GetNotSupported` en la entrada de mapa de envíos en lugar de una normal establecer u obtener la función.

Si desea cambiar una propiedad existente para que sea de solo lectura o solo escritura, puede editar manualmente el mapa de envíos y quite la función Set o Get innecesaria de la clase de control.

Si desea que una propiedad condicionalmente de solo lectura o de sólo escritura (por ejemplo, solo cuando el control está funcionando en un modo determinado), puede proporcionar la función Set o Get, como es habitual y llamar a la `SetNotSupported` o `GetNotSupported` funcione en su caso. Por ejemplo:

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Este ejemplo de código llama a `SetNotSupported` si el `m_bReadOnlyMode` es miembro de datos **TRUE**. Si **FALSE**, la propiedad se establece en el nuevo valor.

##  <a name="_core_returning_error_codes_from_a_property"></a> Devolver códigos de Error de una propiedad

Para indicar que se ha producido un error al intentar obtener o establecer una propiedad, utilice el `COleControl::ThrowError` función, que toma un SCODE (código de estado) como un parámetro. Puede utilizar un SCODE predefinido o definir uno propio. Para obtener una lista de predefinidos SCODEs e instrucciones para definir SCODEs personalizados, consulte [control de errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en el artículo controles ActiveX: temas avanzados.

Funciones auxiliares existen para los más comunes predefinidos SCODEs, tales como [COleControl:: SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), y [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
>  `ThrowError` está pensado para usarse solo como un medio para devolver un error desde dentro Get de una propiedad o Set función o un método de automatización. Estas son las únicas veces que el controlador de excepciones adecuado estará presentan en la pila.

Para obtener más información sobre cómo informar de excepciones en otras áreas del código, consulte [COleControl:: FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección [control de errores en el ActiveX Control](../mfc/mfc-activex-controls-advanced-topics.md) en el artículo de controles ActiveX: avanzada Temas.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
