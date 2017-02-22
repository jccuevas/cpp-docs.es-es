---
title: "CListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListBox (clase)"
  - "cuadros de lista"
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

proporciona la funcionalidad de un cuadro de lista de Windows.  
  
## Sintaxis  
  
```  
class CListBox : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListBox::CListBox](../Topic/CListBox::CListBox.md)|Crea un objeto `CListBox`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListBox::AddString](../Topic/CListBox::AddString.md)|agrega una cadena a un cuadro de lista.|  
|[CListBox::CharToItem](../Topic/CListBox::CharToItem.md)|Reemplace para proporcionar `WM_CHAR` personalizado para los cuadros de lista dibujados por el propietario que no tienen cadenas.|  
|[CListBox::CompareItem](../Topic/CListBox::CompareItem.md)|Llamado por el marco para determinar la posición de un nuevo elemento en un cuadro de lista ordenada de dibujo propietario.|  
|[CListBox::Create](../Topic/CListBox::Create.md)|Crea el cuadro de lista de Windows y lo asocia al objeto de `CListBox` .|  
|[CListBox::DeleteItem](../Topic/CListBox::DeleteItem.md)|Llamado por el marco cuando el usuario elimina un elemento de un cuadro de lista de dibujo propietario.|  
|[CListBox::DeleteString](../Topic/CListBox::DeleteString.md)|elimina una cadena de un cuadro de lista.|  
|[CListBox::Dir](../Topic/CListBox::Dir.md)|Agregar nombres de archivo, unidades, o ambas del directorio actual a un cuadro de lista.|  
|[CListBox::DrawItem](../Topic/CListBox::DrawItem.md)|Llamado por el marco cuando un aspecto visual de los cambios de un cuadro de lista de dibujo propietario.|  
|[CListBox::FindString](../Topic/CListBox::FindString.md)|Buscar una cadena en un cuadro de lista.|  
|[CListBox::FindStringExact](../Topic/CListBox::FindStringExact.md)|Encuentra la primera cadena del cuadro de lista que coincide con una cadena especificada.|  
|[CListBox::GetAnchorIndex](../Topic/CListBox::GetAnchorIndex.md)|Recupera el índice de base cero del elemento actual de delimitación en un cuadro de lista.|  
|[CListBox::GetCaretIndex](../Topic/CListBox::GetCaretIndex.md)|Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.|  
|[CListBox::GetCount](../Topic/CListBox::GetCount.md)|devuelve el número de cadenas en un cuadro de lista.|  
|[CListBox::GetCurSel](../Topic/CListBox::GetCurSel.md)|Devuelve el índice de base cero de la cadena seleccionado actualmente en un cuadro de lista.|  
|[CListBox::GetHorizontalExtent](../Topic/CListBox::GetHorizontalExtent.md)|Devuelve el ancho en píxeles que un cuadro de lista se puede desplazarse horizontalmente.|  
|[CListBox::GetItemData](../Topic/CListBox::GetItemData.md)|Devuelve el valor de 32 bits asociado al elemento del cuadro de lista.|  
|[CListBox::GetItemDataPtr](../Topic/CListBox::GetItemDataPtr.md)|Devuelve un puntero a un elemento del cuadro de lista.|  
|[CListBox::GetItemHeight](../Topic/CListBox::GetItemHeight.md)|determina el alto de elementos en un cuadro de lista.|  
|[CListBox::GetItemRect](../Topic/CListBox::GetItemRect.md)|Devuelve el rectángulo delimitador del elemento del cuadro de lista que se muestra actualmente.|  
|[CListBox::GetListBoxInfo](../Topic/CListBox::GetListBoxInfo.md)|recupera el número de elementos por columna.|  
|[CListBox::GetLocale](../Topic/CListBox::GetLocale.md)|recupera el Id. de configuración regional para un cuadro de lista.|  
|[CListBox::GetSel](../Topic/CListBox::GetSel.md)|Devuelve el estado de selección de un elemento del cuadro de lista.|  
|[CListBox::GetSelCount](../Topic/CListBox::GetSelCount.md)|Devuelve el número de cadenas seleccionado actualmente en un cuadro de lista de selección múltiple.|  
|[CListBox::GetSelItems](../Topic/CListBox::GetSelItems.md)|Devuelve los índices de las cadenas seleccionado actualmente en un cuadro de lista.|  
|[CListBox::GetText](../Topic/CListBox::GetText.md)|Copiar un elemento del cuadro de lista de un búfer.|  
|[CListBox::GetTextLen](../Topic/CListBox::GetTextLen.md)|Devuelve la longitud en bytes de un elemento del cuadro de lista.|  
|[CListBox::GetTopIndex](../Topic/CListBox::GetTopIndex.md)|devuelve el índice de la primera cadena visible en un cuadro de lista.|  
|[CListBox::InitStorage](../Topic/CListBox::InitStorage.md)|Reserva los bloques de memoria para los elementos y las cadenas del cuadro de lista.|  
|[CListBox::InsertString](../Topic/CListBox::InsertString.md)|Inserta una cadena en una ubicación concreta en un cuadro de lista.|  
|[CListBox::ItemFromPoint](../Topic/CListBox::ItemFromPoint.md)|Devuelve el índice del elemento del cuadro de lista cercana un punto.|  
|[CListBox::MeasureItem](../Topic/CListBox::MeasureItem.md)|Llamado por el marco cuando un cuadro de lista de dibujo propietario se crea para determinar dimensiones del cuadro de lista.|  
|[CListBox::ResetContent](../Topic/CListBox::ResetContent.md)|borra todas las entradas de un cuadro de lista.|  
|[CListBox::SelectString](../Topic/CListBox::SelectString.md)|Busca y selecciona una cadena en un cuadro de lista de selección única.|  
|[CListBox::SelItemRange](../Topic/CListBox::SelItemRange.md)|Seleccione o anule la selección de un intervalo de cadenas en un cuadro de lista de selección múltiple.|  
|[CListBox::SetAnchorIndex](../Topic/CListBox::SetAnchorIndex.md)|Establece el delimitador en un cuadro de lista de selección múltiple para iniciar una selección extendida.|  
|[CListBox::SetCaretIndex](../Topic/CListBox::SetCaretIndex.md)|Establece el rectángulo de foco al elemento en el índice especificado en un cuadro de lista de selección múltiple.|  
|[CListBox::SetColumnWidth](../Topic/CListBox::SetColumnWidth.md)|Establece el ancho de columna del cuadro de lista de varias columnas.|  
|[CListBox::SetCurSel](../Topic/CListBox::SetCurSel.md)|Selecciona una cadena en el cuadro de lista.|  
|[CListBox::SetHorizontalExtent](../Topic/CListBox::SetHorizontalExtent.md)|Establece el ancho en píxeles que un cuadro de lista se puede desplazarse horizontalmente.|  
|[CListBox::SetItemData](../Topic/CListBox::SetItemData.md)|Establece el valor de 32 bits asociado al elemento del cuadro de lista.|  
|[CListBox::SetItemDataPtr](../Topic/CListBox::SetItemDataPtr.md)|Establece un puntero al elemento del cuadro de lista.|  
|[CListBox::SetItemHeight](../Topic/CListBox::SetItemHeight.md)|establece el alto de elementos en un cuadro de lista.|  
|[CListBox::SetLocale](../Topic/CListBox::SetLocale.md)|establece el Id. de configuración regional para un cuadro de lista.|  
|[CListBox::SetSel](../Topic/CListBox::SetSel.md)|Seleccione o anule la selección de un elemento de cuadro de un cuadro de lista de selección múltiple.|  
|[CListBox::SetTabStops](../Topic/CListBox::SetTabStops.md)|Establece las posiciones de la interrupción de tabulación en un cuadro de lista.|  
|[CListBox::SetTopIndex](../Topic/CListBox::SetTopIndex.md)|Establece el índice de base cero de la primera cadena visible en un cuadro de lista.|  
|[CListBox::VKeyToItem](../Topic/CListBox::VKeyToItem.md)|Reemplace para proporcionar `WM_KEYDOWN` personalizado para los cuadros de lista con el estilo de **LBS\_WANTKEYBOARDINPUT** .|  
  
## Comentarios  
 Un cuadro de lista muestra una lista de elementos, como nombres de archivo, que el usuario puede ver y seleccione.  
  
 En un cuadro de lista de selección única, el usuario puede seleccionar un solo elemento.  en un cuadro de lista de selección múltiple, un intervalo de elementos puede ser seleccionado.  Cuando el usuario selecciona un elemento, aparecerá resaltada y el cuadro de lista envía un mensaje de notificación a la ventana primaria.  
  
 Puede crear un cuadro de lista de una plantilla de cuadro de diálogo o directamente en el código.  Para hacerlo directamente, crear el objeto de `CListBox` , entonces para llamar a la función miembro de [Crear](../Topic/CListBox::Create.md) para crear el control de cuadro de lista y adjuntar de Windows en el objeto de `CListBox` .  Para utilizar un cuadro de lista en una plantilla de cuadro de diálogo, declarar una variable del cuadro de lista de la del cuadro de diálogo, después para utilizar `DDX_Control` en función de `DoDataExchange` de la del cuadro de diálogo para conectarse a la variable miembro al control.  \(esto se hace automáticamente al agregar una variable de control a la del cuadro de diálogo\).  
  
 la construcción puede ser un proceso de un solo paso en una clase derivada de `CListBox`.  Escriba un constructor para la clase derivada y llame a **Crear** dentro del constructor.  
  
 Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista al elemento primario \(normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)\), agregue una función miembro de entrada y controlador de mensajes de mapa de mensajes a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 `ON_Notification( id, memberFxn )`  
  
 donde `id` especifica el identificador de ventana secundaria del control de cuadro de lista que envía la notificación y `memberFxn` es el nombre de la función principal del miembro que ha escrito para controlar la notificación.  
  
 El prototipo de función del elemento primario es el siguiente:  
  
 `afx_msg void memberFxn( );`  
  
 A continuación se muestra una lista de entradas posibles de mapa de mensajes y una descripción de los casos en que se enviaron al elemento primario:  
  
-   El usuario de**ON\_LBN\_DBLCLK** The hacer doble clic en una cadena en un cuadro de lista.  Sólo un cuadro de lista que tiene el estilo de [LBS\_NOTIFY](../../mfc/reference/list-box-styles.md) enviará este mensaje de notificación.  
  
-   El cuadro de lista de**ON\_LBN\_ERRSPACE** no puede asignar memoria suficiente para resolver la solicitud.  
  
-   El cuadro de lista de**ON\_LBN\_KILLFOCUS** The está realizando el foco de entrada.  
  
-   La selección actual del cuadro de lista de**ON\_LBN\_SELCANCEL** The se cancela.  Este mensaje se envía cuando un cuadro de lista tiene el estilo de **LBS\_NOTIFY** .  
  
-   La selección de**ON\_LBN\_SELCHANGE** The en el cuadro de lista ha cambiado.  Esta notificación no se envía si la selección está realiza una función miembro de [CListBox:: SetCurSel](../Topic/CListBox::SetCurSel.md) .  Esta notificación se aplica solamente a un cuadro de lista con el estilo de **LBS\_NOTIFY** .  El mensaje de notificación de **LBN\_SELCHANGE** se envía para un cuadro de lista de selección múltiple siempre que el usuario presione una tecla de dirección, aunque la selección no cambia.  
  
-   El cuadro de lista de**ON\_LBN\_SETFOCUS** The está recibiendo el foco de entrada.  
  
-   **ON\_WM\_CHARTOITEM** un cuadro de lista de propietario\- dibujo que no tiene ninguna cadena recibe un mensaje de `WM_CHAR` .  
  
-   El cuadro de lista de**ON\_WM\_VKEYTOITEM** con el estilo de **LBS\_WANTKEYBOARDINPUT** recibe un mensaje de `WM_KEYDOWN` .  
  
 Si crea un objeto de `CListBox` dentro de un cuadro de diálogo \(a través de un recurso de cuadro de diálogo\), el objeto de `CListBox` automáticamente se destruye cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un objeto de `CListBox` dentro de una ventana, puede ser necesario destruir el objeto de `CListBox` .  Si crea el objeto de `CListBox` en la pila, se destruye automáticamente.  Si crea el objeto de `CListBox` en la pila mediante la función de **nuevo** , debe llamar a **cancelación** en el objeto para destruirlo cuando el usuario cierra la ventana primaria.  
  
 Si asigna cualquier memoria en el objeto de `CListBox` , reemplace `CListBox` destructor para eliminar de la asignación.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo CTRLTEST de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)