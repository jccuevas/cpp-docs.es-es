---
title: 'TN014: Controles personalizados'
ms.date: 06/28/2018
f1_keywords:
- vc.controls
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
ms.openlocfilehash: 1f04029e47ee7d262cdc5e2eab463799acd7d943
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178413"
---
# <a name="tn014-custom-controls"></a>TN014: Controles personalizados

Esta nota describe la compatibilidad de MFC para controles personalizados y dibujo automático. También describe la creación de subclases dinámica y describe la relación entre [CWnd](../mfc/reference/cwnd-class.md) objetos y `HWND`s.

La aplicación de ejemplo MFC CTRLTEST ilustra cómo usar muchos controles personalizados. Vea el código fuente para el ejemplo General de MFC [CTRLTEST](../visual-cpp-samples.md) y ayuda en línea.

## <a name="owner-draw-controlsmenus"></a>Controles dibujados por el propietario o los menús

Windows proporciona compatibilidad para controles dibujados por el propietario y los menús mediante el uso de los mensajes de Windows. La ventana primaria de cualquier control o menú recibe estos mensajes y llamadas a funciones en la respuesta. Puede invalidar estas funciones para personalizar la apariencia visual y el comportamiento del menú o control dibujado por el propietario.

MFC admite directamente dibujados con las siguientes funciones:

- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)

- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)

- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)

- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)

Puede invalidar estas funciones en su `CWnd` clase derivada para implementar el comportamiento de dibujo personalizado.

Este enfoque no da lugar a código reutilizable. Si tiene dos controles similares en dos diferentes `CWnd` clases, debe implementar el comportamiento de control personalizado en dos ubicaciones. La arquitectura de control de dibujo automático compatible con MFC soluciona este problema.

## <a name="self-draw-controls-and-menus"></a>Dibujar los controles y menús

MFC proporciona una implementación predeterminada (en el `CWnd` y [CMenu](../mfc/reference/cmenu-class.md) clases) para los mensajes estándar dibujado por el propietario. Esta implementación predeterminada se descodificar los parámetros dibujado por el propietario y delegar los mensajes dibujado por el propietario para los controles o el menú. Esto se denomina dibujar automáticamente porque es el código de dibujo en la clase del control o menú, no en la ventana propietaria.

Mediante el uso de dibujar los controles puede generar las clases de control reutilizables que utilizan la semántica de dibujado por el propietario para mostrar el control. El código para dibujar el control está en la clase de control, no su elemento primario. Se trata de un enfoque orientado a la programación de control personalizado. Agregue la siguiente lista de funciones a las clases de dibujar automáticamente:

- Para dibujar los botones:

    ```cpp
    CButton:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw this button
    ```

- Para dibujar los menús:

    ```cpp
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this menu
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this menu
    ```

- Dibujar automáticamente para cuadros de lista:

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

- Para los cuadros combinados dibujar automáticamente:

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

