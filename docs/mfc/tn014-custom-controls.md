---
title: 'TN014: Controles personalizados'
ms.date: 06/28/2018
f1_keywords:
- vc.controls
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
ms.openlocfilehash: 2960c5b8585519adb535e5611315ec4ececcf53e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511187"
---
# <a name="tn014-custom-controls"></a>TN014: Controles personalizados

En esta nota se describe la compatibilidad de MFC con los controles personalizados y de dibujo automático. También describe la subclase dinámica y describe la relación entre los objetos [CWnd](../mfc/reference/cwnd-class.md) y `HWND`s.

La aplicación de ejemplo de MFC CTRLTEST muestra cómo usar muchos controles personalizados. Vea el código fuente del ejemplo general de MFC [CTRLTEST](../overview/visual-cpp-samples.md) y la ayuda en pantalla.

## <a name="owner-draw-controlsmenus"></a>Controles o menús de dibujo propietario

Windows proporciona compatibilidad para los controles y menús de dibujo propietario mediante mensajes de Windows. La ventana primaria de cualquier control o menú recibe estos mensajes y llama a las funciones en respuesta. Puede invalidar estas funciones para personalizar la apariencia visual y el comportamiento del menú o control dibujado por el propietario.

MFC admite directamente el dibujado por el propietario con las siguientes funciones:

- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)

- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)

- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)

- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)

Puede invalidar estas funciones en la `CWnd` clase derivada para implementar el comportamiento personalizado de Draw.

Este enfoque no conduce a código reutilizable. Si tiene dos controles similares en dos clases diferentes `CWnd` , debe implementar el comportamiento del control personalizado en dos ubicaciones. La arquitectura de control de dibujo automático compatible con MFC soluciona este problema.

## <a name="self-draw-controls-and-menus"></a>Controles y menús autoextraíbles

MFC proporciona una implementación predeterminada (en las `CWnd` clases y [CMenu](../mfc/reference/cmenu-class.md) ) para los mensajes estándar de dibujo de propietario. Esta implementación predeterminada descodificará los parámetros de dibujo del propietario y delegará los mensajes de dibujo del propietario en los controles o en el menú. Esto se denomina autodraw porque el código de dibujo está en la clase del control o menú, no en la ventana propietaria.

Mediante el uso de controles autoextraíbles, puede crear clases de control reutilizables que utilicen la semántica de dibujo del propietario para mostrar el control. El código para dibujar el control está en la clase de control, no en su elemento primario. Se trata de un enfoque orientado a objetos para la programación de controles personalizados. Agregue la siguiente lista de funciones a las clases autoextraíbles:

- Para botones autoextraíbles:

    ```cpp
    CButton:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw this button
    ```

- Para menús autoextraíbles:

    ```cpp
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this menu
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this menu
    ```

- Para los cuadros de lista autoextraíbles:

    ```cpp
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this list box
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this list box

    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this list box if LBS_SORT
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this list box
    ```

- Para los cuadros combinados autodibujados:

    ```cpp
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this combo box
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this combo box

    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this combo box if CBS_SORT
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this combo box
    ```

