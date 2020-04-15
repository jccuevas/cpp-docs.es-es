---
title: Implementar las áreas de trabajo en los controles de lista
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 91577203163247bd230fecb083cf1c50e2875b98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377223"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementar las áreas de trabajo en los controles de lista

De forma predeterminada, un control de lista organiza todos los elementos de forma estándar de cuadrícula. Sin embargo, se admite otro método, áreas de trabajo, que organiza los elementos de lista en grupos rectangulares. Para obtener una imagen de un control de lista que implementa áreas de trabajo, consulte Uso de controles de vista de lista en el Windows SDK.

> [!NOTE]
> Las áreas de trabajo solo están visibles cuando el control de lista está en modo de icono o de icono pequeño. Sin embargo, las áreas de trabajo actuales se mantienen si la vista cambia al modo de informe o lista.

Las áreas de trabajo se pueden utilizar para mostrar un borde vacío (a la izquierda, la parte superior y/o la derecha de los elementos), o hacer que se muestre una barra de desplazamiento horizontal cuando normalmente no la habría. Otro uso común es crear varias áreas de trabajo a las que se pueden mover o quitar elementos. Con este método, puede crear áreas en una sola vista que tengan significados diferentes. A continuación, el usuario podría categorizar los elementos colocándolos en un área diferente. Un ejemplo de esto sería una vista de un sistema de archivos que tiene un área para archivos de lectura/escritura y otra área para archivos de solo lectura. Si un elemento de archivo se moviera al área de solo lectura, se convertiría automáticamente en de solo lectura. Mover un archivo desde el área de solo lectura al área de lectura y escritura haría que el archivo leley y escriba.

`CListCtrl`proporciona varias funciones miembro para crear y administrar áreas de trabajo en el control de lista. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) y [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) recuperan `CRect` y establecen una matriz de objetos (o `RECT` estructuras), que almacenan las áreas de trabajo implementadas actualmente para el control de lista. Además, [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) recupera el número actual de áreas de trabajo para el control de lista (de forma predeterminada, cero).

## <a name="items-and-working-areas"></a>Artículos y áreas de trabajo

Cuando se crea un área de trabajo, los elementos que se encuentran dentro del área de trabajo se convierten en miembros de la misma. Del mismo modo, si un elemento se mueve a un área de trabajo, se convierte en miembro del área de trabajo a la que se movió. Si un elemento no se encuentra dentro de ningún área de trabajo, se convierte automáticamente en miembro del primer área de trabajo (índice 0). Si desea crear un elemento y colocarlo dentro de un área de trabajo específica, deberá crear el elemento y, a continuación, moverlo al área de trabajo deseada con una llamada a [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). El segundo ejemplo siguiente muestra esta técnica.

En el ejemplo siguiente se`rcWorkAreas`implementan cuatro áreas de trabajo ( ), de igual tamaño con`m_WorkAreaListCtrl`un borde de 10 píxeles de ancho alrededor de cada área de trabajo, en un control de lista ( ).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

La llamada a [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) se realizó para obtener una estimación del área total necesaria para mostrar todos los elementos en una región. Esta estimación se divide en cuatro regiones y se rellena con un borde de 5 píxeles de ancho.

En el ejemplo siguiente se asignan los`rcWorkAreas`elementos de lista`m_WorkAreaListCtrl`existentes a cada grupo ( ) y se actualiza la vista de control ( ) para completar el efecto.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
