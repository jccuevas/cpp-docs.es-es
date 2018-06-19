---
title: 'TN014: Controles personalizados | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls
dev_langs:
- C++
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54a7ef7f6fd9a9da92c208366ee401d55d07fd5a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384587"
---
# <a name="tn014-custom-controls"></a>TN014: Controles personalizados
Esta nota describe la compatibilidad de MFC para controles personalizados y dibujo automático. También describe subclases dinámica y describe la relación entre [CWnd](../mfc/reference/cwnd-class.md) objetos y `HWND`s.  
  
 La aplicación de ejemplo MFC CTRLTEST ilustra cómo utilizar muchos controles personalizados. Vea el código fuente para el ejemplo General de MFC [CTRLTEST](../visual-cpp-samples.md) y ayuda en pantalla.  
  
## <a name="owner-draw-controlsmenus"></a>Dibujado por el propietario o menús de controles  
 Windows proporciona compatibilidad para los controles de dibujado por el propietario y los menús mediante el uso de mensajes de Windows. La ventana primaria de cualquier menú o control recibe estos mensajes y llamadas a funciones como respuesta. Puede invalidar estas funciones para personalizar la apariencia visual y el comportamiento del menú o control dibujado por el propietario.  
  
 MFC admite directamente dibujado por el propietario con las siguientes funciones:  
  
- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)  
  
- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)  
  
- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)  
  
- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)  
  
 Puede invalidar estas funciones en su `CWnd` clase derivada para implementar el comportamiento de dibujo personalizado.  
  
 Este enfoque no da lugar a código reutilizable. Si tiene dos controles similares en diferentes `CWnd` clases, debe implementar el comportamiento del control personalizado en dos ubicaciones. La arquitectura de control de dibujo automático compatible con MFC soluciona este problema.  
  
## <a name="self-draw-controls-and-menus"></a>Dibujar los controles y menús  
 MFC proporciona una implementación predeterminada (en la `CWnd` y [CMenu](../mfc/reference/cmenu-class.md) clases) para los mensajes estándar dibujado por el propietario. Esta implementación predeterminada se descodificar los parámetros dibujado por el propietario y los mensajes de dibujado por el propietario para los controles o el menú de delegado. Esto se denomina dibujar automáticamente porque es el código de dibujo de la clase del control o el menú, no en la ventana propietaria.  
  
 Mediante dibujar los controles pueden generar clases de control reutilizables que utilizan la semántica de dibujado por el propietario para mostrar el control. El código para dibujar el control está en la clase de control, no su elemento primario. Se trata de un enfoque orientado a objetos a la programación del control personalizado. Agregue la siguiente lista de funciones a las clases de dibujar automáticamente:  
  
-   Para dibujar los botones:  
  
 ```  
    CButton:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw this button  
 ```  
  
-   Para dibujar los menús:  
  
 ```  
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this menu  
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this menu  
 ```  
  
-   Dibujar automáticamente para cuadros de lista:  
  
 ```  
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this list box  
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this list box  
 
    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this list box if LBS_SORT  
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this list box  
 ```  
  
