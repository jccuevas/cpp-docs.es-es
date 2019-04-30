---
title: 'Controles ActiveX MFC: Obtener acceso a las propiedades de ambiente'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: 585ec8720a654bbcb728330d70ddb914f2543e41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239744"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>Controles ActiveX MFC: Obtener acceso a las propiedades de ambiente

Este artículo describe cómo un control ActiveX puede tener acceso a las propiedades de ambiente de su contenedor.

Un control puede obtener información acerca de su contenedor mediante el acceso a las propiedades de ambiente del contenedor. Estas propiedades exponen características visuales, como el color de fondo del contenedor, la fuente actual utilizada por el contenedor y las características operativas, como si el contenedor está actualmente en modo de usuario o modo del diseñador. Un control puede usar las propiedades de ambiente para personalizar su apariencia y comportamiento en el contenedor determinado en el que está incrustado. Sin embargo, un control nunca debe suponer que su contenedor admitirá cualquier propiedad de ambiente. De hecho, algunos contenedores pueden no admitir las propiedades de ambientales en absoluto. En ausencia de una propiedad de ambiente, un control debe suponer un valor predeterminado razonable.

Para obtener acceso a una propiedad de ambiente, realice una llamada a [COleControl:: GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty). Esta función espera el identificador de envío para la propiedad de ambiente como el primer parámetro (el archivo OLECTL. H define los identificadores de envío para el conjunto estándar de las propiedades de ambiente).

Los parámetros de la `GetAmbientProperty` función son el identificador de envío, una etiqueta de tipo variant que indica el tipo de propiedad esperado y un puntero a la memoria donde se debe devolver el valor. El tipo de datos al que hace referencia este puntero variará dependiendo de la etiqueta de variante. La función devuelve **TRUE** si el contenedor admite la propiedad, de lo contrario devuelve **FALSE**.

El ejemplo de código siguiente obtiene el valor de la propiedad de ambiente denominada "UserMode". Si la propiedad no es compatible con el contenedor, un valor predeterminado de **TRUE** se supone que:

[!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

Para su comodidad, `COleControl` proporciona funciones auxiliares que acceder a muchas de las propiedades de ambientales utilizadas y devuelven los valores predeterminados adecuados cuando las propiedades no están disponibles. Estas funciones auxiliares son los siguientes:

- [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  Llamador debe llamar a `Release( )` en la fuente devuelta.

- [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)

Si cambia el valor de una propiedad de ambiente (a través de alguna acción del contenedor), el `OnAmbientPropertyChanged` se llama a la función miembro del control. Reemplace esta función miembro para administrar dicha notificación. El parámetro `OnAmbientPropertyChanged` es el identificador de envío de la propiedad de ambiente afectado. El valor de este identificador de envío puede ser DISPID_UNKNOWN, lo que indica que ha cambiado una o varias propiedades de ambientales, pero no está disponible la información sobre qué propiedades afectadas.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
