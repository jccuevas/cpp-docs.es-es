---
title: Crear una hoja de propiedades no modal
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 90f6dcd5659d308a4b39d6a7d5a42003fc1f2111
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685695"
---
# <a name="creating-a-modeless-property-sheet"></a>Crear una hoja de propiedades no modal

Normalmente, las hojas de propiedades que se crean serán modales. Al usar una hoja de propiedades modal, el usuario debe cerrar la hoja de propiedades antes de usar cualquier otra parte de la aplicación. En este artículo se describen los métodos que puede usar para crear una hoja de propiedades no modal que permita al usuario mantener abierta la hoja de propiedades mientras usa otras partes de la aplicación.

Para mostrar una hoja de propiedades como un cuadro de diálogo no modal en lugar de como un cuadro de diálogo modal, llame a [CPropertySheet:: Create](../mfc/reference/cpropertysheet-class.md#create) en lugar de a [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). También debe implementar algunas tareas adicionales para admitir una hoja de propiedades no modal.

Una de las tareas adicionales es intercambiar datos entre la hoja de propiedades y el objeto externo que está modificando cuando la hoja de propiedades está abierta. Normalmente, se trata de la misma tarea que en los cuadros de diálogo no modales estándar. Parte de esta tarea está implementando un canal de comunicación entre la hoja de propiedades no modal y el objeto externo al que se aplican los valores de propiedad. Esta implementación es mucho más fácil si se deriva una clase de [CPropertySheet](../mfc/reference/cpropertysheet-class.md) para la hoja de propiedades no modal. En este artículo se da por supuesto que lo ha hecho.

Un método para la comunicación entre la hoja de propiedades no modal y el objeto externo (por ejemplo, la selección actual en una vista) es definir un puntero desde la hoja de propiedades hasta el objeto externo. Defina una función (llamada algo como `SetMyExternalObject`) en la clase derivada @no__t -1 para cambiar el puntero cada vez que el foco cambie de un objeto externo a otro. La función `SetMyExternalObject` debe restablecer la configuración de cada página de propiedades para reflejar el objeto externo recién seleccionado. Para ello, la función `SetMyExternalObject` debe poder tener acceso a los objetos [CPropertyPage](../mfc/reference/cpropertypage-class.md) que pertenecen a la clase `CPropertySheet`.

La manera más cómoda de proporcionar acceso a las páginas de propiedades dentro de una hoja de propiedades es insertar los objetos `CPropertyPage` en el objeto derivado de @no__t -1. La incrustación de objetos `CPropertyPage` en el objeto derivado de @no__t -1 difiere del diseño típico de los cuadros de diálogo modales, donde el propietario de la hoja de propiedades crea los objetos `CPropertyPage` y los pasa a la hoja de propiedades a través de [CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage).

Hay muchas alternativas de interfaz de usuario para determinar cuándo se debe aplicar la configuración de la hoja de propiedades no modal a un objeto externo. Una alternativa consiste en aplicar la configuración de la página de propiedades actual cada vez que el usuario cambie cualquier valor. Otra alternativa consiste en proporcionar un botón aplicar, que permite al usuario acumular los cambios en las páginas de propiedades antes de confirmarlos en el objeto externo. Para obtener información sobre cómo controlar el botón aplicar, consulte el artículo [controlar el botón aplicar](../mfc/handling-the-apply-button.md).

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)<br/>
[Intercambio de datos](../mfc/exchanging-data.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)