-   Para los cuadros combinados dibujar automáticamente:  
  
 ```  
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
*// insert code to measure the size of an item in this combo box  
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
*// insert code to draw an item in this combo box  
 
    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
*// insert code to compare two items in this combo box if CBS_SORT  
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
*// insert code to delete an item from this combo box  
 ```  
  
 Para obtener más información sobre las estructuras de dibujado por el propietario ([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md), [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md), [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md), y [DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md)) consulte la documentación de MFC de `CWnd::OnDrawItem`, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`, y `CWnd::OnDeleteItem` respectivamente.  
  
## <a name="using-self-draw-controls-and-menus"></a>Utilizar menús y dibujar los controles  
 Para dibujar los menús, debe invalidar el `OnMeasureItem` y `OnDrawItem` métodos.  
  
 Para cuadros de lista automática dibujar y cuadros combinados, debe invalidar `OnMeasureItem` y `OnDrawItem`. Debe especificar el `LBS_OWNERDRAWVARIABLE` estilos para los cuadros de lista o `CBS_OWNERDRAWVARIABLE` cuadros de estilo para combinado de la plantilla de cuadro de diálogo. El `OWNERDRAWFIXED` estilo no funcionará con los elementos de dibujar automáticamente porque antes de dibujar los controles se adjuntan al cuadro de lista, se determina el alto del elemento fijo. (Puede usar los métodos [CListBox::SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) y [CComboBox::SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) para superar esta limitación.)  
  
 Cambiar a una `OWNERDRAWVARIABLE` estilo, forzará el sistema para aplicar el `NOINTEGRALHEIGHT` estilos al control. Dado que el control no puede calcular el alto de un entero con un tamaño de variable de elementos, el estilo predeterminado de `INTEGRALHEIGHT` se omite y el control es siempre `NOINTEGRALHEIGHT`. Si los elementos son fijos alto, puede impedir que parte de los elementos que se va a dibujar especificando el tamaño del control para que sea un multiplicador de entero del tamaño del elemento.  
  
 Para dibujar los cuadros de lista y cuadros combinados con el `LBS_SORT` o `CBS_SORT` estilo, es necesario reemplazar el `OnCompareItem` método.  
  
 Para dibujar los cuadros de lista y cuadros combinados, `OnDeleteItem` no se suele reemplazar. Puede invalidar `OnDeleteItem` si desea realizar cualquier procesamiento especial. Un caso donde esto sería aplicable resulta más memoria u otros recursos se almacenan con cada elemento de cuadro combinado o cuadro de lista.  
  
## <a name="examples-of-self-drawing-controls-and-menus"></a>Ejemplos de dibujar los controles y menús  
 El ejemplo General de MFC [CTRLTEST](../visual-cpp-samples.md) se proporcionan ejemplos de un menú dibujar automáticamente y un cuadro de lista dibujar automáticamente.  
  
 El ejemplo más habitual de un botón de dibujo automático es un botón de mapa de bits. Un botón de mapa de bits es un botón que muestra uno, dos o tres imágenes de mapa de bits para los diferentes Estados. Se proporciona un ejemplo de esto en la clase MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).  
  
## <a name="dynamic-subclassing"></a>Crear subclases de una dinámica  
 En ocasiones, deseará cambiar la funcionalidad de un objeto que ya existe. Los ejemplos anteriores requerían que permite personalizar los controles antes de que se creen. Crear subclases de una dinámica le permite personalizar un control que ya se ha creado.  
  
 Subclases es el término de Windows para reemplazar el [/ / WndProc](http://msdn.microsoft.com/en-us/94ba8ffa-3c36-46d4-ac74-9bd10b1ffd26) de una ventana con una personalizada `WndProc` y llamar a la antigua `WndProc` para la funcionalidad de forma predeterminada.  
  
 No debe confundirse con la derivación de la clase de C++. Para una aclaración de los términos de C++ *clase base* y *clase derivada* son análogos a *superclase* y *subclase* en las ventanas modelo de objetos. Derivación de C++ con MFC y Windows subclases son funcionalmente similares, salvo C++ no admite la creación de subclases dinámica.  
  
 El `CWnd` clase proporciona la conexión entre un objeto de C++ (derivado de `CWnd`) y un objeto de ventana de Windows (conocido como un `HWND`).  
  
 Hay tres formas comunes de estos están relacionados con:  
  
- `CWnd` crea el `HWND`. También puede modificar el comportamiento en una clase derivada mediante la creación de una clase derivada de `CWnd`. El `HWND` se crea cuando la aplicación llama a [CWnd:: Create](../mfc/reference/cwnd-class.md#create).  
  
-   La aplicación asocia un `CWnd` a un archivo `HWND`. No se modifica el comportamiento de la ventana existente. Esto es un caso de delegación y se realiza mediante una llamada a [CWnd::Attach](../mfc/reference/cwnd-class.md#attach) a alias existente `HWND` a una `CWnd` objeto.  
  
- `CWnd` se adjunta a un archivo `HWND` y se puede modificar el comportamiento en una clase derivada. Esto se denomina dinámica porque se está cambiando el comportamiento y, por lo tanto, la clase de objeto de Windows en tiempo de ejecución de la creación de subclases.  
  
 Puede lograr subclases dinámica mediante los métodos [CWnd:: SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) y[CWnd:: SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).  
  
 Las rutinas de adjuntar un `CWnd` objeto a un archivo `HWND`. `SubclassWindow` toma el `HWND` directamente. `SubclassDlgItem` es una función auxiliar que toma un identificador de control y la ventana primaria. `SubclassDlgItem` está diseñado para asociar objetos de C++ a los controles de cuadro de diálogo creados a partir de una plantilla de cuadro de diálogo.  
  
 Consulte la [CTRLTEST](../visual-cpp-samples.md) ejemplo para ver varios ejemplos de cuándo usar `SubclassWindow` y `SubclassDlgItem`.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

