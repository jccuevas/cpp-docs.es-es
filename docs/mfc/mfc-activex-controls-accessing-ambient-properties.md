---
title: 'Controls ActiveX MFC: Acceso a las propiedades de ambiente'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: e5c78c9943f8baeadcc1198ee8c96f2023ac0215
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625443"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>Controls ActiveX MFC: Acceso a las propiedades de ambiente

En este artículo se describe cómo un control ActiveX puede tener acceso a las propiedades de ambiente de su contenedor de control.

Un control puede obtener información sobre su contenedor mediante el acceso a las propiedades de ambiente del contenedor. Estas propiedades exponen características visuales, como el color de fondo del contenedor, la fuente actual usada por el contenedor y características operativas, como si el contenedor está actualmente en modo de usuario o en modo de diseñador. Un control puede utilizar propiedades de ambiente para adaptar su apariencia y comportamiento al contenedor determinado en el que se inserta. Sin embargo, un control nunca debe suponer que su contenedor será compatible con cualquier propiedad de ambiente determinada. De hecho, es posible que algunos contenedores no admitan ninguna propiedad de ambiente. En ausencia de una propiedad de ambiente, un control debe suponer un valor predeterminado razonable.

Para tener acceso a una propiedad de ambiente, realice una llamada a [COleControl:: getAmbientProperty](reference/colecontrol-class.md#getambientproperty). Esta función espera el ID. de envío de la propiedad de ambiente como primer parámetro (el archivo OLECTL. H define los identificadores de envío para el conjunto estándar de propiedades de ambiente).

Los parámetros de la `GetAmbientProperty` función son el ID. de envío, una etiqueta variante que indica el tipo de propiedad esperado y un puntero a la memoria en la que se debe devolver el valor. El tipo de datos al que hace referencia este puntero variará en función de la etiqueta variante. La función devuelve **true** si el contenedor admite la propiedad; en caso contrario, devuelve **false**.

En el ejemplo de código siguiente se obtiene el valor de la propiedad de ambiente denominada "en modo de". Si el contenedor no admite la propiedad, se asume un valor predeterminado de **true** :

[!code-cpp[NVC_MFC_AxUI#30](codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

Para su comodidad, `COleControl` proporciona funciones auxiliares que tienen acceso a muchas de las propiedades de ambiente usadas con frecuencia y devuelven los valores predeterminados adecuados cuando las propiedades no están disponibles. Estas funciones auxiliares son las siguientes:

- [COleControl:: AmbientBackColor](reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  El llamador debe llamar a `Release( )` en la fuente devuelta.

- [AmbientForeColor](reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](reference/colecontrol-class.md#ambientshowgrabhandles)

Si el valor de una propiedad de ambiente cambia (a través de alguna acción del contenedor), `OnAmbientPropertyChanged` se llama a la función miembro del control. Invalide esta función miembro para controlar este tipo de notificación. El parámetro de `OnAmbientPropertyChanged` es el ID. de envío de la propiedad ambiente afectada. El valor de este identificador de envío puede ser DISPID_UNKNOWN, lo que indica que una o más propiedades de ambiente han cambiado, pero la información sobre qué propiedades se vieron afectados no está disponible.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
