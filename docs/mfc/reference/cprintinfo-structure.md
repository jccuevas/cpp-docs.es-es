---
title: CPrintInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintInfo
dev_langs:
- C++
helpviewer_keywords:
- CPrintInfo structure
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ffa72acc58e0ac1a387e67e6542abcd466be9640
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cprintinfo-structure"></a>CPrintInfo (estructura)
Almacena información acerca de un trabajo de impresión o la vista previa de impresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CPrintInfo  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](#getfrompage)|Devuelve el número de la primera página que se va a imprimir.|  
|[CPrintInfo::GetMaxPage](#getmaxpage)|Devuelve el número de la última página del documento.|  
|[CPrintInfo::GetMinPage](#getminpage)|Devuelve el número de la primera página del documento.|  
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Devuelve el número de las páginas que precede a la primera página de un elemento de DocObject se imprime en un trabajo de impresión combinado de DocObject.|  
|[CPrintInfo::GetToPage](#gettopage)|Devuelve el número de la última página que se va a imprimir.|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|Establece el número de la última página del documento.|  
|[CPrintInfo::SetMinPage](#setminpage)|Establece el número de la primera página del documento.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Contiene una marca que indica si el marco de trabajo debe continuar el bucle de impresión.|  
|[CPrintInfo::m_bDirect](#m_bdirect)|Contiene una marca que indica si el documento se imprime directamente (sin mostrar el cuadro de diálogo de impresión).|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Contiene una marca que indica si el documento que está imprimiendo es DocObject.|  
|[CPrintInfo::m_bPreview](#m_bpreview)|Contiene una marca que indica si el documento está abierto en vista previa.|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|Especifica las operaciones de impresión de DocObject.|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Contiene un puntero a una estructura creada por el usuario.|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Identifica el número de la página que se está imprimiendo.|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Especifica el número de trabajo asignado por el sistema operativo para el trabajo de impresión actual|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Identifica el número de páginas que se muestran en la ventana de vista previa; 1 o 2.|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Especifica el desplazamiento de la primera página de DocObject determinado en un trabajo de impresión de DocObject combinado.|  
|[CPrintInfo::m_pPD](#m_ppd)|Contiene un puntero a la `CPrintDialog` objeto utilizado para el cuadro de diálogo Imprimir.|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Especifica un rectángulo que define el área de página utilizable actual.|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Contiene una cadena de formato para mostrar números de página.|  
  
## <a name="remarks"></a>Comentarios  
 `CPrintInfo`es una estructura y no tiene una clase base.  
  
 El marco de trabajo crea un objeto de `CPrintInfo` cada vez que la impresión o el comando de vista previa de impresión se selecciona y destruye cuando se completa el comando.  
  
 `CPrintInfo`contiene información sobre el trabajo de impresión como un todo, como el intervalo de páginas que se imprimen y el estado actual del trabajo de impresión, como la página que se está imprimiendo. Cierta información se almacena en un asociado [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objeto; este objeto contiene los valores especificados por el usuario en el cuadro de diálogo Imprimir.  
  
 Un `CPrintInfo` objeto se pasa entre el marco y la clase de vista durante el proceso de impresión y se utiliza para intercambiar información entre los dos. Por ejemplo, el marco de trabajo informa a la clase de vista de la página del documento para imprimir asignando un valor a la `m_nCurPage` miembro de `CPrintInfo`; la vista recupera el valor de clase y realiza la impresión real de la página especificada.  
  
 Otro ejemplo es el caso en el que no se conoce la longitud del documento hasta que se imprima. En esta situación, la clase de vista comprueba al final del documento cada vez que se imprima una página. Cuando se llega al final, Establece la clase de vista la `m_bContinuePrinting` miembro de `CPrintInfo` a **FALSE**; esto indica que el marco de trabajo para detener el bucle de impresión.  
  
 `CPrintInfo`usa las funciones miembro de `CView` enumerados en "Consulte también". Para obtener más información acerca de la arquitectura de impresión proporcionada por la biblioteca Microsoft Foundation Class, consulte [ventanas de marco](../../mfc/frame-windows.md) y [arquitectura documento/vista](../../mfc/document-view-architecture.md) y los artículos de [impresión](../../mfc/printing.md) y [imprimir: documentos de varias páginas](../../mfc/multipage-documents.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CPrintInfo`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="getfrompage"></a>CPrintInfo::GetFromPage  
 Llame a esta función para recuperar el número de la primera página que se va a imprimir.  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la primera página que se va a imprimir.  
  
### <a name="remarks"></a>Comentarios  
 Este es el valor especificado por el usuario en el cuadro de diálogo Imprimir, y se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro. Si el usuario no ha especificado un valor, el valor predeterminado es la primera página del documento.  
  
##  <a name="getmaxpage"></a>CPrintInfo::GetMaxPage  
 Llame a esta función para recuperar el número de la última página del documento.  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la última página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro.  
  
##  <a name="getminpage"></a>CPrintInfo::GetMinPage  
 Llame a esta función para recuperar el número de la primera página del documento.  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la primera página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro.  
  
##  <a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage  
 Llame a esta función para recuperar el desplazamiento al imprimir varios elementos de DocObject desde un cliente de DocObject.  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de páginas que precede a la primera página de un elemento de DocObject se imprime en un trabajo de impresión combinado de DocObject.  
  
### <a name="remarks"></a>Comentarios  
 Este valor hace referencia a la **m_nOffsetPage** miembro. La primera página del documento se numeran los **m_nOffsetPage** valor de + 1 cuando se imprima como DocObject con otros documentos activos. El **m_nOffsetPage** miembro es válido sólo si la **m_bDocObject** valor es **TRUE**.  
  
##  <a name="gettopage"></a>CPrintInfo::GetToPage  
 Llame a esta función para recuperar el número de la última página que se va a imprimir.  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de la última página que se va a imprimir.  
  
### <a name="remarks"></a>Comentarios  
 Este es el valor especificado por el usuario en el cuadro de diálogo Imprimir, y se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro. Si el usuario no ha especificado un valor, el valor predeterminado es la última página del documento.  
  
##  <a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting  
 Contiene una marca que indica si el marco de trabajo debe continuar el bucle de impresión.  
  
### <a name="remarks"></a>Comentarios  
 Si está realizando la paginación en tiempo de impresión, puede establecer este miembro en **FALSE** en el reemplazo de `CView::OnPrepareDC` una vez que se ha alcanzado el final del documento. No es necesario modificar esta variable si ha especificado la longitud del documento al principio del trabajo de impresión mediante la `SetMaxPage` función miembro. El `m_bContinuePrinting` miembro es una variable pública de tipo **BOOL**.  
  
##  <a name="m_bdirect"></a>CPrintInfo::m_bDirect  
 El marco de trabajo establece este miembro en **TRUE** si se omitirán el cuadro de diálogo de impresión para impresión directa; **FALSE** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se omite el cuadro de diálogo Imprimir al imprimir desde el shell o cuando se realiza la impresión con el identificador de comando **ID_FILE_PRINT_DIRECT**.  
  
 Normalmente no cambie este miembro, pero si lo cambia, cámbiela antes llamada [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) en el reemplazo de [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="m_bdocobject"></a>CPrintInfo::m_bDocObject  
 Contiene una marca que indica si el documento que está imprimiendo es DocObject.  
  
### <a name="remarks"></a>Comentarios  
 Miembros de datos `m_dwFlags` y **m_nOffsetPage** no son válidas a menos que esta marca es **TRUE**.  
  
##  <a name="m_bpreview"></a>CPrintInfo::m_bPreview  
 Contiene una marca que indica si el documento está abierto en vista previa.  
  
### <a name="remarks"></a>Comentarios  
 Esto establece el marco de trabajo según el que ejecutan comandos del usuario. No se muestra el cuadro de diálogo de impresión de un trabajo de vista previa de impresión. El **m_bPreview** miembro es una variable pública de tipo **BOOL**.  
  
##  <a name="m_dwflags"></a>CPrintInfo::m_dwFlags  
 Contiene una combinación de marcadores que especifican las operaciones de impresión de DocObject.  
  
### <a name="remarks"></a>Comentarios  
 Sólo es válido si el miembro de datos **m_bDocObject** es **TRUE**.  
  
 Los indicadores pueden ser uno o varios de los siguientes valores:  
  
- **PRINTFLAG_MAYBOTHERUSER**  
  
- **PRINTFLAG_PROMPTUSER**  
  
- **PRINTFLAG_USERMAYCHANGEPRINTER**  
  
- **PRINTFLAG_RECOMPOSETODEVICE**  
  
- **PRINTFLAG_DONTACTUALLYPRINT**  
  
- **PRINTFLAG_FORCEPROPERTIES**  
  
- **PRINTFLAG_PRINTTOFILE**  
  
##  <a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData  
 Contiene un puntero a una estructura creada por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizarla para almacenar datos específicos de la impresión de que no desea almacenar en la clase de vista. El **m_lpUserData** miembro es una variable pública de tipo **LPVOID**.  
  
##  <a name="m_ncurpage"></a>CPrintInfo::m_nCurPage  
 Contiene el número de la página actual.  
  
### <a name="remarks"></a>Comentarios  
 El marco llama `CView::OnPrepareDC` y `CView::OnPrint` una vez para cada página del documento, especificando un valor diferente para este miembro cada vez; sus valores de rango del valor devuelto por `GetFromPage` a la devuelta por `GetToPage`. Este miembro se utiliza en las invalidaciones de `CView::OnPrepareDC` y `CView::OnPrint` para imprimir la página especificada del documento.  
  
 Cuando el modo de vista previa se invoca por primera vez, el marco de trabajo lee el valor de este miembro para determinar qué página del documento se debe mostrar inicialmente. Puede establecer el valor de este miembro en el reemplazo de `CView::OnPreparePrinting` para mantener la posición del usuario actual en el documento al entrar en modo de vista previa. El `m_nCurPage` miembro es una variable pública de tipo **UINT**.  
  
##  <a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber  
 Indica el número de trabajo asignado por el sistema operativo para el trabajo de impresión actual.  
  
### <a name="remarks"></a>Comentarios  
 Este valor puede ser **SP_ERROR** si aún no se ha impreso el trabajo (es decir, si la `CPrintInfo` objeto está construido recientemente y todavía no se ha usado para imprimir), o si se produjo un error al iniciar el trabajo.  
  
##  <a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages  
 Contiene el número de páginas que se muestran en el modo de vista previa; puede ser 1 o 2.  
  
### <a name="remarks"></a>Comentarios  
 El **m_nNumPreviewPages** miembro es una variable pública de tipo **UINT**.  
  
##  <a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage  
 Contiene el número de páginas delante de la primera página de DocObject determinado en un trabajo de impresión combinado de DocObject.  
  
##  <a name="m_ppd"></a>CPrintInfo::m_pPD  
 Contiene un puntero a la `CPrintDialog` objeto utilizado para mostrar el cuadro de diálogo de impresión del trabajo de impresión.  
  
### <a name="remarks"></a>Comentarios  
 El `m_pPD` miembro es una variable pública que se declara como un puntero a `CPrintDialog`.  
  
##  <a name="m_rectdraw"></a>CPrintInfo::m_rectDraw  
 Especifica el área de dibujo utilizable de la página en coordenadas lógicas.  
  
### <a name="remarks"></a>Comentarios  
 Puede hacer referencia a ella en el reemplazo de `CView::OnPrint`. Este miembro puede utilizarse para realizar un seguimiento de qué área permanece utilizable después de imprimir los encabezados y pies de página. El **m_rectDraw** miembro es una variable pública de tipo `CRect`.  
  
##  <a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc  
 Contiene una cadena de formato utilizada para mostrar los números de página durante la vista previa de impresión; Esta cadena consta de dos subcadenas, una para la presentación de una página y otra para la presentación de página doble, cada una termina con un carácter '\n'.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa "Página %u\nPages % u-%u\n" como el valor predeterminado. Si desea un formato diferente para los números de página, especifique una cadena de formato en el reemplazo de `CView::OnPreparePrinting`. El **m_strPageDesc** miembro es una variable pública de tipo `CString`.  
  
##  <a name="setmaxpage"></a>CPrintInfo::SetMaxPage  
 Llame a esta función para especificar el número de la última página del documento.  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>Parámetros  
 *nMaxPage*  
 Número de la última página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro. Si se conoce la longitud del documento antes de imprimirlo, llame a esta función desde el reemplazo de `CView::OnPreparePrinting`. Si la longitud del documento depende de un valor especificado por el usuario en el cuadro de diálogo Imprimir, llame a esta función desde el reemplazo de `CView::OnBeginPrinting`. Si no se conoce la longitud del documento hasta que se imprima, use la `m_bContinuePrinting` miembros para controlar el bucle de impresión.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="setminpage"></a>CPrintInfo::SetMinPage  
 Llame a esta función para especificar el número de la primera página del documento.  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>Parámetros  
 *nMinPage*  
 Número de la primera página del documento.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, los números de página empiezan en 1. Este valor se almacena en el `CPrintDialog` objeto al que hace referencia el `m_pPD` miembro.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)




