---
title: 'Controles ActiveX MFC: Acceso a las propiedades de ambiente | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd3376e19d7780922102240ae1bfaa1b4eb89b2b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931728"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>Controls ActiveX MFC: Acceso a las propiedades de ambiente
Este artículo describe cómo un control ActiveX puede tener acceso a las propiedades de ambiente de su contenedor de control.  
  
 Un control puede obtener información acerca de su contenedor mediante el acceso a propiedades de ambiente del contenedor. Estas propiedades exponen características visuales, como el color de fondo del contenedor, la fuente actual utilizada por el contenedor y características operativas, como si el contenedor está actualmente en modo de usuario o modo del diseñador. Un control puede utilizar propiedades de ambiente para personalizar su apariencia y comportamiento en el contenedor particular en el que está incrustado. Sin embargo, un control nunca debería suponer que su contenedor admitirá cualquier propiedad de ambiente. De hecho, algunos contenedores pueden no admitir las propiedades de ambiente en absoluto. En ausencia de una propiedad de ambiente, un control debe suponer un valor predeterminado razonable.  
  
 Para obtener acceso a una propiedad de ambiente, realizar una llamada a [COleControl:: GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty). Esta función espera el identificador de envío para la propiedad de ambiente como el primer parámetro (el archivo OLECTL. H define identificadores de envío para el conjunto estándar de propiedades de ambiente).  
  
 Los parámetros de la `GetAmbientProperty` función son el identificador de envío, una etiqueta variante que indica el tipo de propiedad esperada y un puntero a memoria que se debe devolver el valor. El tipo de datos al que hace referencia este puntero variará según la etiqueta variante. La función devuelve **TRUE** si el contenedor admite la propiedad, de lo contrario devuelve **FALSE**.  
  
 En el ejemplo de código siguiente se obtiene el valor de la propiedad de ambiente denominada "UserMode". Si la propiedad no es compatible con el contenedor, un valor predeterminado de **TRUE** se supone que:  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 Para su comodidad, `COleControl` proporciona funciones auxiliares que tener acceso a muchas de las propiedades de ambiente utilizadas y devuelven valores predeterminados oportunos cuando las propiedades no están disponibles. Estas funciones auxiliares son los siguientes:  
  
-   [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)  
  
-   [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)  
  
-   [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)  
  
    > [!NOTE]
    >  Llamador debe llamar a `Release( )` en la fuente devuelta.  
  
-   [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)  
  
-   [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)  
  
-   [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)  
  
-   [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)  
  
-   [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)  
  
-   [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)  
  
-   [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)  
  
-   [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)  
  
 Si cambia el valor de una propiedad de ambiente (a través de alguna acción del contenedor), el `OnAmbientPropertyChanged` se llama a la función miembro del control. Reemplace esta función miembro para controlar este tipo de notificación. El parámetro `OnAmbientPropertyChanged` es el identificador de envío de la propiedad de ambiente afectada. El valor de este identificador de envío puede ser DISPID_UNKNOWN, lo que indica que ha cambiado una o varias propiedades de ambiente, pero no está disponible la información acerca de qué propiedades resultaron afectadas.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

