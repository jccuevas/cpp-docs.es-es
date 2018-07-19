---
title: CPrintInfo (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPrintInfo
dev_langs:
- C++
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cac063d2ee2aeed563137dcb42d3007e81b1bd5
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851618"
---
# <a name="cprintinfo-structure"></a>CPrintInfo (estructura)
Almacena información acerca de un trabajo de impresión o de vista previa de impresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CPrintInfo  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](#getfrompage)|Devuelve el número de la primera página que se va a imprimir.|  
|[CPrintInfo::GetMaxPage](#getmaxpage)|Devuelve el número de la última página del documento.|  
|[CPrintInfo::GetMinPage](#getminpage)|Devuelve el número de la primera página del documento.|  
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Devuelve el número de las páginas anteriores a la primera página de un elemento de DocObject se pueda imprimir en un trabajo de impresión combinado de DocObject.|  
|[CPrintInfo::GetToPage](#gettopage)|Devuelve el número de la última página que se va a imprimir.|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|Establece el número de la última página del documento.|  
|[CPrintInfo::SetMinPage](#setminpage)|Establece el número de la primera página del documento.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Contiene una marca que indica si el marco de trabajo debe continuar el bucle de impresión.|  
|[CPrintInfo::m_bDirect](#m_bdirect)|Contiene una marca que indica si el documento se imprime directamente (sin mostrar el cuadro de diálogo Imprimir).|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Contiene una marca que indica si el documento que se está imprimiendo es DocObject.|  
|[CPrintInfo::m_bPreview](#m_bpreview)|Contiene una marca que indica si el documento está abierto en vista previa.|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|Especifica las operaciones de impresión de DocObject.|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Contiene un puntero a una estructura creada por el usuario.|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Identifica el número de la página que se está imprimiendo actualmente.|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Especifica el número de trabajo asignado por el sistema operativo para el trabajo de impresión actual|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Identifica el número de páginas que se muestran en la ventana de vista previa; 1 o 2.|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Especifica el desplazamiento de primera página de DocObject determinado en un trabajo de impresión combinado de DocObject.|  
|[CPrintInfo::m_pPD](#m_ppd)|Contiene un puntero a la `CPrintDialog` objeto usado para el cuadro de diálogo Imprimir.|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Especifica un rectángulo que define el área de página utilizable actual.|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Contiene una cadena de formato de visualización del número de página.|  
  
## <a name="remarks"></a>Comentarios  
 `CPrintInfo` es una estructura y no tiene una clase base.  
  
 El marco de trabajo crea un objeto de `CPrintInfo` cada vez que la impresión o el comando Vista previa de impresión se elige y destruye cuando se complete el comando.  
  
 `CPrintInfo` contiene información sobre el trabajo de impresión como un todo, así como el intervalo de páginas que se imprimen y el estado actual del trabajo de impresión, como la página que se está imprimiendo actualmente. Parte de la información se almacena en un asociado [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objeto; este objeto contiene los valores especificados por el usuario en el cuadro de diálogo Imprimir.  
  
 Un `CPrintInfo` objeto se pasa entre el marco de trabajo y la clase de vista durante el proceso de impresión y se utiliza para intercambiar información entre los dos. Por ejemplo, el marco de trabajo informa a la clase de vista qué página del documento para imprimir asignando un valor para el `m_nCurPage` miembro `CPrintInfo`; la vista recupera el valor de clase y realiza la impresión real de la página especificada.  
  
 Otro ejemplo es el caso en el que no se conoce la longitud del documento hasta que se imprima. En esta situación, la clase de vista de pruebas para el final del documento cada vez que se imprima una página. Cuando se alcanza el final, Establece la clase de vista el `m_bContinuePrinting` miembro `CPrintInfo` como FALSE; así informa el marco de trabajo para detener el bucle de impresión.  
  
 `CPrintInfo` se utiliza por las funciones miembro de `CView` enumerados bajo "Consulte también". Para obtener más información sobre la arquitectura de impresión proporcionada por la biblioteca Microsoft Foundation Class, consulte [marco Windows](../../mfc/frame-windows.md) y [arquitectura documento/vista](../../mfc/document-view-architecture.md) y los artículos [ Imprimir](../../mfc/printing.md) y [imprimir: documentos de varias páginas](../../mfc/multipage-documents.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CPrintInfo`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="getfrompage"></a>  CPrintInfo::GetFromPage  
 Llame a esta función para recuperar el número de la primera página que se imprimen.  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la primera página que se imprimen.  
  
### <a name="remarks"></a>Comentarios  
 Este es el valor especificado por el usuario en el cuadro de diálogo Imprimir, y se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro. Si el usuario no ha especificado un valor, el valor predeterminado es la primera página del documento.  
  
##  <a name="getmaxpage"></a>  CPrintInfo::GetMaxPage  
 Llame a esta función para recuperar el número de la última página del documento.  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la última página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro.  
  
##  <a name="getminpage"></a>  CPrintInfo::GetMinPage  
 Llame a esta función para recuperar el número de la primera página del documento.  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la primera página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro.  
  
##  <a name="getoffsetpage"></a>  CPrintInfo::GetOffsetPage  
 Llame a esta función para recuperar el desplazamiento al imprimir varios elementos de DocObject desde un cliente de DocObject.  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de páginas anterior a la primera página de un elemento de DocObject se pueda imprimir en un trabajo de impresión combinado de DocObject.  
  
### <a name="remarks"></a>Comentarios  
 Este valor hace referencia el `m_nOffsetPage` miembro. La primera página del documento se numeran los `m_nOffsetPage` valor de + 1 cuando se imprime como DocObject con otros documentos activos. El `m_nOffsetPage` miembro es válido únicamente si el `m_bDocObject` valor es TRUE.  
  
##  <a name="gettopage"></a>  CPrintInfo::GetToPage  
 Llame a esta función para recuperar el número de la última página que se van a imprimir.  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la última página que se van a imprimir.  
  
### <a name="remarks"></a>Comentarios  
 Este es el valor especificado por el usuario en el cuadro de diálogo Imprimir, y se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro. Si el usuario no ha especificado un valor, el valor predeterminado es la última página del documento.  
  
##  <a name="m_bcontinueprinting"></a>  CPrintInfo::m_bContinuePrinting  
 Contiene una marca que indica si el marco de trabajo debe continuar el bucle de impresión.  
  
### <a name="remarks"></a>Comentarios  
 Si va a realizar la paginación en tiempo de impresión, puede establecer este miembro en FALSE en el reemplazo de `CView::OnPrepareDC` una vez que se alcanzó el final del documento. No es necesario modificar esta variable si ha especificado la longitud del documento al principio del trabajo de impresión mediante la `SetMaxPage` función miembro. El `m_bContinuePrinting` miembro es una variable pública de tipo BOOL.  
  
##  <a name="m_bdirect"></a>  CPrintInfo::m_bDirect  
 El marco de trabajo establece a este miembro en TRUE si se omitirán el cuadro de diálogo de impresión para impresión directa; FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se omite el cuadro de diálogo de impresión al imprimir desde el shell o cuando se realiza la impresión con el comando ID_FILE_PRINT_DIRECT de identificador.  
  
 No cambie este miembro con normalidad, pero si lo cambia, cambiarlo antes llamada [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) en el reemplazo de [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="m_bdocobject"></a>  CPrintInfo::m_bDocObject  
 Contiene una marca que indica si el documento que se está imprimiendo es DocObject.  
  
### <a name="remarks"></a>Comentarios  
 Los miembros de datos `m_dwFlags` y `m_nOffsetPage` no son válidas, a menos que esta marca es TRUE.  
  
##  <a name="m_bpreview"></a>  CPrintInfo::m_bPreview  
 Contiene una marca que indica si el documento está abierto en vista previa.  
  
### <a name="remarks"></a>Comentarios  
 Esto se establece el marco de trabajo dependiendo de qué ejecuta el comando que el usuario. No se muestra el cuadro de diálogo de impresión de un trabajo de vista previa de impresión. El `m_bPreview` miembro es una variable pública de tipo BOOL.  
  
##  <a name="m_dwflags"></a>  CPrintInfo::m_dwFlags  
 Contiene una combinación de marcas que especifican las operaciones de impresión de DocObject.  
  
### <a name="remarks"></a>Comentarios  
 Sólo es válido si el miembro de datos `m_bDocObject` es TRUE.  
  
 Las marcas pueden ser uno o varios de los siguientes valores:  
  
- PRINTFLAG_MAYBOTHERUSER  
  
- PRINTFLAG_PROMPTUSER  
  
- PRINTFLAG_USERMAYCHANGEPRINTER  
  
- PRINTFLAG_RECOMPOSETODEVICE  
  
- PRINTFLAG_DONTACTUALLYPRINT  
  
- PRINTFLAG_FORCEPROPERTIES  
  
- PRINTFLAG_PRINTTOFILE  
  
##  <a name="m_lpuserdata"></a>  CPrintInfo::m_lpUserData  
 Contiene un puntero a una estructura creada por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizarlo para almacenar datos específicos de impresión que no desea almacenar en la clase de vista. El `m_lpUserData` miembro es una variable pública de tipo LPVOID.  
  
##  <a name="m_ncurpage"></a>  CPrintInfo::m_nCurPage  
 Contiene el número de la página actual.  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas de framework `CView::OnPrepareDC` y `CView::OnPrint` una vez para cada página del documento, especificando un valor diferente para este miembro cada vez; sus valores de intervalo del valor devuelto por `GetFromPage` al devuelto por `GetToPage`. Utilice este miembro en las invalidaciones de `CView::OnPrepareDC` y `CView::OnPrint` para imprimir la página especificada del documento.  
  
 Cuando se llama primero a modo de vista previa, el marco de trabajo lee el valor de este miembro para determinar qué página del documento se debe mostrar inicialmente. Puede establecer el valor de este miembro en el reemplazo de `CView::OnPreparePrinting` para mantener la posición del usuario actual en el documento al entrar en modo de vista previa. El `m_nCurPage` miembro es una variable pública de tipo UINT.  
  
##  <a name="m_njobnumber"></a>  CPrintInfo::m_nJobNumber  
 Indica el número de trabajo asignado por el sistema operativo para el trabajo de impresión actual.  
  
### <a name="remarks"></a>Comentarios  
 Este valor puede ser SP_ERROR si aún no se ha impreso el trabajo (es decir, si la `CPrintInfo` objeto recién se construye y aún no se ha usado para imprimir), o si se produjo un error en el inicio de la tarea.  
  
##  <a name="m_nnumpreviewpages"></a>  CPrintInfo::m_nNumPreviewPages  
 Contiene el número de páginas que se muestran en el modo de vista previa; puede ser 1 o 2.  
  
### <a name="remarks"></a>Comentarios  
 El `m_nNumPreviewPages` miembro es una variable pública de tipo UINT.  
  
##  <a name="m_noffsetpage"></a>  CPrintInfo::m_nOffsetPage  
 Contiene el número de páginas que preceden a la primera página de DocObject determinado en un trabajo de impresión combinado de DocObject.  
  
##  <a name="m_ppd"></a>  CPrintInfo::m_pPD  
 Contiene un puntero a la `CPrintDialog` objeto utilizado para mostrar el cuadro de diálogo de impresión del trabajo de impresión.  
  
### <a name="remarks"></a>Comentarios  
 El `m_pPD` miembro es una variable pública que se declara como un puntero a `CPrintDialog`.  
  
##  <a name="m_rectdraw"></a>  CPrintInfo::m_rectDraw  
 Especifica el área de dibujo utilizable de la página en coordenadas lógicas.  
  
### <a name="remarks"></a>Comentarios  
 Es posible que desee hacer referencia a ella en el reemplazo de `CView::OnPrint`. Puede utilizar a este miembro para realizar un seguimiento de qué área permanece utilizable después de imprimir los encabezados, pies de página y así sucesivamente. El `m_rectDraw` miembro es una variable pública de tipo `CRect`.  
  
##  <a name="m_strpagedesc"></a>  CPrintInfo::m_strPageDesc  
 Contiene una cadena de formato utilizada para mostrar los números de página durante la vista previa de impresión; Esta cadena consta de dos subcadenas, uno para la presentación de página única y otro para la presentación de página de doble, cada una termina con un carácter '\n'.  
  
### <a name="remarks"></a>Comentarios  
 El marco usa "Página %u\nPages % u-%u\n" como valor predeterminado. Si desea un formato diferente para los números de página, especifique una cadena de formato en el reemplazo de `CView::OnPreparePrinting`. El `m_strPageDesc` miembro es una variable pública de tipo `CString`.  
  
##  <a name="setmaxpage"></a>  CPrintInfo::SetMaxPage  
 Llame a esta función para especificar el número de la última página del documento.  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>Parámetros  
 *nMaxPage*  
 Número de la última página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro. Si se conoce la longitud del documento antes de imprimirlo, llame a esta función desde el reemplazo de `CView::OnPreparePrinting`. Si la longitud del documento depende de una configuración especificada por el usuario en el cuadro de diálogo Imprimir, llame a esta función desde el reemplazo de `CView::OnBeginPrinting`. Si no se conoce la longitud del documento hasta que se imprima, use el `m_bContinuePrinting` miembro para controlar el bucle de impresión.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="setminpage"></a>  CPrintInfo::SetMinPage  
 Llame a esta función para especificar el número de la primera página del documento.  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>Parámetros  
 *nMinPage*  
 Número de la primera página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Números de página normalmente empiezan en 1. Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)



