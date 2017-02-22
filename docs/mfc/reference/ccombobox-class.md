---
title: "CComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComboBox (clase)"
  - "cuadros combinados, CComboBox objects"
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

proporciona la funcionalidad de un cuadro combinado de Windows.  
  
## Sintaxis  
  
```  
class CComboBox : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComboBox::CComboBox](../Topic/CComboBox::CComboBox.md)|Crea un objeto `CComboBox`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComboBox::AddString](../Topic/CComboBox::AddString.md)|Agrega una cadena al final de la lista del cuadro de lista de un cuadro combinado, o en la posición ordenada para los cuadros de lista con el estilo de **CBS\_SORT** .|  
|[CComboBox::Clear](../Topic/CComboBox::Clear.md)|Elimina \(claro\) la selección actual, si existe, en el control de edición.|  
|[CComboBox::CompareItem](../Topic/CComboBox::CompareItem.md)|Llamado por el marco para determinar la posición relativa de un nuevo elemento de un cuadro combinado propietario\- dibujado ordenados.|  
|[CComboBox::Copy](../Topic/CComboBox::Copy.md)|Copia la selección actual, si existe, en el portapapeles en el formato de **CF\_TEXT** .|  
|[CComboBox::Create](../Topic/CComboBox::Create.md)|Crea el cuadro combinado y lo asocia al objeto de `CComboBox` .|  
|[CComboBox::Cut](../Topic/CComboBox::Cut.md)|Elimina \(cortes\) la selección actual, si existe, en el control de edición y copia el texto eliminado en el portapapeles en el formato de **CF\_TEXT** .|  
|[CComboBox::DeleteItem](../Topic/CComboBox::DeleteItem.md)|Llamado por el marco cuando un elemento de lista se elimina de un cuadro combinado propietario\- dibujado.|  
|[CComboBox::DeleteString](../Topic/CComboBox::DeleteString.md)|Elimina una cadena listbox de un cuadro combinado.|  
|[CComboBox::Dir](../Topic/CComboBox::Dir.md)|Agrega una lista de nombres de archivo al cuadro de lista de un cuadro combinado.|  
|[CComboBox::DrawItem](../Topic/CComboBox::DrawItem.md)|Llamado por el marco cuando un aspecto visual de los cambios propietario\- dibujados en un cuadro combinado.|  
|[CComboBox::FindString](../Topic/CComboBox::FindString.md)|Encuentra la primera cadena que contiene el prefijo especificado en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::FindStringExact](../Topic/CComboBox::FindStringExact.md)|Encuentra la primera cadena del cuadro de lista \(en un cuadro combinado\) que coincide con la cadena especificada.|  
|[CComboBox::GetComboBoxInfo](../Topic/CComboBox::GetComboBoxInfo.md)|Información de recupera sobre el objeto de `CComboBox` .|  
|[CComboBox::GetCount](../Topic/CComboBox::GetCount.md)|Recupera el número de elementos del cuadro de lista de un cuadro combinado.|  
|[CComboBox::GetCueBanner](../Topic/CComboBox::GetCueBanner.md)|Obtiene el texto de señal que se muestra para un control de cuadro combinado.|  
|[CComboBox::GetCurSel](../Topic/CComboBox::GetCurSel.md)|Recupera el índice del elemento actualmente seleccionado, si existe, en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::GetDroppedControlRect](../Topic/CComboBox::GetDroppedControlRect.md)|Recupera las coordenadas de pantalla \(interrumpido abajo\) del cuadro de lista visible de un cuadro combinado desplegable.|  
|[CComboBox::GetDroppedState](../Topic/CComboBox::GetDroppedState.md)|Determina si el cuadro de lista del cuadro combinado desplegable está visible \(interrumpido siguiente\).|  
|[CComboBox::GetDroppedWidth](../Topic/CComboBox::GetDroppedWidth.md)|Recupera el ancho mínimo permitido por la parte del cuadro de lista desplegable de un cuadro combinado.|  
|[CComboBox::GetEditSel](../Topic/CComboBox::GetEditSel.md)|Obtiene las posiciones de caracteres inicial y final de la selección actual en el control de edición de un cuadro combinado.|  
|[CComboBox::GetExtendedUI](../Topic/CComboBox::GetExtendedUI.md)|Determina si un cuadro combinado tiene la interfaz de usuario predeterminada o la interfaz de usuario extendida.|  
|[CComboBox::GetHorizontalExtent](../Topic/CComboBox::GetHorizontalExtent.md)|Devuelve el ancho en píxeles que la parte del cuadro de lista del cuadro combinado se puede mover horizontalmente.|  
|[CComboBox::GetItemData](../Topic/CComboBox::GetItemData.md)|Recupera el valor de 32 bits aplicación\- proporcionado asociado al elemento especificado del cuadro combinado.|  
|[CComboBox::GetItemDataPtr](../Topic/CComboBox::GetItemDataPtr.md)|Recupera el puntero de 32 bits aplicación\- proporcionado asociado al elemento especificado del cuadro combinado.|  
|[CComboBox::GetItemHeight](../Topic/CComboBox::GetItemHeight.md)|Recupera el alto de los elementos de un cuadro combinado.|  
|[CComboBox::GetLBText](../Topic/CComboBox::GetLBText.md)|Obtiene una cadena listbox de un cuadro combinado.|  
|[CComboBox::GetLBTextLen](../Topic/CComboBox::GetLBTextLen.md)|obtiene la longitud de una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::GetLocale](../Topic/CComboBox::GetLocale.md)|Recupera el Id. de configuración regional de un cuadro combinado.|  
|[CComboBox::GetMinVisible](../Topic/CComboBox::GetMinVisible.md)|Obtiene el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|  
|[CComboBox::GetTopIndex](../Topic/CComboBox::GetTopIndex.md)|Devuelve el índice del primer elemento visible en la parte del cuadro de lista del cuadro combinado.|  
|[CComboBox::InitStorage](../Topic/CComboBox::InitStorage.md)|Reserva los bloques de memoria para los elementos y las cadenas de la parte del cuadro de lista del cuadro combinado.|  
|[CComboBox::InsertString](../Topic/CComboBox::InsertString.md)|inserta una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::LimitText](../Topic/CComboBox::LimitText.md)|Restringe la longitud de texto que el usuario puede escribir en el control de edición de un cuadro combinado.|  
|[CComboBox::MeasureItem](../Topic/CComboBox::MeasureItem.md)|Llamado por el marco para determinar dimensiones de cuadro combinado cuando se crea un cuadro combinado propietario\- dibujado.|  
|[CComboBox::Paste](../Topic/CComboBox::Paste.md)|Inserta los datos del portapapeles en el control de edición en la posición del cursor actual.  Se inserta los datos sólo si el portapapeles contiene datos en el formato de **CF\_TEXT** .|  
|[CComboBox::ResetContent](../Topic/CComboBox::ResetContent.md)|Quita todos los elementos de cuadro de lista y control de edición de un cuadro combinado.|  
|[CComboBox::SelectString](../Topic/CComboBox::SelectString.md)|Busca una cadena en el cuadro de lista de un cuadro combinado y, si se encuentra la cadena, se selecciona la cadena en el cuadro de lista y copie la cadena al control de edición.|  
|[CComboBox::SetCueBanner](../Topic/CComboBox::SetCueBanner.md)|Establece el texto de señal que se muestra para un control de cuadro combinado.|  
|[CComboBox::SetCurSel](../Topic/CComboBox::SetCurSel.md)|selecciona una cadena en el cuadro de lista de un cuadro combinado.|  
|[CComboBox::SetDroppedWidth](../Topic/CComboBox::SetDroppedWidth.md)|Establece el ancho mínimo permitido por la parte del cuadro de lista desplegable de un cuadro combinado.|  
|[CComboBox::SetEditSel](../Topic/CComboBox::SetEditSel.md)|Selecciona los caracteres del control de edición de un cuadro combinado.|  
|[CComboBox::SetExtendedUI](../Topic/CComboBox::SetExtendedUI.md)|Selecciona la interfaz de usuario predeterminada o la interfaz de usuario extendida para un cuadro combinado con el estilo de **CBS\_DROPDOWN** o de **CBS\_DROPDOWNLIST** .|  
|[CComboBox::SetHorizontalExtent](../Topic/CComboBox::SetHorizontalExtent.md)|Establece el ancho en píxeles que la parte del cuadro de lista del cuadro combinado se puede mover horizontalmente.|  
|[CComboBox::SetItemData](../Topic/CComboBox::SetItemData.md)|Establece el valor de 32 bits asociado al elemento especificado en un cuadro combinado.|  
|[CComboBox::SetItemDataPtr](../Topic/CComboBox::SetItemDataPtr.md)|Establece el puntero de 32 bits asociado al elemento especificado en un cuadro combinado.|  
|[CComboBox::SetItemHeight](../Topic/CComboBox::SetItemHeight.md)|Establece el alto de los elementos de un cuadro combinado o el alto de la parte del control de edición \(o texto estático\) de un cuadro combinado.|  
|[CComboBox::SetLocale](../Topic/CComboBox::SetLocale.md)|Establece el Id. de configuración regional de un cuadro combinado.|  
|[CComboBox::SetMinVisibleItems](../Topic/CComboBox::SetMinVisibleItems.md)|Establece el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|  
|[CComboBox::SetTopIndex](../Topic/CComboBox::SetTopIndex.md)|Indica a la parte del cuadro de lista del cuadro combinado que muestre el elemento con el índice especificado en la parte superior.|  
|[CComboBox::ShowDropDown](../Topic/CComboBox::ShowDropDown.md)|Muestra u oculta el cuadro de lista de un cuadro combinado con el estilo de **CBS\_DROPDOWN** o de **CBS\_DROPDOWNLIST** .|  
  
## Comentarios  
 Un cuadro combinado se compone de un cuadro de lista combinado con un control estático o control de edición.  La parte del cuadro de lista del control puede mostrar siempre o puede interrumpir sólo abajo cuando el usuario selecciona la flecha de lista desplegable situada junto al control.  
  
 El elemento seleccionado \(si existe\) en el cuadro de lista se muestra actualmente en static o el control de edición.  Además, si el cuadro combinado tiene el estilo en la lista desplegable, el usuario puede escribir el carácter inicial de uno de los elementos en la lista, y el cuadro de lista, si está visible, resaltará el siguiente elemento con ese carácter inicial.  
  
 La tabla siguiente se comparan tres el cuadro combinado [estilos](../../mfc/reference/combo-box-styles.md).  
  
|Estilo|¿Cuándo es el cuadro de lista visible?|¿Estática o control de edición?|  
|------------|--------------------------------------------|-------------------------------------|  
|Sencillo|Siempre|Edición|  
|Desplegable|Cuando se divide abajo|Edición|  
|Lista desplegable.|Cuando se divide abajo|Static|  
  
 Puede crear un objeto de `CComboBox` de una plantilla de cuadro de diálogo o directamente en el código.  En ambos casos, llame primero al constructor `CComboBox` para construir el objeto de `CComboBox` ; llamar a continuación a la función miembro de [cree](../Topic/CComboBox::Create.md) para crear el control y para adjuntarlo al objeto de `CComboBox` .  
  
 Si desea controlar los mensajes de notificación de Windows enviados por un cuadro combinado a su elemento primario \(normalmente una clase derivada de `CDialog`\), agregue una función miembro de entrada y controlador de mensajes de mensaje\- mapa a la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 Notificación**\(**`id`**,**`memberFxn`**\)**de**ON\_**  
  
 donde `id` especifica el id. de la ventana secundaria del control de cuadro combinado que envía la notificación y `memberFxn` es el nombre de la función principal del miembro que ha escrito para controlar la notificación.  
  
 El prototipo de función del elemento primario es el siguiente:  
  
 **afx\_msg** `void` `memberFxn` **\(**\);  
  
 El orden en el que algunas notificaciones se enviarán no puede ser predicha.  En concreto, una notificación de **CBN\_SELCHANGE** puede producir antes o después de una notificación de **CBN\_CLOSEUP** .  
  
 Las entradas posibles de mensaje\- mapa son las siguientes:  
  
-   **ON\_CBN\_CLOSEUP** \(Windows 3.1 y posterior\). El cuadro de lista de un cuadro combinado se ha cerrado.  Este mensaje de notificación no se envía para un cuadro combinado con el estilo de [CBS\_SIMPLE](../../mfc/reference/combo-box-styles.md) .  
  
-   El usuario de**ON\_CBN\_DBLCLK** The hacer doble clic en una cadena en el cuadro de lista de un cuadro combinado.  Este mensaje de notificación se envía a un cuadro combinado con el estilo de **CBS\_SIMPLE** .  Para un cuadro combinado con el estilo de [CBS\_DROPDOWN](../../mfc/reference/combo-box-styles.md) o de [CBS\_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) , un doble clic no puede producirse porque un solo clic oculta el cuadro de lista.  
  
-   El cuadro de lista de**ON\_CBN\_DROPDOWN** speed un combobox está a punto de interrumpir siguiente \(creese visible\).  Este mensaje de notificación sólo puede aparecer en un cuadro combinado con el estilo de **CBS\_DROPDOWN** o de **CBS\_DROPDOWNLIST** .  
  
-   El usuario de**ON\_CBN\_EDITCHANGE** The ha realizado una acción que podrían haber modificado el texto en la parte del control de edición de un cuadro combinado.  A diferencia del mensaje de **CBN\_EDITUPDATE** , se envía este mensaje después de que Windows actualizar la pantalla.  No se envía si el cuadro combinado tiene el estilo de **CBS\_DROPDOWNLIST** .  
  
-   La parte del control de edición**ON\_CBN\_EDITUPDATE** The de un cuadro combinado trata sobre el texto modificado pantalla.  Se envía este mensaje de notificación después de que el control ha dado formato al texto pero antes de que muestra el texto.  No se envía si el cuadro combinado tiene el estilo de **CBS\_DROPDOWNLIST** .  
  
-   El cuadro combinado de**ON\_CBN\_ERRSPACE** no puede asignar memoria suficiente para satisfacer una solicitud concreta.  
  
-   **ON\_CBN\_SELENDCANCEL** \(Windows 3.1 y posterior\). Indica que la selección del usuario debe cancelarse.  El usuario hace clic en un elemento y haga clic en otra ventana o control para ocultar el cuadro de lista de un cuadro combinado.  Este mensaje de notificación se envía antes de que el mensaje de notificación de **CBN\_CLOSEUP** para indicar que la selección del usuario debe omitir.  Se envía el mensaje de notificación de **CBN\_SELENDCANCEL** o de **CBN\_SELENDOK** incluso si el mensaje de notificación de **CBN\_CLOSEUP** no se envía \(como en el caso de un cuadro combinado con el estilo de **CBS\_SIMPLE** \).  
  
-   El usuario de**ON\_CBN\_SELENDOK** The selecciona un elemento y después presione la tecla ENTRAR o haga clic en la tecla de flecha ABAJO para ocultar el cuadro de lista de un cuadro combinado.  Este mensaje de notificación se envía antes de que el mensaje de **CBN\_CLOSEUP** para indicar que la selección del usuario debe considerarse válida.  Se envía el mensaje de notificación de **CBN\_SELENDCANCEL** o de **CBN\_SELENDOK** incluso si el mensaje de notificación de **CBN\_CLOSEUP** no se envía \(como en el caso de un cuadro combinado con el estilo de **CBS\_SIMPLE** \).  
  
-   El cuadro combinado de**ON\_CBN\_KILLFOCUS** The está realizando el foco de entrada.  
  
-   La selección de**ON\_CBN\_SELCHANGE** The en el cuadro de lista de un cuadro combinado está a punto de cambiar como resultado del usuario que hace clic en el cuadro de lista o cambiar la selección mediante las teclas de dirección.  Al procesar este mensaje, el texto del control de edición del cuadro combinado se puede recuperar sólo mediante `GetLBText` u otra función similar.  No se puede usar `GetWindowText`.  
  
-   El cuadro combinado de**ON\_CBN\_SETFOCUS** The recibe el foco de entrada.  
  
 Si crea un objeto de `CComboBox` dentro de un cuadro de diálogo \(a través de un recurso de cuadro de diálogo\), el objeto de `CComboBox` automáticamente se destruye cuando el usuario cierra el cuadro de diálogo.  
  
 Si se inserta un objeto de `CComboBox` dentro de otro objeto de la ventana, no necesita destruirlo.  Si crea el objeto de `CComboBox` en la pila, se destruye automáticamente.  Si crea el objeto de `CComboBox` en la pila mediante la función de **nuevo** , debe llamar a **borrar** en el objeto para destruirlo cuando se destruye el cuadro combinado de Windows.  
  
 **Note** si desea controlar `WM_KEYDOWN` y los mensajes de `WM_CHAR` , tiene que crear subclases de edición y los controles de cuadro de lista del cuadro combinado, derivar clases de `CEdit` y de `CListBox`, y agregar controladores para esos mensajes a las clases derivadas.  Para obtener más información, vea [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;Q174667](http://support.microsoft.com/default.aspx?scid=kb;en-us;Q174667) y [CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo CTRLBARS de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)