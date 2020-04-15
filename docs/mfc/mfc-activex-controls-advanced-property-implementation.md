---
title: 'Controles ActiveX MFC: Implementación de propiedades avanzada'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d4f1265e6540e9f84bdb680e7948a4e308d31bb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364647"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Controles ActiveX MFC: Implementación de propiedades avanzada

En este artículo se describen temas relacionados con la implementación de propiedades avanzadas en un control ActiveX.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

- [Propiedades de solo lectura y de solo escritura](#_core_read2donly_and_write2donly_properties)

- [Devolver códigos de error de una propiedad](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Propiedades de solo lectura y solo escritura

El Asistente para agregar propiedades proporciona un método rápido y fácil para implementar propiedades de solo lectura o de solo escritura para el control.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Para implementar una propiedad de solo lectura o de solo escritura

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el cuadro Nombre de **propiedad,** escriba el nombre de la propiedad.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. En el cuadro Tipo de **propiedad,** seleccione el tipo adecuado para la propiedad.

1. Si desea una propiedad de solo lectura, desactive el establecer nombre de función. Si desea una propiedad de solo escritura, desactive el Get nombre de función.

1. Haga clic en **Finalizar**

Al hacerlo, el Asistente para agregar `SetNotSupported` propiedades `GetNotSupported` inserta la función o en la entrada de mapa de distribución en lugar de una función Normal Set u Get.

Si desea cambiar una propiedad existente para que sea de solo lectura o de solo escritura, puede editar el mapa de distribución manualmente y quitar la función Set u Get innecesaria de la clase de control.

Si desea que una propiedad sea condicionalmente de solo lectura o de solo escritura (por ejemplo, solo cuando el control está funcionando en un modo determinado), puede proporcionar la función Set u Get, como normal, y llamar a la `SetNotSupported` función o cuando `GetNotSupported` corresponda. Por ejemplo:

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Este ejemplo `SetNotSupported` de `m_bReadOnlyMode` código llama si el miembro de datos es **TRUE**. Si **FALSE**, la propiedad se establece en el nuevo valor.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Devolución de códigos de error de una propiedad

Para indicar que se ha producido un error al intentar `COleControl::ThrowError` obtener o establecer una propiedad, utilice la función, que toma un SCODE (código de estado) como parámetro. Puede utilizar un SCODE predefinido o definir uno propio. Para obtener una lista de SCODE predefinidos e instrucciones para definir SCODE personalizados, consulte Control de errores en el [control ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) en el artículo Controles ActiveX: Temas avanzados.

Existen funciones auxiliares para los SCODE predefinidos más comunes, como [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)y [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`está diseñado para usarse solo como un medio para devolver un error desde dentro de una propiedad Get o Set función o un método de automatización. Estas son las únicas veces que el controlador de excepciones adecuado estará presente en la pila.

Para obtener más información sobre cómo notificar excepciones en otras áreas del código, vea [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) y la sección Control de errores en el [control ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) en el artículo Controles ActiveX: Temas avanzados.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
