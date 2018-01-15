---
title: Crear una hoja de propiedades no modal | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4686caf6c414952cd86dfe0c69fcc3be8ee09af9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-modeless-property-sheet"></a>Crear una hoja de propiedades no modal
Normalmente, las hojas de propiedades que cree será modales. Cuando se utiliza una hoja de propiedades modal, el usuario debe cerrar la hoja de propiedades antes de usar cualquier otra parte de la aplicación. Este artículo describe métodos que puede usar para crear una hoja de propiedades no modal que permite al usuario mantener la hoja de propiedades abiertas durante el uso de otras partes de la aplicación.  
  
 Para mostrar una hoja de propiedades como un cuadro de diálogo no modal en lugar de como un cuadro de diálogo modal, llame a [CPropertySheet:: Create](../mfc/reference/cpropertysheet-class.md#create) en lugar de [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). También debe implementar algunas tareas adicionales para admitir una hoja de propiedades no modal.  
  
 Una de las tareas adicionales intercambia datos entre la hoja de propiedades y el objeto externo que se modifica cuando se abre la hoja de propiedades. Por lo general, suele ser la misma tarea que para los cuadros de diálogo no modales estándar. Parte de esta tarea consiste en implementar un canal de comunicación entre la hoja de propiedades no modal y el objeto externo al que se aplican los valores de propiedad. Esta implementación es mucho más fácil si se deriva una clase de [CPropertySheet](../mfc/reference/cpropertysheet-class.md) para la hoja de propiedades no modal. En este artículo se da por supuesto que lo ha hecho.  
  
 Un método para la comunicación entre la hoja de propiedades no modal y la externa es objeto (es decir, la selección actual en una vista, por ejemplo) definir un puntero desde la hoja de propiedades para el objeto externo. Definir una función (denominada algo parecido a `SetMyExternalObject`) en el `CPropertySheet`-clase derivada para cambiar el puntero siempre que cambie el foco desde un objeto externo a otro. El `SetMyExternalObject` función necesita restablecer la configuración de cada página de propiedades para reflejar el objeto externo recién seleccionado. Para lograr esto, la `SetMyExternalObject` función debe ser capaz de obtener acceso a la [CPropertyPage](../mfc/reference/cpropertypage-class.md) objetos que pertenecen a la `CPropertySheet` clase.  
  
 La manera más conveniente para proporcionar acceso a las páginas de propiedades dentro de una hoja de propiedades es incrustar el `CPropertyPage` objetos en el `CPropertySheet`-objeto derivado. Incrustar `CPropertyPage` objetos en el `CPropertySheet`-objeto derivado es distinto del diseño típico para cuadros de diálogo modales, donde se crea el propietario de la hoja de propiedades de la `CPropertyPage` objetos y los pasa a la hoja de propiedades a través de [ CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage).  
  
 Hay muchas alternativas de interfaz de usuario para determinar cuándo se debe aplicar la configuración de la hoja de propiedades no modal a un objeto externo. Una alternativa consiste en aplicar la configuración de la página de propiedades actual cuando el usuario cambia cualquier valor. Otra alternativa consiste en incluir un botón Aplicar, lo que permite al usuario acumular cambios en las páginas de propiedades antes de confirmarlos en el objeto externo. Para obtener información sobre la forma de controlar el botón Aplicar, vea el artículo [controlar el botón Aplicar](../mfc/handling-the-apply-button.md).  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)   
 [Intercambio de datos](../mfc/exchanging-data.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

