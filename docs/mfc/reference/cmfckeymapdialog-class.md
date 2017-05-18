---
title: Clase CMFCKeyMapDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCKeyMapDialog class
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6599f5c3cda6eb407f4545d42528c1c68950b94c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cmfckeymapdialog-class"></a>Clase CMFCKeyMapDialog
La `CMFCKeyMapDialog` clase es compatible con un control que asigna comandos a teclas del teclado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Construye un objeto `CMFCKeyMapDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|Muestra un cuadro de diálogo de asignación de teclado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Llamado por el marco de trabajo para generar una cadena que describe una asignación de claves. De forma predeterminada, la cadena contiene el nombre de comando, utiliza las teclas de método abreviado y la descripción de la clave de acceso directo.|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Recupera una cadena que contiene una lista de teclas de método abreviado asociada con el comando especificado.|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Llamado por el marco antes de inserta un nuevo elemento en el control de lista interna que admite el control de asignación de teclado.|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Llamado por el marco de trabajo para imprimir el encabezado para la asignación de teclado en una página nueva.|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Llamado por el marco de trabajo para imprimir un elemento de asignación de teclado.|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Llamado por el marco para establecer los títulos de las columnas en el control de lista interna que admite el control de asignación de teclado.|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Llamado por el marco cuando un usuario hace clic en el **imprimir** botón.|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Llamado por el marco para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.|  
  
## <a name="remarks"></a>Comentarios  
 Utilice la `CMFCKeyMapDialog` clase para implementar un cuadro de diálogo de asignación de teclado de tamaño variable. El cuadro de diálogo, utiliza un control de vista de lista para mostrar métodos abreviados de teclado y sus comandos asociados.  
  
 Usar el `CMFCKeyMapDialog` de clases en una aplicación, pase un puntero a la ventana de marco principal como un parámetro a la `CMFCKeyMapDialog` constructor. A continuación, llame el `DoModal` método para iniciar el cuadro de diálogo modal.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxkeymapdialog.h  
  
##  <a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog  
 Construye un objeto `CMFCKeyMapDialog`.  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParentFrame`  
 Un puntero a la ventana primaria de la `CMFCKeyMapDialog` objeto.  
  
 [in] `bEnablePrint`  
 `TRUE`Si se puede imprimir la lista de teclas de aceleración; de lo contrario, `FALSE`. De manera predeterminada, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCKeyMapDialog` clase. Este ejemplo forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[21 NVC_MFC_VisualStudioDemo](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CMFCKeyMapDialog::DoModal  
 Muestra un cuadro de diálogo de asignación de teclado.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero con signo, como `IDOK` o `IDCANCEL`, que se pasa a la [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) método. El método, a su vez, cierra el cuadro de diálogo. Para obtener más información, consulte [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de diálogo de asignación de teclado permite seleccionar y asignar teclas de aceleración a distintas categorías de comandos. Además, puede copiar las teclas de aceleración seleccionada y su descripción en el Portapapeles.  
  
##  <a name="formatitem"></a>CMFCKeyMapDialog::FormatItem  
 Llamado por el marco de trabajo para generar una cadena que describe una asignación de claves. De forma predeterminada, la cadena contiene el nombre de comando, utiliza las teclas de método abreviado y la descripción de la clave de acceso directo.  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nItem`  
 Índice de base cero de un elemento de la lista interna de asignaciones de clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene el texto del elemento con formato.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys  
 Recupera un valor de cadena. La cadena contiene una lista de teclas de método abreviado asociadas a un comando especificado.  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Un identificador de comando.  
  
### <a name="return-value"></a>Valor devuelto  
 Delimitado por un punto y coma (';') lista de teclas de método abreviado asociada con el comando especificado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem  
 Llamado por el marco antes de inserta un nuevo elemento en un control de lista interna que admite el control de asignación de teclado.  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Un puntero a un botón de barra de herramientas que se utiliza para asignar una combinación de teclas del teclado para un nombre de comando y una descripción. El elemento de mapa de claves se almacena en un control de lista interna.  
  
 [in] `nItem`  
 Índice de base cero que especifica dónde se debe insertar el nuevo elemento de mapa de claves en el control de lista interna.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader  
 Llamado por el marco de trabajo para imprimir el encabezado para la asignación de teclado en una página nueva.  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dc`  
 El contexto de dispositivo para la impresora.  
  
 [in] `nPage`  
 Para imprimir el número de página.  
  
 [in] `cx`  
 El desplazamiento horizontal del encabezado, en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el alto del texto impreso. Para obtener más información, consulte la sección de valor devuelto de [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext).  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo utiliza este método para imprimir la asignación de teclado. De forma predeterminada, este método imprime el número de página, el nombre de aplicación y el título del cuadro de diálogo.  
  
##  <a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem  
 Llamado por el marco de trabajo para imprimir un elemento de asignación de teclado.  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dc`  
 El contexto de dispositivo de la impresora.  
  
 [in] `nItem`  
 Índice de base cero del elemento que se va a imprimir.  
  
 [in] `y`  
 El desplazamiento vertical entre la parte superior de la página y la posición del elemento.  
  
 [in] `cx`  
 El desplazamiento horizontal entre la izquierda de la página y la posición del elemento.  
  
 [in] `bCalcHeight`  
 `TRUE`para calcular el alto mejor para el elemento de impresión; `FALSE` para truncar el elemento de impresión para que se ajuste el espacio predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Alto del elemento impreso.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para imprimir un elemento de cuadro de diálogo de mapa de claves. De forma predeterminada, este método imprime el nombre de comando del artículo, teclas de método abreviado y descripción del comando.  
  
##  <a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns  
 Llamado por el marco para establecer los títulos de las columnas en el control de lista interna que admite el control de asignación de teclado.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método obtiene los títulos de las columnas de tres recursos. El título de columna de comando es de IDS_AFXBARRES_COMMAND, el título de la columna de clave es de IDS_AFXBARRES_KEYS y el título de columna de descripción es de IDS_AFXBARRES_DESCRIPTION.  
  
##  <a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap  
 Llamado por el marco cuando un usuario hace clic en el **imprimir** botón.  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>Comentarios  
 El `PrintKeyMap` método imprime el mapa de claves. Inicia un nuevo trabajo de impresión y luego llama repetidamente el [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) y [CMFCKeyMapDialog::OnPrintItem](#onprintitem) métodos hasta que se imprimen todas las asignaciones de clave.  
  
##  <a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth  
 Llamado por el marco para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método establece la lista interna columnas del control al ancho predeterminado. En primer lugar, se calcula el ancho de la columna de teclas de método abreviado. A continuación, un tercio del ancho restante se asigna a la columna de comandos y los dos tercios restantes se asigna a la columna Descripción.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

