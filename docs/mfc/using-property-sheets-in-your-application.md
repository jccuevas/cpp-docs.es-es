---
title: Usar hojas de propiedades en una aplicación
ms.date: 11/04/2016
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
ms.openlocfilehash: 76acbfa9625fe6cb9a575244b0ed6954eeaaf3f2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301693"
---
# <a name="using-property-sheets-in-your-application"></a>Usar hojas de propiedades en una aplicación

Para utilizar una hoja de propiedades en la aplicación, complete los pasos siguientes:

1. Crear un recurso de plantilla de cuadro de diálogo para cada página de propiedades. Tenga en cuenta que el usuario se puede cambiar de una página a otra, por lo que disponer de cada página de un modo tan coherente como sea posible.

   Las plantillas de cuadro de diálogo para todas las páginas no tiene que ser del mismo tamaño. El marco de trabajo usa el tamaño de la página más grande para determinar cuánto espacio asignar en la hoja de propiedades para las páginas de propiedades.

   Cuando se crea el recurso de plantilla de cuadro de diálogo para una página de propiedades, debe especificar los estilos siguientes en la hoja Propiedades de cuadro de diálogo:

   - Establecer el **título** cuadro de edición en el **General** página para el texto que desee que aparezca en la ficha para esta página.

   - Establecer el **estilo** cuadro de lista en el **estilos** paginar en **secundarios**.

   - Establecer el **borde** cuadro de lista en el **estilos** paginar en **Thin**.

   - Asegúrese de que el **Titlebar** casilla de verificación en la **estilos** página está seleccionada.

   - Asegúrese de que el **deshabilitado** casilla de verificación en la **más estilos** página está seleccionada.

1. Crear un [CPropertyPage](../mfc/reference/cpropertypage-class.md)-correspondiente a cada plantilla de cuadro de diálogo página de propiedades de clase derivada. Consulte [agregar una clase](../ide/adding-a-class-visual-cpp.md). Elija `CPropertyPage` como clase base.

1. Cree variables para contener los valores de esta página de propiedades de miembro. El proceso para agregar variables miembro a una página de propiedades es exactamente igual que agregar variables miembro a un cuadro de diálogo, dado que una página de propiedades es un cuadro de diálogo especializado. Para obtener más información, consulte [definir Variables miembro para controles de cuadro de diálogo](../windows/defining-member-variables-for-dialog-controls.md).

1. Construir un [CPropertySheet](../mfc/reference/cpropertysheet-class.md) objeto en el código fuente. Normalmente se construye la `CPropertySheet` objeto en el controlador para el comando que muestra la hoja de propiedades. Este objeto representa la hoja de propiedades completa. Si crea una hoja de propiedades modal con el [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) función, el marco de trabajo proporciona tres botones de comando de forma predeterminada: Aceptar, Cancelar y aplicar. El marco de trabajo no crea ningún botón de comando para hojas de propiedades no modal crean con el [crear](../mfc/reference/cpropertysheet-class.md#create) función. No es necesario derivar una clase de `CPropertySheet` a menos que desee agregar otros controles (por ejemplo, una ventana de vista previa) o mostrar una hoja de propiedades no modal. Este paso es necesario para las hojas de propiedades no modal porque no contienen ningún control predeterminado que podría utilizarse para cerrar la hoja de propiedades.

1. Para que cada página que se agregarán a la hoja de propiedades, haga lo siguiente:

   - Construir un objeto para cada `CPropertyPage`-clase derivada que creó anteriormente en este proceso.

   - Llame a [CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage) para cada página.

   Normalmente, el objeto que crea el `CPropertySheet` también crea el `CPropertyPage` objetos en este paso. Sin embargo, si implementa un `CPropertySheet`-clase derivada, se puede incrustar el `CPropertyPage` objetos en el `CPropertySheet` objeto y llamar a `AddPage` para cada página de la `CPropertySheet`-derivados de constructor de clase. `AddPage` Agrega el `CPropertyPage` objeto a la lista de la hoja de propiedades de las páginas, pero no crea realmente la ventana para esa página. Por lo tanto, no es necesario esperar a la creación de la ventana de la hoja de propiedades para llamar a `AddPage`; se puede llamar a `AddPage` desde el constructor de la hoja de propiedades.

   De forma predeterminada, si una hoja de propiedades tiene varias pestañas que caben en una sola fila de la hoja de propiedades, las pestañas se apilarán en varias filas. Para deshabilitar el apilamiento, llame a [CPropertySheet:: EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) con el parámetro establecido en **FALSE**. Debe llamar a `EnableStackedTabs` cuando se crea la hoja de propiedades.

1. Llame a [CPropertySheet:: DoModal](../mfc/reference/cpropertysheet-class.md#domodal) o [crear](../mfc/reference/cpropertysheet-class.md#create) para mostrar la hoja de propiedades. Llame a `DoModal` para crear una hoja de propiedades como un cuadro de diálogo modal. Llame a **crear** para crear la hoja de propiedades como un cuadro de diálogo no modal.

1. Intercambiar datos entre páginas de propiedades y el propietario de la hoja de propiedades. Esto se explica en el artículo [intercambiar datos](../mfc/exchanging-data.md).

Para obtener un ejemplo de cómo usar las hojas de propiedades, vea el ejemplo General de MFC [PROPDLG](../visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)
