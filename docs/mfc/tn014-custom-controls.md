---
title: "TN014: Controles personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles personalizados [MFC]"
  - "TN014"
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# TN014: Controles personalizados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe la compatibilidad de MFC con los controles personalizados y de uno mismo\- gráfico.  También describe crear subclases dinámico, y describe la relación entre los objetos de [CWnd](../mfc/reference/cwnd-class.md) y s para `HWND`.  
  
 La aplicación de ejemplo CTRLTEST MFC muestra cómo utilizar muchos controles personalizados.  Vea el código fuente del ejemplo [CTRLTEST](../top/visual-cpp-samples.md) MFC General y la ayuda en línea.  
  
## Controles y menús de Propietario\- dibujo  
 Windows proporciona compatibilidad para controles y menús de propietario\- dibujo mediante los mensajes de Windows.  La ventana primaria de cualquier control o menú recibe estos mensajes y las llamadas funcionan en respuesta.  Puede reemplazar estas funciones para personalizar el aspecto visual y el comportamiento de control o de menú de propietario\- dibujo.  
  
 MFC admite directamente propietario\-dibujo con las funciones siguientes:  
  
-   [CWnd::OnDrawItem](../Topic/CWnd::OnDrawItem.md)  
  
-   [CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)  
  
-   [CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)  
  
-   [CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)  
  
 Puede reemplazar estas funciones en la clase derivada de `CWnd` para implementar el comportamiento personalizado de dibujo.  
  
 Este enfoque no lleva al código reutilizable.  Si tiene dos controles similares en dos clases diferentes de `CWnd` , debe implementar el comportamiento de control personalizado en dos ubicaciones.  La arquitectura MFC\- compatible del control de uno mismo\- gráfico resuelve este problema.  
  
## Controles y menús de Uno mismo\- dibujo  
 MFC proporciona una implementación predeterminada \(en las clases de `CWnd` y de [CMenu](../mfc/reference/cmenu-class.md) \) para los mensajes estándar de propietario\- dibujo.  Esta implementación predeterminada descodificará los parámetros de propietario\- dibujo y delegará los mensajes de propietario\- dibujo a los controles o el menú.  Esto se denomina uno mismo\- dibujo porque el código del gráfico está en la clase de control o de menú, no en la ventana propietaria.  
  
 Mediante los controles de uno mismo\- dibujo puede compilar las clases reutilizables de control que usan semántica de propietario\- dibujo para mostrar el control.  El código para dibujar el control está en la clase de control, no su elemento primario.  Esto es un enfoque basado en la programación de control personalizado.  Agregue la siguiente lista de funciones a las clases de uno mismo\- dibujo:  
  
-   Para los botones de uno mismo\- dibujo:  
  
    ```  
    CButton:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw this button  
    ```  
  
-   Para los menús de uno mismo\- dibujo:  
  
    ```  
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this menu  
    CMenu:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this menu  
    ```  
  
-   Para los cuadros de lista de uno mismo\- dibujo:  
  
    ```  
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this list box  
    CListBox:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this list box  
  
    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);  
            // insert code to compare two items in this list box if LBS_SORT  
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);  
            // insert code to delete an item from this list box  
    ```  
  
-   Para cuadros combinados de uno mismo\- dibujo:  
  
    ```  
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);  
            // insert code to measure the size of an item in this combo box  
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);  
            // insert code to draw an item in this combo box  
  
    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);  
            // insert code to compare two items in this combo box if CBS_SORT  
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);  
            // insert code to delete an item from this combo box  
    ```  
  
 Para obtener información sobre las estructuras de propietario\- dibujo \([DRAWITEMSTRUCT](../mfc/reference/drawitemstruct-structure.md), [MEASUREITEMSTRUCT](../mfc/reference/measureitemstruct-structure.md), [COMPAREITEMSTRUCT](../mfc/reference/compareitemstruct-structure.md), y [DELETEITEMSTRUCT](../mfc/reference/deleteitemstruct-structure.md)\) vea la documentación de MFC para `CWnd::OnDrawItem`, `CWnd::OnMeasureItem`, `CWnd::OnCompareItem`, y `CWnd::OnDeleteItem` respectivamente.  
  