Para obtener más información sobre las estructuras dibujado por el propietario ([DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct), [MEASUREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct), [COMPAREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcompareitemstruct), y [DELETEITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdeleteitemstruct)) consulte la documentación de MFC para `CWnd::OnDrawItem`, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`, y `CWnd::OnDeleteItem` respectivamente.

## <a name="using-self-draw-controls-and-menus"></a>Uso de menús y controles de dibujar automáticamente

En los menús de dibujar automáticamente, debe invalidar el `OnMeasureItem` y `OnDrawItem` métodos.

Para los cuadros de lista dibujar automáticamente y los cuadros combinados, debe invalidar `OnMeasureItem` y `OnDrawItem`. Debe especificar el estilo LBS_OWNERDRAWVARIABLE para cuadros de lista o estilo CBS_OWNERDRAWVARIABLE en los cuadros combinados en la plantilla de cuadro de diálogo. El estilo OWNERDRAWFIXED no funcionará con elementos dibujar automáticamente porque se determina el alto del elemento fijo antes de dibujar los controles se adjuntan al cuadro de lista. (Puede usar los métodos [CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) y [CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) para superar esta limitación.)

Cambiar a un estilo OWNERDRAWVARIABLE forzará el sistema para aplicar el estilo NOINTEGRALHEIGHT al control. Dado que el control no puede calcular un alto integral con elementos de tamaño variable, se ignora el estilo predeterminado de INTEGRALHEIGHT y el control siempre se NOINTEGRALHEIGHT. Si los elementos son fijos alto, puede impedir que parte de los elementos que se va a dibujar especificando el tamaño del control para que sea un multiplicador de entero del tamaño del elemento.

Para dibujar los cuadros de lista y cuadros combinados con el estilo LBS_SORT o CBS_SORT, se debe reemplazar el `OnCompareItem` método.

Para dibujar los cuadros de lista y cuadros combinados, `OnDeleteItem` normalmente no se ve invalidado. Puede invalidar `OnDeleteItem` si desea realizar ningún procesamiento especial. Un caso donde esto sería aplicable es cuando la memoria adicional u otros recursos se almacenan con cada elemento de cuadro combinado o cuadro de lista.

## <a name="examples-of-self-drawing-controls-and-menus"></a>Ejemplos de dibujo de los controles y menús

El ejemplo General de MFC [CTRLTEST](../visual-cpp-samples.md) se proporcionan ejemplos de un menú propio dibujo y un cuadro de lista dibujar automáticamente.

El ejemplo más habitual de un botón de dibujo automático es un botón de mapa de bits. Un botón de mapa de bits es un botón que muestra uno, dos o tres imágenes de mapa de bits para los distintos Estados. Se proporciona un ejemplo de esto en la clase MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).

## <a name="dynamic-subclassing"></a>Creación de subclases dinámico

En ocasiones, deseará cambiar la funcionalidad de un objeto que ya existe. Los ejemplos anteriores era necesario personalizar los controles antes de que se crearon. Creación de subclases dinámica le permite personalizar un control que ya se ha creado.

Creación de subclases es el término de Windows para reemplazar el <xref:System.Windows.Forms.Control.WndProc%2A> de una ventana con una personalizada `WndProc` y llamar a la antigua `WndProc` para la funcionalidad de forma predeterminada.

No debe confundirse con la derivación de clases de C++. Para una mayor aclaración, los términos de C++ *clase base* y *clase derivada* son análogos a *superclase* y *subclase* en el Windows modelo de objetos. Derivación de C++ con la creación de subclases MFC y Windows son funcionalmente similares, excepto C++ no admite la creación de subclases dinámico.

El `CWnd` clase proporciona la conexión entre un objeto de C++ (derivado de `CWnd`) y un objeto de ventana de Windows (conocido como un `HWND`).

Hay tres formas comunes de estos están relacionados con:

- `CWnd` crea el `HWND`. Puede modificar el comportamiento en una clase derivada mediante la creación de una clase derivada de `CWnd`. El `HWND` se crea cuando la aplicación llama a [CWnd:: Create](../mfc/reference/cwnd-class.md#create).

- Las conexiones de la aplicación un `CWnd` a un `HWND`. No se modifica el comportamiento de la ventana existente. Esto es un caso de delegación y es posible mediante una llamada a [CWnd::Attach](../mfc/reference/cwnd-class.md#attach) a alias existente `HWND` a un `CWnd` objeto.

- `CWnd` se adjunta a una existente `HWND` y se puede modificar el comportamiento en una clase derivada. Esto se denomina dinámica porque se está cambiando el comportamiento y, por lo tanto, la clase de un objeto de Windows en tiempo de ejecución de la creación de subclases.

Puede lograr subclases dinámica mediante los métodos [CWnd:: SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) y[CWnd:: SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).

Tanto las rutinas de adjuntar un `CWnd` objeto a una existente `HWND`. `SubclassWindow` toma el `HWND` directamente. `SubclassDlgItem` es una función auxiliar que toma un identificador de control y la ventana primaria. `SubclassDlgItem` está diseñado para asociar los objetos de C++ a controles de cuadro de diálogo creados a partir de una plantilla de cuadro de diálogo.

Consulte la [CTRLTEST](../visual-cpp-samples.md) ejemplo para ver varios ejemplos de cuándo usar `SubclassWindow` y `SubclassDlgItem`.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
