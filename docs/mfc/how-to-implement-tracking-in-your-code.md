---
title: "C&#243;mo: Implementar el seguimiento en el c&#243;digo | Microsoft Docs"
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
  - "CRectTracker (clase), implementar seguimiento"
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Implementar el seguimiento en el c&#243;digo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para seguir un elemento OLE, debe controlar ciertos eventos relacionados con el elemento, como hacer clic en el elemento o actualizar la vista del documento.  En todos los casos, es suficiente para declarar un objeto temporal de [CRectTracker](../mfc/reference/crecttracker-class.md) y manipular el elemento mediante este objeto.  
  
 Cuando un usuario selecciona un elemento o incrusta un objeto con un comando de menú, debe inicializar el seguimiento con estilos adecuados para representar el estado del elemento.  La tabla siguiente se describen las convenciones utilizadas por el ejemplo OCLIENT.  Para obtener más información sobre estos estilos, vea `CRectTracker`.  
  
### Estilos del contenedor y el estado del elemento OLE  
  
|Estilo mostrado|Estado del elemento OLE|  
|---------------------|-----------------------------|  
|Borde dotted|Se vincula el elemento|  
|Borde sólido|El elemento se incrusta en el documento|  
|Asas de ajuste de tamaño|El elemento está seleccionado|  
|Borde tramado|El elemento es actualmente activo en contexto|  
|Tramando el modelo se superpone al elemento|El servidor de elemento está abierto|  
  
 Puede administrar esta inicialización fácilmente utilizando un procedimiento que compruebe el estado del elemento OLE y establezca los estilos apropiados.  La función de **SetupTracker** encontrada en el ejemplo OCLIENT muestra la inicialización del seguimiento.  Los parámetros para esta función son la dirección de seguimiento, *pTracker*; un puntero al elemento que se relaciona con el seguimiento, `pItem`de cliente; y un puntero a un rectángulo, *pTrueRect*.  Para obtener un ejemplo completo de esta función, vea a MFC el ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md).  
  
 El ejemplo de código de **SetupTracker** muestra una sola función; las líneas de la función se da con la descripción de las características de la función:  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 El seguimiento se inicializa estableciendo el tamaño mínimo y borrar el estilo de seguimiento.  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 La comprobación de las líneas siguientes para ver si el elemento está seleccionado actualmente y si el elemento está vinculado al documento o incrustado en ella.  Los controles de tamaño situados dentro del borde se agregan al estilo, que indica que el elemento está seleccionado actualmente.  Si el elemento se vincula al documento, se utiliza el estilo de borde dotted.  Se utiliza un borde sólido si se inserta el elemento.  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 El código siguiente se superpone al elemento con un modelo tramado si el elemento está abierto.  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 Puede llamar a esta función siempre que el seguimiento tiene que mostrar.  Por ejemplo, llame a esta función desde la función de `OnDraw` de la clase de vista.  Esto actualiza el aspecto de seguimiento siempre que se dibujar la vista.  Para obtener un ejemplo completo, vea la función de **CMainView::OnDraw** de ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md)MFC.  
  
 En la aplicación, los eventos que requieren código de seguimiento, como cambiar el tamaño, mover, o la merma que detecta, aparecerán.  Estas acciones indican normalmente que se está creando un intento arrastrar o de mover el elemento.  En estos casos, deberá decidir qué se asida: un controlador de cambio de tamaño o parte del borde entre los controladores de tamaño.  El controlador de mensajes `OnLButtonDown` es un buen lugar para probar la posición del mouse en relación con el elemento.  Haga una llamada a `CRectTracker::HitTest`.  Si la prueba devuelve algo además de **CRectTracker::hitOutside**, se está cambiando de tamaño o se mueve el elemento.  Por consiguiente, debe realizar una llamada a la función miembro de `Track` .  Vea la función de **CMainView::OnLButtonDown** ubicada en el ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md) de MFC para obtener un ejemplo completo.  
  
 La clase de `CRectTracker` proporciona varias formas de cursor utilizadas para indicar si un movimiento, el tamaño, o la operación de arrastre está ocurriendo.  Para controlar este evento, comprobar si el elemento bajo el mouse está actualmente seleccionado.  Si es, haga una llamada a `CRectTracker::SetCursor`, o llamar al controlador predeterminado.  El ejemplo siguiente es el ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md)de MFC:  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/CPP/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## Vea también  
 [Seguimiento: Implementar el seguimiento en la aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)