---
title: 'Controles ActiveX MFC: Implementación de propiedades avanzada'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: f5abef4db2f9c6d375428c0b0fd313198ce6283f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621229"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Controles ActiveX MFC: Implementación de propiedades avanzada

En este artículo se describen los temas relacionados con la implementación de propiedades avanzadas en un control ActiveX.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

- [Propiedades de solo lectura y de solo escritura](#_core_read2donly_and_write2donly_properties)

- [Devolver códigos de error de una propiedad](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Propiedades de solo lectura y de solo escritura

El Asistente para agregar propiedades proporciona un método rápido y sencillo para implementar propiedades de solo lectura o de solo escritura para el control.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Para implementar una propiedad de solo lectura o de solo escritura

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar propiedad**.

   Se abrirá el [Asistente para agregar propiedades](../ide/names-add-property-wizard.md).

1. En el cuadro **nombre de propiedad** , escriba el nombre de la propiedad.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. En el cuadro **tipo de propiedad** , seleccione el tipo adecuado para la propiedad.

1. Si desea una propiedad de solo lectura, borre el nombre de la función set. Si desea una propiedad de solo escritura, desactive el nombre de la función get.

1. Haga clic en **Finalizar**

Al hacerlo, el Asistente para agregar propiedades inserta la función `SetNotSupported` o `GetNotSupported` en la entrada de mapa de envío en lugar de una función set o GET normal.

Si desea cambiar una propiedad existente para que sea de solo lectura o de solo escritura, puede editar el mapa de envío manualmente y quitar la función set o get innecesaria de la clase del control.

Si desea que una propiedad sea de solo lectura condicional o de solo escritura (por ejemplo, solo cuando el control está funcionando en un modo determinado), puede proporcionar la función set u get, como de costumbre, y llamar a la `SetNotSupported` función o `GetNotSupported` cuando corresponda. Por ejemplo:

[!code-cpp[NVC_MFC_AxUI#29](codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Este ejemplo de código llama a `SetNotSupported` si el `m_bReadOnlyMode` miembro de datos es **true**. Si es **false**, la propiedad se establece en el nuevo valor.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Devolver códigos de error de una propiedad

Para indicar que se ha producido un error al intentar obtener o establecer una propiedad, utilice la `COleControl::ThrowError` función, que toma SCODE (código de estado) como parámetro. Puede usar un SCODE predefinido o definir uno de los suyos propios. Para obtener una lista de SCODEs predefinidos e instrucciones para definir SCODEs personalizados, vea [control de errores en el control ActiveX](mfc-activex-controls-advanced-topics.md) en el artículo controles ActiveX: temas avanzados.

Existen funciones auxiliares para los SCODEs predefinidos más comunes, como [COleControl:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl:: GetNotSupported](reference/colecontrol-class.md#getnotsupported)y [COleControl:: SetNotPermitted](reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`está pensado para usarse únicamente como medio para devolver un error desde dentro de la función get o set de una propiedad o un método de automatización. Estas son las únicas veces en que el controlador de excepciones adecuado estará presente en la pila.

Para obtener más información sobre la generación de informes de excepciones en otras áreas del código, vea [COleControl:: FireError (](reference/colecontrol-class.md#fireerror) y la sección [control de errores en el control ActiveX](mfc-activex-controls-advanced-topics.md) en el artículo controles ActiveX: temas avanzados.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Propiedades](mfc-activex-controls-properties.md)<br/>
[Controles ActiveX MFC: Métodos](mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](reference/colecontrol-class.md)