Para obtener más información sobre las estructuras de dibujo del propietario ([drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct), [measureitemstruct (](/windows/win32/api/winuser/ns-winuser-measureitemstruct), [compareitemstruct (](/windows/win32/api/winuser/ns-winuser-compareitemstruct)y [deleteitemstruct (](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)), vea la `CWnd::OnDrawItem`documentación `CWnd::OnMeasureItem`de `CWnd::OnCompareItem`MFC para,, y .`CWnd::OnDeleteItem` respectivamente.

## <a name="using-self-draw-controls-and-menus"></a>Usar controles y menús de autodibujo

En el caso de los menús autoextraíbles, debe `OnMeasureItem` invalidar los métodos y `OnDrawItem` .

En el caso de los cuadros de lista y los cuadros combinados, `OnMeasureItem` debe `OnDrawItem`invalidar y. Debe especificar el estilo LBS_OWNERDRAWVARIABLE para los cuadros de lista o el estilo CBS_OWNERDRAWVARIABLE para los cuadros combinados en la plantilla de cuadro de diálogo. El estilo OWNERDRAWFIXED no funcionará con los elementos autoextraíbles, ya que el alto del elemento fijo se determina antes de que los controles autoextraíbles se adjunten al cuadro de lista. (Puede usar los métodos [CListBox:: SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) y [CComboBox:: SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) para superar esta limitación).

Al cambiar a un estilo OWNERDRAWVARIABLE, se obliga al sistema a aplicar el estilo NOINTEGRALHEIGHT al control. Dado que el control no puede calcular un alto entero con elementos de tamaño variable, se omite el estilo predeterminado de INTEGRALHEIGHT y el control siempre es NOINTEGRALHEIGHT. Si los elementos tienen un alto fijo, puede evitar que se dibujen elementos parciales especificando el tamaño del control para que sea un multiplicador entero del tamaño del elemento.

En el caso de los cuadros de lista y los cuadros combinados con el estilo LBS_SORT o CBS_SORT, debe `OnCompareItem` invalidar el método.

En el caso de los cuadros de lista y los `OnDeleteItem` cuadros combinados de dibujo propio, no se suele invalidar. Puede invalidar `OnDeleteItem` si desea realizar algún procesamiento especial. Un caso en el que esto sería aplicable es cuando se almacena memoria adicional u otros recursos con cada elemento de cuadro combinado o cuadro de lista.

## <a name="examples-of-self-drawing-controls-and-menus"></a>Ejemplos de controles y menús de dibujo propio

En el ejemplo de [ejemplo general](../overview/visual-cpp-samples.md) de MFC se proporcionan ejemplos de un menú autoextraíble y un cuadro de lista de autodibujo.

El ejemplo más típico de un botón de dibujo propio es un botón de mapa de bits. Un botón de mapa de bits es un botón que muestra una, dos o tres imágenes de mapa de bits para los diferentes Estados. Un ejemplo de esto se proporciona en la clase de MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).

## <a name="dynamic-subclassing"></a>Subclase dinámica

En ocasiones, querrá cambiar la funcionalidad de un objeto que ya existe. En los ejemplos anteriores se necesitaba personalizar los controles antes de que se crearan. La creación de subclases dinámicas le permite personalizar un control que ya se ha creado.

La subclase es el término de Windows para reemplazar <xref:System.Windows.Forms.Control.WndProc%2A> el de una ventana por una `WndProc` personalizada y llamar a `WndProc` la antigua para la funcionalidad predeterminada.

Esto no se debe confundir C++ con la derivación de clases. Para aclararlo, C++ los términos *clase base* y *clase derivada* son análogos a la *superclase* y *subclase* del modelo de objetos de Windows. C++la derivación con MFC y la subclase de Windows es funcionalmente C++ similar, excepto que no admite la subclase dinámica.

La `CWnd` clase proporciona la conexión entre un C++ objeto (derivado de `CWnd`) y un objeto de ventana de `HWND`Windows (conocido como).

Existen tres formas comunes de relacionar estas:

- `CWnd`crea el `HWND`. Puede modificar el comportamiento en una clase derivada creando una clase derivada de `CWnd`. Se crea cuando la aplicación llama a [CWnd:: Create.](../mfc/reference/cwnd-class.md#create) `HWND`

- La aplicación adjunta un `CWnd` a un existente. `HWND` El comportamiento de la ventana existente no se modifica. Este es un caso de delegación y se hace posible llamando a [CWnd:: attach para asignar](../mfc/reference/cwnd-class.md#attach) un alias `HWND` a `CWnd` un objeto existente.

- `CWnd`está asociado a un existente `HWND` y se puede modificar el comportamiento en una clase derivada. Esto se denomina subclase dinámica porque estamos cambiando el comportamiento y, por lo tanto, la clase de un objeto de Windows en tiempo de ejecución.

Puede lograr la subclase dinámica con los métodos [CWnd:: SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) y[CWnd:: SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).

Ambas rutinas adjuntan un `CWnd` objeto a un existente. `HWND` `SubclassWindow``HWND` toma directamente. `SubclassDlgItem`es una función auxiliar que toma un identificador de control y la ventana primaria. `SubclassDlgItem`está diseñado para adjuntar C++ objetos a los controles de cuadro de diálogo creados a partir de una plantilla de cuadro de diálogo.

Vea el ejemplo de [CTRLTEST](../overview/visual-cpp-samples.md) para ver varios ejemplos de Cuándo `SubclassWindow` usar `SubclassDlgItem`y.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
