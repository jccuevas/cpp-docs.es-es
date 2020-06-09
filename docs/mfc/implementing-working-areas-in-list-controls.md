---
title: Implementar las áreas de trabajo en los controles de lista
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: abbf9dd823e13fab252b7af8f32338b0d801079b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626384"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementar las áreas de trabajo en los controles de lista

De forma predeterminada, un control de lista organiza todos los elementos en un modo de cuadrícula estándar. Sin embargo, se admite otro método, áreas de trabajo, que organiza los elementos de la lista en grupos rectangulares. Para obtener una imagen de un control de lista que implementa áreas de trabajo, vea usar controles de vista de lista en el Windows SDK.

> [!NOTE]
> Las áreas de trabajo solo están visibles cuando el control de lista está en modo de icono o icono pequeño. Sin embargo, se mantienen todas las áreas de trabajo actuales si la vista cambia al modo de informe o de lista.

Las áreas de trabajo se pueden usar para mostrar un borde vacío (a la izquierda, en la parte superior y/o a la derecha de los elementos) o hacer que se muestre una barra de desplazamiento horizontal cuando normalmente no hubiera una. Otro uso común es crear varias áreas de trabajo a las que se pueden descartar o quitar elementos. Con este método, podría crear áreas en una vista única que tiene significados diferentes. Después, el usuario podría categorizar los elementos colocándolos en un área diferente. Un ejemplo de esto sería una vista de un sistema de archivos que tiene un área para los archivos de lectura/escritura y otra para los archivos de solo lectura. Si un elemento de archivo se moviera al área de solo lectura, se convertiría automáticamente en solo lectura. Mover un archivo desde el área de solo lectura al área de lectura/escritura haría que el archivo fuera de lectura/escritura.

`CListCtrl`proporciona varias funciones miembro para crear y administrar áreas de trabajo en el control de lista. [GetWorkAreas](reference/clistctrl-class.md#getworkareas) y [SetWorkAreas](reference/clistctrl-class.md#setworkareas) recuperan y establecen una matriz de `CRect` objetos (o `RECT` estructuras) que almacenan las áreas de trabajo implementadas actualmente para el control de lista. Además, [GetNumberOfWorkAreas](reference/clistctrl-class.md#getnumberofworkareas) recupera el número actual de áreas de trabajo para el control de lista (de forma predeterminada, cero).

## <a name="items-and-working-areas"></a>Elementos y áreas de trabajo

Cuando se crea un área de trabajo, los elementos que se encuentran dentro del área de trabajo se convierten en miembros del mismo. Del mismo modo, si un elemento se mueve a un área de trabajo, se convierte en un miembro del área de trabajo al que se ha despasado. Si un elemento no se encuentra dentro de un área de trabajo, se convierte automáticamente en miembro del primer área de trabajo (índice 0). Si desea crear un elemento y colocarlo en un área de trabajo específica, deberá crear el elemento y, a continuación, moverlo al área de trabajo que desee con una llamada a [SetItemPosition](reference/clistctrl-class.md#setitemposition). En el segundo ejemplo siguiente se muestra esta técnica.

En el ejemplo siguiente se implementan cuatro áreas `rcWorkAreas` de trabajo () de igual tamaño con un borde de 10 píxeles de ancho alrededor de cada área de trabajo, en un control de lista ( `m_WorkAreaListCtrl` ).

[!code-cpp[NVC_MFCControlLadenDialog#20](codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

La llamada a [ApproximateViewRect](reference/clistctrl-class.md#approximateviewrect) se realizó para obtener una estimación del área total necesaria para mostrar todos los elementos de una región. Esta estimación se divide en cuatro regiones y se rellena con un borde de 5 píxeles de ancho.

En el ejemplo siguiente se asignan los elementos de lista existentes a cada grupo ( `rcWorkAreas` ) y se actualiza la vista de control ( `m_WorkAreaListCtrl` ) para completar el efecto.

[!code-cpp[NVC_MFCControlLadenDialog#21](codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
