---
title: Crear una hoja de propiedades no modal
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 39285927b67091f5b8762dab56009712d806d259
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302265"
---
# <a name="creating-a-modeless-property-sheet"></a>Crear una hoja de propiedades no modal

Normalmente, las hojas de propiedades que cree será modales. Cuando se usa una hoja de propiedades modal, el usuario debe cerrar la hoja de propiedades antes de usar cualquier otra parte de la aplicación. En este artículo se describe los métodos que puede usar para crear una hoja de propiedades no modal que permite al usuario mantener la hoja de propiedades abiertas durante el uso de otras partes de la aplicación.

Para mostrar una hoja de propiedades como un cuadro de diálogo no modal en lugar de como un cuadro de diálogo modal, llame a [CPropertySheet:: Create](../mfc/reference/cpropertysheet-class.md#create) en lugar de [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). También debe implementar algunas tareas adicionales para admitir una hoja de propiedades no modal.

Una de las tareas adicionales intercambia datos entre la hoja de propiedades y el objeto externo que se modifica cuando se abre la hoja de propiedades. Esto suele ser la misma tarea en cuanto a los cuadros de diálogo no modal estándar. Parte de esta tarea consiste en implementar un canal de comunicación entre la hoja de propiedades no modal y el objeto externo al que se aplican los valores de propiedad. Esta implementación es mucho más fácil si deriva una clase de [CPropertySheet](../mfc/reference/cpropertysheet-class.md) para la hoja de propiedades no modal. En este artículo se da por supuesto que lo ha hecho.

Un método para la comunicación entre la hoja de propiedades no modal y la externa es objeto (es decir, la selección actual en una vista, por ejemplo) definir un puntero desde la hoja de propiedades para el objeto externo. Definir una función (llamado algo parecido a `SetMyExternalObject`) en el `CPropertySheet`-clase derivada para cambiar el puntero siempre que cambia el foco de un objeto externo a otro. El `SetMyExternalObject` función tenga que restablecer la configuración de cada página de propiedades para reflejar el objeto externo recién seleccionado. Para lograr esto, el `SetMyExternalObject` función debe poder tener acceso a la [CPropertyPage](../mfc/reference/cpropertypage-class.md) objetos que pertenecen a la `CPropertySheet` clase.

La manera más conveniente para proporcionar acceso a las páginas de propiedades dentro de una hoja de propiedades es incrustar el `CPropertyPage` objetos en el `CPropertySheet`-objeto derivado. Incrustación `CPropertyPage` objetos en el `CPropertySheet`-objeto derivado es distinto del diseño típico para cuadros de diálogo modales, donde se crea el propietario de la hoja de propiedades de la `CPropertyPage` objetos y los pasa a la hoja de propiedades a través de [ CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage).

Existen muchas alternativas de interfaz de usuario para determinar cuándo se debe aplicar la configuración de la hoja de propiedades no modal a un objeto externo. Una alternativa es aplicar la configuración de la página de propiedades actual cada vez que el usuario cambia cualquier valor. Otra alternativa es proporcionar un botón Aplicar, que permite al usuario que se acumulen los cambios en las páginas de propiedades antes de confirmarlos en el objeto externo. Para obtener información sobre las formas de controlar el botón Aplicar, vea el artículo [controlar el botón Aplicar](../mfc/handling-the-apply-button.md).

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)<br/>
[Intercambio de datos](../mfc/exchanging-data.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)
