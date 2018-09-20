---
title: Implementación de áreas de trabajo en los controles de lista | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc245ef87343d9f33277e41c5c191ea713e21da0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383422"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementar las áreas de trabajo en los controles de lista

De forma predeterminada, un control de lista organiza todos los elementos de un modo de cuadrícula estándar. Sin embargo, se admite otro método, las áreas, que organiza los elementos de lista en rectangulares grupos de trabajo. Para una imagen de un control de lista que implementa áreas de trabajo, vea Usar controles de vista de lista en el SDK de Windows.

> [!NOTE]
>  Áreas de trabajo sólo son visibles cuando el control de lista está en modo de iconos pequeños o icono. Sin embargo, se mantienen las áreas de trabajo actual si la vista cambia al modo de informe o una lista.

Áreas de trabajo pueden utilizarse para mostrar un borde vacío (en la parte izquierda, superior o derecha de los elementos), o provocar que se mostrará cuando hay normalmente no una barra de desplazamiento horizontal. Otro uso común es crear varias áreas de trabajo al que pueden mover o quitar elementos. Con este método, puede crear áreas en una sola vista que tienen significados diferentes. El usuario, a continuación, puede clasificar los elementos colocándolos en un área diferente. Un ejemplo de esto sería una vista de un sistema de archivos que tiene un área para archivos de lectura/escritura y otra área para archivos de solo lectura. Si un elemento de archivo se movieron en el área de solo lectura, convertiría automáticamente en solo lectura. Mover un archivo desde el área de solo lectura en el área de lectura/escritura haría que el archivo de lectura/escritura.

`CListCtrl` proporciona varias funciones de miembro para crear y administrar áreas de trabajo en el control de lista. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) y [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) recuperar y establecer una matriz de `CRect` objetos (o `RECT` estructuras), que almacena las áreas de trabajo implementadas actualmente para el control de lista. Además, [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) recupera el número actual de áreas de trabajo para el control de lista (de forma predeterminada, cero).

## <a name="items-and-working-areas"></a>Los elementos y las áreas de trabajo

Cuando se crea un área de trabajo, los elementos que se encuentren dentro del área de trabajo se convierten en miembros del mismo. De forma similar, si un elemento se mueve a un área de trabajo, se convierte en un miembro del área de trabajo al que se ha movido. Si un elemento no se encuentra dentro de cualquier área de trabajo, se convierte automáticamente en miembro de la primera área de trabajo (índice 0). Si desea crear un elemento y hacer que se coloca dentro de un área de trabajo específica, deberá crear el elemento y, a continuación, traslade el área de trabajo deseada con una llamada a [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). El segundo ejemplo siguiente muestra esta técnica.

El ejemplo siguiente implementa cuatro áreas de trabajo (`rcWorkAreas`), de igual tamaño con un borde de 10 píxeles de ancho alrededor de cada área de trabajo, en un control de lista (`m_WorkAreaListCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

La llamada a [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) se intentó obtener una estimación de la superficie total necesaria para mostrar todos los elementos en una región. Esta estimación se divide en cuatro regiones, a continuación y se rellenan con un borde de 5 píxeles de ancho.

En el ejemplo siguiente se asigna a los elementos de lista existente a cada grupo (`rcWorkAreas`) y actualiza la vista de control (`m_WorkAreaListCtrl`) para completar el efecto.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

