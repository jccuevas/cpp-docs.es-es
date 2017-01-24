---
title: "Controls ActiveX MFC: Acceso a las propiedades de ambiente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX en MFC, obtener acceso a las propiedades ambient"
  - "propiedades [MFC], obtener acceso a la propiedad ambient"
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controls ActiveX MFC: Acceso a las propiedades de ambiente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo un control ActiveX puede tener acceso a las propiedades de ambiente del contenedor del control.  
  
 Un control puede obtener información sobre el contenedor teniendo acceso a las propiedades de ambiente del contenedor.  Estas propiedades exponen características visuales, tales como el color de fondo del contenedor, la fuente actual utilizada por el contenedor, y características operativas, por ejemplo si el contenedor se encuentra en modo de modo usuario o del diseñador.  Un control puede utilizar propiedades de ambiente para personalizar su apariencia y comportamiento al contenedor determinado en el que se inserta.  Sin embargo, un control nunca debe suponer que el contenedor admitirá cualquier propiedad de ambiente determinada.  De hecho, algunos contenedores pueden no admitir ninguna propiedad de ambiente en absoluto.  En ausencia de una propiedad de ambiente, un control debe suponer un valor predeterminado razonable.  
  
 Para tener acceso a una propiedad de ambiente, haga una llamada a [COleControl::GetAmbientProperty](../Topic/COleControl::GetAmbientProperty.md).  Esta función espera el identificador de envío para la propiedad de ambiente como primer parámetro \(el archivo OLECTL.H define los id. de envío para el conjunto estándar de propiedades de ambiente\).  
  
 Los parámetros de la función de `GetAmbientProperty` son el identificador de envío, etiqueta variable que indica el tipo de propiedad esperado, y puntero a la memoria donde el valor debe ser devuelto.  El tipo de datos a los que este puntero vea varía dependiendo de la etiqueta variable.  La función devuelve **VERDADERO** si el contenedor admite la propiedad, si no devuelve **FALSE**.  
  
 El ejemplo de código siguiente se obtiene el valor de “UserMode propiedad denominada ambiente.” Si la propiedad no es compatible con el contenedor, un valor predeterminado de **VERDADERO** se supone:  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/CPP/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 Por comodidad, la aplicación auxiliar de fuentes de `COleControl` funciona que tiene acceso a muchas de las propiedades de ambiente de uso general y devuelve valores predeterminados adecuados cuando las propiedades no están disponibles.  Estas funciones auxiliares son los siguientes:  
  
-   [COleControl::AmbientBackColor](../Topic/COleControl::AmbientBackColor.md)  
  
-   [AmbientDisplayName](../Topic/COleControl::AmbientDisplayName.md)  
  
-   [AmbientFont](../Topic/COleControl::AmbientFont.md)  
  
    > [!NOTE]
    >  El llamador debe llamar a **Release\( \)** en la fuente devuelta.  
  
-   [AmbientForeColor](../Topic/COleControl::AmbientForeColor.md)  
  
-   [AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md)  
  
-   [AmbientScaleUnits](../Topic/COleControl::AmbientScaleUnits.md)  
  
-   [AmbientTextAlign](../Topic/COleControl::AmbientTextAlign.md)  
  
-   [AmbientUserMode](../Topic/COleControl::AmbientUserMode.md)  
  
-   [AmbientUIDead](../Topic/COleControl::AmbientUIDead.md)  
  
-   [AmbientShowHatching](../Topic/COleControl::AmbientShowHatching.md)  
  
-   [AmbientShowGrabHandles](../Topic/COleControl::AmbientShowGrabHandles.md)  
  
 Si el valor de los cambios de ambiente de una propiedad \(con alguna acción del contenedor\), la función miembro de **OnAmbientPropertyChanged** de control se denomina.  Invalide esta función miembro para controlar este tipo de notificación.  El parámetro para **OnAmbientPropertyChanged** es el identificador de envío de propiedad de ambiente afectada.  El valor del identificador de envío puede ser **DISPID\_UNKNOWN**, que indica que una o más propiedades de ambiente han cambiado, sólo información sobre qué propiedades estaba afectado no está disponible.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)