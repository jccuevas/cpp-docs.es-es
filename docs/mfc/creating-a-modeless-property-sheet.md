---
title: "Crear una hoja de propiedades no modal | Microsoft Docs"
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
  - "Create (método) [C++], hojas de propiedades"
  - "hojas de propiedades no modales"
  - "hojas de propiedades, no modales"
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear una hoja de propiedades no modal
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Normalmente, las hojas de propiedades que cree se modales.  Al utilizar una hoja de propiedades modal, el usuario debe cerrar la hoja de propiedades antes de utilizar cualquier otra parte de la aplicación.  En este artículo se describe métodos que puede utilizar para crear una hoja de propiedades no modal que permite al usuario mantiene la hoja de propiedades abierto mientras utiliza otras partes de la aplicación.  
  
 Para mostrar una hoja de propiedades como cuadro de diálogo no modal en lugar de como cuadro de diálogo modal, llame a [CPropertySheet::Create](../Topic/CPropertySheet::Create.md) en lugar de [DoModal](../Topic/CPropertySheet::DoModal.md).  También debe implementar algunas tareas adicionales para admitir una hoja de propiedades no modal.  
  
 Una de las tareas adicionales está intercambiando datos entre la hoja de propiedades y el objeto externo que se está modificando cuando la hoja de propiedades está abierto.  Suele ser la misma tarea que para los cuadros de diálogo no modal estándar.  La parte de esta tarea implementando un canal de comunicación entre la hoja de propiedades no modal y el objeto externo a los que los valores de propiedades se aplican.  Esta implementación es mucho más fácil si se deriva una clase de [CPropertySheet](../mfc/reference/cpropertysheet-class.md) de la hoja de propiedades no modal.  En este artículo se supone que se ha hecho en.  
  
 Un método para la comunicación entre la hoja de propiedades no modal y el objeto externo \(la selección actual en una vista, por ejemplo\) es definir un puntero de la hoja de propiedades al objeto externo.  Defina una función \(denominada algo como `SetMyExternalObject`\) en `CPropertySheet`\- clase derivada para cambiar el puntero siempre que el foco cambia de un objeto externo a otro.  La función de `SetMyExternalObject` necesita restaurar los valores para cada página de propiedades refleje el objeto externo recientemente seleccionado.  Para ello, la función de `SetMyExternalObject` debe poder tener acceso a los objetos de [CPropertyPage](../mfc/reference/cpropertypage-class.md) que pertenecen a la clase de `CPropertySheet` .  
  
 La manera más conveniente de proporcionar acceso a las páginas de propiedades dentro de una hoja de propiedades es insertar los objetos de `CPropertySheet`\- objeto derivado de `CPropertyPage` .  Objetos de `CPropertyPage` de incrustación en `CPropertySheet`\- el objeto derivado diferencia de diseño típico de los cuadros de diálogo modales, donde el propietario de la hoja de propiedades crea los objetos de `CPropertyPage` y los pasa a la hoja de propiedades mediante [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md).  
  
 Hay muchas alternativas de interfaz de usuario para determinar cuando los valores de la hoja de propiedades no modal se deben aplicar a un objeto externo.  Una alternativa consiste en aplicar los valores de la página de propiedades actual siempre que el usuario cambie cualquier valor.  Otra alternativa es proporcionar un botón de aplicar, que permite al usuario acumula cambios en las páginas de propiedades antes de confiarlas el objeto externo.  Para obtener información sobre maneras de controlar el botón de aplicar, vea el artículo [Administrar el botón apply](../mfc/handling-the-apply-button.md).  
  
## Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)   
 [Intercambiar datos](../mfc/exchanging-data.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)