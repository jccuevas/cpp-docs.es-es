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
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1965e5dd2d522175b3709449df9a0b8575e20c59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfckeymapdialog-class"></a>Clase CMFCKeyMapDialog
La `CMFCKeyMapDialog` clase es compatible con un control que asigna comandos a teclas del teclado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Construye un objeto `CMFCKeyMapDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::DoModal](#domodal)|Muestra un cuadro de diálogo de asignación de teclado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Lo llama el marco para generar una cadena que describe una asignación de claves. De forma predeterminada, la cadena contiene el nombre de comando, las teclas de método abreviado que se utiliza y la descripción de la clave de acceso directo.|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Recupera una cadena que contiene una lista de teclas de método abreviado asociada con el comando especificado.|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Llamado por el marco de trabajo antes de que se inserta un nuevo elemento en el control de lista interna que admite el control de asignación de teclado.|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Lo llama el marco de trabajo para imprimir el encabezado para la asignación de teclado en una página nueva.|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Lo llama el marco de trabajo para imprimir un elemento de asignación de teclado.|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Lo llama el marco para establecer los títulos de las columnas en el control de lista interna que admite el control de asignación de teclado.|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Lo llama el marco cuando un usuario hace clic en el **impresión** botón.|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Lo llama el marco para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.|  
  
## <a name="remarks"></a>Comentarios  
 Use la `CMFCKeyMapDialog` clase para implementar un cuadro de diálogo de asignación de teclado de tamaño ajustable. El cuadro de diálogo, usa un control de vista de lista para mostrar los métodos abreviados de teclado y sus comandos asociados.  
  
 Para usar el `CMFCKeyMapDialog` de clases en una aplicación, pase un puntero a la ventana de marco principal como un parámetro a la `CMFCKeyMapDialog` constructor. A continuación, llame a la `DoModal` método para iniciar el cuadro de diálogo modal.  
  
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
 `TRUE`Si se puede imprimir la lista de teclas de aceleración; en caso contrario, `FALSE`. De manera predeterminada, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCKeyMapDialog` clase. Este ejemplo forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CMFCKeyMapDialog::DoModal  
 Muestra un cuadro de diálogo de asignación de teclado.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero con signo, como `IDOK` o `IDCANCEL`, que se pasa a la [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) método. El método, a su vez, cierra el cuadro de diálogo. Para obtener más información, consulte [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).  
  
### <a name="remarks"></a>Comentarios  
 El cuadro de diálogo de asignación de teclado permite seleccionar y asignar teclas de aceleración a varias categorías de comandos. Además, puede copiar las teclas de aceleración seleccionado y su descripción en el Portapapeles.  
  
##  <a name="formatitem"></a>CMFCKeyMapDialog::FormatItem  
 Lo llama el marco para generar una cadena que describe una asignación de claves. De forma predeterminada, la cadena contiene el nombre de comando, las teclas de método abreviado que se utiliza y la descripción de la clave de acceso directo.  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nItem`  
 Índice de base cero de un elemento en la lista interna de asignaciones de clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene el texto del elemento con formato.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys  
 Recupera un valor de cadena. La cadena contiene una lista de teclas de método abreviado que están asociados a un comando especificado.  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdID`  
 Un identificador de comando.  
  
### <a name="return-value"></a>Valor devuelto  
 Delimitado por un punto y coma (';') lista de teclas de método abreviado que está asociado con el comando especificado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem  
 Llamado por el marco de trabajo antes de que se inserta un nuevo elemento en un control de lista interna que admite el control de asignación de teclado.  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Un puntero a un botón de barra de herramientas que se utiliza para asignar una combinación de teclas del teclado a un nombre de comando y una descripción. El elemento de mapa de claves se almacena en un control de lista interna.  
  
 [in] `nItem`  
 Índice de base cero que especifica dónde desea insertar el nuevo elemento de mapa de claves en el control de lista interna.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader  
 Lo llama el marco de trabajo para imprimir el encabezado para la asignación de teclado en una página nueva.  
  
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
 El número de página para imprimir.  
  
 [in] `cx`  
 El desplazamiento horizontal del encabezado, en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el alto del texto impreso. Para obtener más información, vea la sección de valor devuelto de [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext).  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo utiliza este método para imprimir la asignación de teclado. De forma predeterminada, este método imprime el número de página, el nombre de la aplicación y el título del cuadro de diálogo.  
  
##  <a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem  
 Lo llama el marco de trabajo para imprimir un elemento de asignación de teclado.  
  
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
 `TRUE`para calcular el alto recomendado para el elemento de impresión; `FALSE` para truncar el elemento de impresión para que se ajuste el espacio predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 El alto del elemento impreso.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para imprimir un elemento de cuadro de diálogo de mapa de claves. De forma predeterminada, este método imprime el nombre de comando del elemento, teclas de método abreviado y descripción del comando.  
  
##  <a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns  
 Lo llama el marco para establecer los títulos de las columnas en el control de lista interna que admite el control de asignación de teclado.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método obtiene los títulos de las columnas de tres recursos. El título de columna de comando es de IDS_AFXBARRES_COMMAND, el título de columna de clave es de IDS_AFXBARRES_KEYS y el título de columna de descripción es de IDS_AFXBARRES_DESCRIPTION.  
  
##  <a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap  
 Lo llama el marco cuando un usuario hace clic en el **impresión** botón.  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>Comentarios  
 El `PrintKeyMap` método imprime el mapa de claves. Se inicia un nuevo trabajo de impresión y, a continuación, se llama repetidamente el [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) y [CMFCKeyMapDialog::OnPrintItem](#onprintitem) métodos hasta que se imprimen todas las asignaciones de clave.  
  
##  <a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth  
 Lo llama el marco para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método establece la lista interna columnas del control a los anchos de forma predeterminada. En primer lugar, se calcula el ancho de la columna de las teclas de método abreviado. A continuación, un tercio del ancho restante se asigna a la columna de comando y los dos tercios restantes se asigna a la columna de descripción.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager (clase)](../../mfc/reference/ckeyboardmanager-class.md)
