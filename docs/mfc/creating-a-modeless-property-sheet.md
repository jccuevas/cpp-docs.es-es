---
title: Crear una hoja de propiedades no modal
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 7a44d96adf0a25a401fbc2e561bd7d32758a37d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617167"
---
# <a name="creating-a-modeless-property-sheet"></a>Crear una hoja de propiedades no modal

Normalmente, las hojas de propiedades que se crean serán modales. Al usar una hoja de propiedades modal, el usuario debe cerrar la hoja de propiedades antes de usar cualquier otra parte de la aplicación. En este artículo se describen los métodos que puede usar para crear una hoja de propiedades no modal que permita al usuario mantener abierta la hoja de propiedades mientras usa otras partes de la aplicación.

Para mostrar una hoja de propiedades como un cuadro de diálogo no modal en lugar de como un cuadro de diálogo modal, llame a [CPropertySheet:: Create](reference/cpropertysheet-class.md#create) en lugar de a [DoModal](reference/cpropertysheet-class.md#domodal). También debe implementar algunas tareas adicionales para admitir una hoja de propiedades no modal.

Una de las tareas adicionales es intercambiar datos entre la hoja de propiedades y el objeto externo que está modificando cuando la hoja de propiedades está abierta. Normalmente, se trata de la misma tarea que en los cuadros de diálogo no modales estándar. Parte de esta tarea está implementando un canal de comunicación entre la hoja de propiedades no modal y el objeto externo al que se aplican los valores de propiedad. Esta implementación es mucho más fácil si se deriva una clase de [CPropertySheet](reference/cpropertysheet-class.md) para la hoja de propiedades no modal. En este artículo se da por supuesto que lo ha hecho.

Un método para la comunicación entre la hoja de propiedades no modal y el objeto externo (por ejemplo, la selección actual en una vista) es definir un puntero desde la hoja de propiedades hasta el objeto externo. Defina una función (denominada algo similar `SetMyExternalObject` ) en la `CPropertySheet` clase derivada de para cambiar el puntero cada vez que el foco cambie de un objeto externo a otro. La `SetMyExternalObject` función debe restablecer la configuración de cada página de propiedades para reflejar el objeto externo recién seleccionado. Para ello, la `SetMyExternalObject` función debe poder tener acceso a los objetos [CPropertyPage](reference/cpropertypage-class.md) que pertenecen a la `CPropertySheet` clase.

La manera más cómoda de proporcionar acceso a las páginas de propiedades dentro de una hoja de propiedades es insertar los `CPropertyPage` objetos en el `CPropertySheet` objeto derivado de. La incrustación de `CPropertyPage` objetos en el `CPropertySheet` objeto derivado de difiere del diseño típico de los cuadros de diálogo modales, donde el propietario de la hoja de propiedades crea los `CPropertyPage` objetos y los pasa a la hoja de propiedades mediante [CPropertySheet:: AddPage](reference/cpropertysheet-class.md#addpage).

Hay muchas alternativas de interfaz de usuario para determinar cuándo se debe aplicar la configuración de la hoja de propiedades no modal a un objeto externo. Una alternativa consiste en aplicar la configuración de la página de propiedades actual cada vez que el usuario cambie cualquier valor. Otra alternativa consiste en proporcionar un botón aplicar, que permite al usuario acumular los cambios en las páginas de propiedades antes de confirmarlos en el objeto externo. Para obtener información sobre cómo controlar el botón aplicar, consulte el artículo [controlar el botón aplicar](handling-the-apply-button.md).

## <a name="see-also"></a>Consulte también

[Hojas de propiedades](property-sheets-mfc.md)<br/>
[Intercambiar datos](exchanging-data.md)<br/>
[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)
