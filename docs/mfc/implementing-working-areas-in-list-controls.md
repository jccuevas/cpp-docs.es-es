---
title: "Implementar áreas de trabajo en controles de lista | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cefb8007fd9b73dda4c0e8a99e9ae9daa1bfcc34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementar las áreas de trabajo en los controles de lista
De forma predeterminada, un control de lista organiza todos los elementos de un modo de cuadrícula estándar. Sin embargo, se admite otro método, las áreas, que organiza los elementos de lista en rectangulares grupos de trabajo. Para una imagen de un control de lista que implementa áreas de trabajo, vea Usar controles de vista de lista en el SDK de Windows.  
  
> [!NOTE]
>  Áreas de trabajo sólo son visibles cuando el control de lista está en modo de icono pequeño o icono. Sin embargo, las áreas de trabajo actual se mantienen si la vista se cambió al modo de informe o una lista.  
  
 Áreas de trabajo se pueden utilizar para mostrar un borde vacío (en el lado izquierdo, superior o derecha de los elementos), o hacer que una barra de desplazamiento horizontal que se mostrará cuando normalmente no haber uno. Otro uso frecuente es crear varias áreas de trabajo a la que los elementos se pueden mover o quitar. Con este método, podría crear áreas en una vista única que tienen significados diferentes. El usuario, a continuación, puede categorizar los elementos colocándolos en un área diferente. Un ejemplo de esto sería una vista de un sistema de archivos que tiene un área para archivos de lectura/escritura y otra área para archivos de solo lectura. Si se mueve un elemento de archivo en el área de solo lectura, automáticamente se volverían de solo lectura. Mover un archivo desde el área de solo lectura en el área de lectura/escritura haría que el archivo de lectura/escritura.  
  
 `CListCtrl`proporciona varias funciones miembro para crear y administrar áreas de trabajo en el control de lista. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) y [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) recuperar y establecer una matriz de `CRect` objetos (o `RECT` estructuras), que almacena las áreas de trabajo implementadas actualmente para el control de lista. Además, [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) recupera el número actual de áreas de trabajo para el control de lista (de forma predeterminada, cero).  
  
## <a name="items-and-working-areas"></a>Los elementos y las áreas de trabajo  
 Cuando se crea un área de trabajo, los elementos que se encuentran dentro del área de trabajo se convierten en miembros del mismo. De forma similar, si un elemento se mueve a un área de trabajo, se convierte en un miembro del área de trabajo a la que se ha movido. Si un elemento no está incluido dentro de cualquier área de trabajo, se convierte automáticamente en miembro de la primera área de trabajo (índice 0). Si desea crear un elemento y hacer que se coloca dentro de un área de trabajo específica, debe crear el elemento y, a continuación, traslade el área de trabajo deseada con una llamada a [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). El segundo ejemplo siguiente muestra esta técnica.  
  
 En el ejemplo siguiente se implementa cuatro áreas de trabajo (`rcWorkAreas`), de igual tamaño, con un borde de 10 píxeles de ancho alrededor de cada área de trabajo, en un control de lista (`m_WorkAreaListCtrl`).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]  
  
 La llamada a [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) se intentó obtener una estimación del área total necesario para mostrar todos los elementos en una región. Esta estimación, a continuación, se divide en cuatro regiones y se rellenan con un borde de 5 píxeles de ancho.  
  
 En el ejemplo siguiente se asigna los elementos de lista existentes a cada grupo (`rcWorkAreas`) y actualiza la vista de control (`m_WorkAreaListCtrl`) para completar el efecto.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

