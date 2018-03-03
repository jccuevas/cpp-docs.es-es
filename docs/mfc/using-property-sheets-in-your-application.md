---
title: "Usar hojas de propiedades de la aplicación | Documentos de Microsoft"
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
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4247a40fa364774674c1c79845625df51ecd34ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-property-sheets-in-your-application"></a>Usar hojas de propiedades en una aplicación
Para utilizar una hoja de propiedades de la aplicación, complete los pasos siguientes:  
  
1.  Crear un recurso de plantilla de cuadro de diálogo para cada página de propiedades. Tenga en cuenta que el usuario se puede cambiar de una página a otra, para disponer de cada página como constantemente como sea posible.  
  
     Las plantillas de cuadro de diálogo para todas las páginas no tiene que ser del mismo tamaño. El marco de trabajo usa el tamaño de la página más grande para determinar cuánto espacio debe asignar en la hoja de propiedades para las páginas de propiedades.  
  
     Cuando se crea el recurso de plantilla de cuadro de diálogo para una página de propiedades, debe especificar los estilos siguientes en la hoja Propiedades de cuadro de diálogo:  
  
    -   Establecer el **título** cuadro de edición en el **General** página para el texto que desea que aparezca en la ficha para esta página.  
  
    -   Establecer el **estilo** cuadro de lista en el **estilos** página a **secundarios**.  
  
    -   Establecer el **borde** cuadro de lista en la **estilos** página a **fino**.  
  
    -   Asegúrese de que el **Titlebar** casilla de verificación en la **estilos** página está seleccionada.  
  
    -   Asegúrese de que el **deshabilitado** casilla de verificación en la **más estilos** página está seleccionada.  
  
2.  Crear un [CPropertyPage](../mfc/reference/cpropertypage-class.md)-correspondiente a cada plantilla de cuadro de diálogo de página de propiedades de clase derivada. Vea [agregar una clase](../ide/adding-a-class-visual-cpp.md). Elija `CPropertyPage` como la clase base.  
  
3.  Cree variables para contener los valores de esta página de propiedades de miembro. El proceso para agregar variables miembro a una página de propiedades es exactamente igual que agregar variables miembro a un cuadro de diálogo, dado que una página de propiedades es un cuadro de diálogo especializado. Para obtener más información, consulte [definir Variables miembro para los controles de cuadro de diálogo](../windows/defining-member-variables-for-dialog-controls.md).  
  
4.  Construir un [CPropertySheet](../mfc/reference/cpropertysheet-class.md) objeto en el código fuente. Normalmente se construye la `CPropertySheet` objeto en el controlador para el comando que muestra la hoja de propiedades. Este objeto representa la hoja de propiedades completa. Si crea una hoja de propiedades modal con el [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) función, el marco de trabajo proporciona tres botones de comando de forma predeterminada: Aceptar, Cancelar y aplicar. El marco de trabajo no crea ningún botón de comando de hojas de propiedades no modal crean con la [crear](../mfc/reference/cpropertysheet-class.md#create) función. No es necesario derivar una clase de `CPropertySheet` a menos que desee agregar otros controles (por ejemplo, una ventana de vista previa) o mostrar una hoja de propiedades no modal. Este paso es necesario para las hojas de propiedades no modal porque no contienen ningún control predeterminado que podría usarse para cerrar la hoja de propiedades.  
  
5.  Para que cada página que se va a agregar a la hoja de propiedades, haga lo siguiente:  
  
    -   Construir un objeto para cada `CPropertyPage`-clase derivada que creó anteriormente en este proceso.  
  
    -   Llame a [CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage) para cada página.  
  
     Normalmente, el objeto que crea la `CPropertySheet` también crea el `CPropertyPage` objetos en este paso. Sin embargo, si implementa un `CPropertySheet`-clase derivada, se puede incrustar el `CPropertyPage` objetos en el `CPropertySheet` objeto y llame al método `AddPage` para cada página de la `CPropertySheet`-derivado constructor de clase. `AddPage`Agrega el `CPropertyPage` el objeto a la lista de la hoja de propiedades de páginas, pero no crea realmente la ventana para esa página. Por lo tanto, no es necesario que espere hasta que la creación de la ventana de la hoja de propiedades para llamar a `AddPage`; puede llamar a `AddPage` desde el constructor de la hoja de propiedades.  
  
     De forma predeterminada, si una hoja de propiedades tiene más fichas que caben en una sola fila de la hoja de propiedades, las fichas se apilan en varias filas. Para deshabilitar el apilado, llame a [CPropertySheet:: EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) con el parámetro establecido en **FALSE**. Debe llamar a `EnableStackedTabs` cuando se crea la hoja de propiedades.  
  
6.  Llame a [CPropertySheet:: DoModal](../mfc/reference/cpropertysheet-class.md#domodal) o [crear](../mfc/reference/cpropertysheet-class.md#create) para mostrar la hoja de propiedades. Llame a `DoModal` para crear una hoja de propiedades como un cuadro de diálogo modal. Llame a **crear** para crear la hoja de propiedades como un cuadro de diálogo no modal.  
  
7.  Intercambiar datos entre páginas de propiedades y el propietario de la hoja de propiedades. Esto se explica en el artículo [intercambiar datos](../mfc/exchanging-data.md).  
  
 Para obtener un ejemplo de cómo utilizar las hojas de propiedades, vea el ejemplo General de MFC [PROPDLG](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)