## Mediante los controles y menús de uno mismo\- dibujo  
 Para los menús de uno mismo\- dibujo, debe invalidar los métodos de `OnMeasureItem` y de `OnDrawItem` .  
  
 Para los cuadros de lista y cuadros combinados de uno mismo\- dibujo, debe invalidar `OnMeasureItem` y `OnDrawItem`.  Debe especificar el estilo de `LBS_OWNERDRAWVARIABLE` para los cuadros de lista o el estilo de `CBS_OWNERDRAWVARIABLE` para cuadros combinados en la plantilla de cuadro de diálogo.  El estilo de `OWNERDRAWFIXED` no funcionará con los elementos de un mismo\- dibujo porque se determina el alto fijo de elemento antes de que los controles de un mismo\- dibujo están asociados al cuadro de lista. \(Puede utilizar los métodos [CListBox::SetItemHeight](../Topic/CListBox::SetItemHeight.md) y [CComboBox::SetItemHeight](../Topic/CComboBox::SetItemHeight.md) para superar esta limitación.\)  
  
 Conmutación a un estilo de `OWNERDRAWVARIABLE` también el sistema para aplicar el estilo de `NOINTEGRALHEIGHT` al control.  Dado que el control no puede calcular un alto entero con variable \(se omiten los elementos ordenados, el estilo predeterminado de `INTEGRALHEIGHT` y el control siempre es `NOINTEGRALHEIGHT`.  Si los elementos son de altitud fija, puede evitar que los elementos parciales están dibujados especificando el tamaño del control para ser un multiplicador entero del tamaño del elemento.  
  
 Para los cuadros de lista y cuadros combinados de uno mismo\- gráfico con el estilo de `LBS_SORT` o de `CBS_SORT` , debe reemplazar el método de `OnCompareItem` .  
  
 Para los cuadros de lista y cuadros combinados de uno mismo\- gráfico, `OnDeleteItem` no se invalida normalmente.  Puede reemplazar `OnDeleteItem` si desea realizar algún procesamiento especial.  Un caso donde es aplicable es cuando almacenan memoria adicional u otros recursos con cada elemento del cuadro de lista o de cuadro combinado.  
  
## Ejemplos de Controles y de los menús de self \- Drawing  
 El ejemplo [CTRLTEST](../top/visual-cpp-samples.md) MFC General proporciona ejemplos de un menú de uno mismo\- dibujo y un cuadro de lista de uno mismo\- dibujo.  
  
 El ejemplo más común de un botón de uno mismo\- gráfico es un botón bitmap.  Un botón bitmap es un botón que muestra una, dos, o tres imágenes de mapa de bits para distintos estados.  Un ejemplo de ello se proporciona en la clase MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).  
  
## El crear subclases dinámico  
 Deseará en ocasiones para cambiar la funcionalidad de un objeto que ya existe.  Los ejemplos anteriores se requieren personalizar controles antes de que se crearon mediante.  El crear subclases dinámicos permiten personalizar un control que se ha creado.  
  
 El crear subclases es el término de Windows para reemplazar [WndProc](http://msdn.microsoft.com/es-es/94ba8ffa-3c36-46d4-ac74-9bd10b1ffd26) de una ventana con `WndProc` personalizado y llamar a `WndProc` anterior para la funcionalidad predeterminada.  
  
 Esto no se debe confundir con la derivación de clases de C\+\+.  Para la aclaración, los términos *clase base* de C\+\+ y *la clase derivada* son análogos *crear superclase* y *crear subclases* del modelo de objetos de Windows.  La derivación de C\+\+ con MFC y crear subclases de Windows es funcionalmente similar, a menos que C\+\+ no admite crear subclases dinámico.  
  
 La clase de `CWnd` proporciona la conexión entre el objeto en cuestión. \(derivado de `CWnd`\) y un objeto de la ventana de Windows \(conocido como `HWND`\).  
  
 Hay tres formas comunes que son relacionados:  
  
-   `CWnd` crea `HWND`.  Puede modificar el comportamiento en una clase derivada creando una clase derivada de `CWnd`.  Se crea `HWND` cuando la aplicación llama [CWnd::Create](../Topic/CWnd::Create.md).  
  
-   La aplicación asocia `CWnd` a `HWND`existente.  El comportamiento de la ventana existente no se modifica.  Éste es un caso de delegación y crea posible llamando a [CWnd::Attach](../Topic/CWnd::Attach.md) a alias `HWND` existente a un objeto de `CWnd` .  
  
-   `CWnd` se adjunta a `HWND` existente y puede modificar el comportamiento en una clase derivada.  Esto se denomina el crear subclases dinámico porque estamos cambiando el comportamiento y, por tanto la clase, un objeto de Windows en tiempo de ejecución.  
  
 Puede lograr crear subclases dinámico mediante los métodos [CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md) y[CWnd::SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md).  
  
 Ambas rutinas asocian un objeto de `CWnd` a `HWND`existente.  `SubclassWindow` toma `HWND` directamente.  `SubclassDlgItem` es una función auxiliar que toma un identificador de control y la ventana primaria.  `SubclassDlgItem` está diseñado para asociar los objetos de C\+\+ a los controles de cuadro de diálogo creados a partir de una plantilla de cuadro de diálogo.  
  
 Vea el ejemplo de [CTRLTEST](../top/visual-cpp-samples.md) para varios ejemplos de cuándo utilizar `SubclassWindow` y `SubclassDlgItem`.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)