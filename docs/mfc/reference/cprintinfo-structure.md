---
title: Estructura CPrintInfo
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: cf0a1e6b7e742e950663f1ed9cc9ff2ddabd9d6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364023"
---
# <a name="cprintinfo-structure"></a>Estructura CPrintInfo

Almacena información sobre un trabajo de impresión o vista previa de impresión.

## <a name="syntax"></a>Sintaxis

```
struct CPrintInfo
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|Devuelve el número de la primera página que se está imprimiendo.|
|[CPrintInfo::GetMaxPage](#getmaxpage)|Devuelve el número de la última página del documento.|
|[CPrintInfo::GetMinPage](#getminpage)|Devuelve el número de la primera página del documento.|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Devuelve el número de páginas que preceden a la primera página de un elemento DocObject que se imprime en un trabajo de impresión DocObject combinado.|
|[CPrintInfo::GetToPage](#gettopage)|Devuelve el número de la última página que se está imprimiendo.|
|[CPrintInfo::SetMaxPage](#setmaxpage)|Establece el número de la última página del documento.|
|[CPrintInfo::SetMinPage](#setminpage)|Establece el número de la primera página del documento.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Contiene un indicador que indica si el marco de trabajo debe continuar el bucle de impresión.|
|[CPrintInfo::m_bDirect](#m_bdirect)|Contiene una marca que indica si el documento se está imprimiendo directamente (sin mostrar el cuadro de diálogo Imprimir).|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Contiene una marca que indica si el documento que se está imprimiendo es un DocObject.|
|[CPrintInfo::m_bPreview](#m_bpreview)|Contiene una marca que indica si se está previsualizando el documento.|
|[CPrintInfo::m_dwFlags](#m_dwflags)|Especifica las operaciones de impresión de DocObject.|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Contiene un puntero a una estructura creada por el usuario.|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Identifica el número de la página que se está imprimiendo actualmente.|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Especifica el número de trabajo asignado por el sistema operativo para el trabajo de impresión actual|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Identifica el número de páginas que se muestran en la ventana de vista previa; 1 o 2.|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Especifica el desplazamiento de la primera página de un DocObject determinado en un trabajo de impresión DocObject combinado.|
|[CPrintInfo::m_pPD](#m_ppd)|Contiene un puntero `CPrintDialog` al objeto utilizado para el cuadro de diálogo Imprimir.|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Especifica un rectángulo que define el área de página utilizable actual.|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Contiene una cadena de formato para la visualización del número de página.|

## <a name="remarks"></a>Observaciones

`CPrintInfo`es una estructura y no tiene una clase base.

El marco de `CPrintInfo` trabajo crea un objeto de cada vez que se elige el comando Imprimir o Vista previa de impresión y lo destruye cuando se completa el comando.

`CPrintInfo`contiene información sobre el trabajo de impresión en su conjunto, como el intervalo de páginas que se van a imprimir y el estado actual del trabajo de impresión, como la página que se está imprimiendo actualmente. Parte de la información se almacena en un [asociado CPrintDialog](../../mfc/reference/cprintdialog-class.md) objeto; este objeto contiene los valores introducidos por el usuario en el cuadro de diálogo Imprimir.

Un `CPrintInfo` objeto se pasa entre el marco de trabajo y la clase de vista durante el proceso de impresión y se utiliza para intercambiar información entre los dos. Por ejemplo, el marco de trabajo informa a la clase de `m_nCurPage` vista `CPrintInfo`qué página del documento se va a imprimir asignando un valor al miembro de ; la clase de vista recupera el valor y realiza la impresión real de la página especificada.

Otro ejemplo es el caso en el que la longitud del documento no se conoce hasta que se imprime. En esta situación, la clase de vista comprueba el final del documento cada vez que se imprime una página. Cuando se alcanza el final, `m_bContinuePrinting` la `CPrintInfo` clase de vista establece el miembro de FALSE; esto informa al marco de trabajo para detener el bucle de impresión.

`CPrintInfo`es utilizado por las `CView` funciones miembro de la lista en "Ver también." Para obtener más información acerca de la arquitectura de impresión proporcionada por la biblioteca Microsoft Foundation Class, consulte [Frame Windows](../../mfc/frame-windows.md) and [Document/View Architecture](../../mfc/document-view-architecture.md) y los artículos [Printing](../../mfc/printing.md) and [Printing: Multipage Documents](../../mfc/multipage-documents.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CPrintInfo`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo::GetFromPage

Llame a esta función para recuperar el número de la primera página que se va a imprimir.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>Valor devuelto

El número de la primera página que se va a imprimir.

### <a name="remarks"></a>Observaciones

Este es el valor especificado por el usuario en el cuadro `CPrintDialog` de diálogo `m_pPD` Imprimir y se almacena en el objeto al que hace referencia el miembro. Si el usuario no ha especificado un valor, el valor predeterminado es la primera página del documento.

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo::GetMaxPage

Llame a esta función para recuperar el número de la última página del documento.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>Valor devuelto

El número de la última página del documento.

### <a name="remarks"></a>Observaciones

Este valor se `CPrintDialog` almacena en `m_pPD` el objeto al que hace referencia el miembro.

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo::GetMinPage

Llame a esta función para recuperar el número de la primera página del documento.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>Valor devuelto

El número de la primera página del documento.

### <a name="remarks"></a>Observaciones

Este valor se `CPrintDialog` almacena en `m_pPD` el objeto al que hace referencia el miembro.

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage

Llame a esta función para recuperar el desplazamiento al imprimir varios elementos DocObject desde un cliente DocObject.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>Valor devuelto

El número de páginas que preceden a la primera página de un elemento DocObject que se imprime en un trabajo de impresión combinado de DocObject.

### <a name="remarks"></a>Observaciones

El miembro hace `m_nOffsetPage` referencia a este valor. La primera página del documento se `m_nOffsetPage` numerará el valor + 1 cuando se imprima como DocObject con otros documentos activos. El `m_nOffsetPage` miembro solo es `m_bDocObject` válido si el valor es TRUE.

## <a name="cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo::GetToPage

Llame a esta función para recuperar el número de la última página que se va a imprimir.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>Valor devuelto

El número de la última página que se va a imprimir.

### <a name="remarks"></a>Observaciones

Este es el valor especificado por el usuario en el cuadro `CPrintDialog` de diálogo `m_pPD` Imprimir y se almacena en el objeto al que hace referencia el miembro. Si el usuario no ha especificado un valor, el valor predeterminado es la última página del documento.

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting

Contiene un indicador que indica si el marco de trabajo debe continuar el bucle de impresión.

### <a name="remarks"></a>Observaciones

Si va a realizar la paginación en tiempo de impresión, puede establecer este miembro en FALSE en la invalidación de `CView::OnPrepareDC` una vez que se ha alcanzado el final del documento. No es necesario modificar esta variable si ha especificado la longitud del documento al `SetMaxPage` principio del trabajo de impresión mediante la función miembro. El `m_bContinuePrinting` miembro es una variable pública de tipo BOOL.

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a>CPrintInfo::m_bDirect

El marco de trabajo establece este miembro en TRUE si el cuadro de diálogo Imprimir se omitirá para la impresión directa; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Normalmente, el cuadro de diálogo Imprimir se omite al imprimir desde el shell o al imprimir mediante el id de comando ID_FILE_PRINT_DIRECT.

Normalmente no cambia este miembro, pero si lo cambia, cámbielo antes de llamar a [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) en la invalidación de [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a>CPrintInfo::m_bDocObject

Contiene una marca que indica si el documento que se está imprimiendo es un DocObject.

### <a name="remarks"></a>Observaciones

Miembros `m_dwFlags` `m_nOffsetPage` de datos y no son válidos a menos que esta marca sea TRUE.

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a>CPrintInfo::m_bPreview

Contiene una marca que indica si se está previsualizando el documento.

### <a name="remarks"></a>Observaciones

Esto lo establece el marco de trabajo en función del comando que el usuario haya ejecutado. El cuadro de diálogo Imprimir no se muestra para un trabajo de vista previa de impresión. El `m_bPreview` miembro es una variable pública de tipo BOOL.

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a>CPrintInfo::m_dwFlags

Contiene una combinación de indicadores que especifican operaciones de impresión DocObject.

### <a name="remarks"></a>Observaciones

Válido solo si `m_bDocObject` el miembro de datos es TRUE.

Los indicadores pueden ser uno o varios de los siguientes valores:

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData

Contiene un puntero a una estructura creada por el usuario.

### <a name="remarks"></a>Observaciones

Puede usarlo para almacenar datos específicos de impresión que no desea almacenar en la clase de vista. El `m_lpUserData` miembro es una variable pública de tipo LPVOID.

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a>CPrintInfo::m_nCurPage

Contiene el número de la página actual.

### <a name="remarks"></a>Observaciones

El marco `CView::OnPrepareDC` `CView::OnPrint` de trabajo llama y una vez para cada página del documento, especificando un valor diferente para este miembro cada vez; sus valores van desde `GetFromPage` el valor `GetToPage`devuelto por el devuelto por . Utilice este miembro en `CView::OnPrepareDC` las `CView::OnPrint` invalidaciones de e imprimir la página especificada del documento.

Cuando se invoca por primera vez el modo de vista previa, el marco de trabajo lee el valor de este miembro para determinar qué página del documento se debe obtener una vista previa inicialmente. Puede establecer el valor de este `CView::OnPreparePrinting` miembro en la invalidación de mantener la posición actual del usuario en el documento al entrar en modo de vista previa. El `m_nCurPage` miembro es una variable pública de tipo UINT.

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber

Indica el número de trabajo asignado por el sistema operativo para el trabajo de impresión actual.

### <a name="remarks"></a>Observaciones

Este valor puede ser SP_ERROR si el trabajo aún no `CPrintInfo` se ha impreso (es decir, si el objeto está recién construido y aún no se ha utilizado para imprimir), o si se ha producido un error al iniciar el trabajo.

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages

Contiene el número de páginas mostradas en modo de vista previa; puede ser 1 o 2.

### <a name="remarks"></a>Observaciones

El `m_nNumPreviewPages` miembro es una variable pública de tipo UINT.

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage

Contiene el número de páginas que preceden a la primera página de un DocObject determinado en un trabajo de impresión Combinado de DocObject.

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a>CPrintInfo::m_pPD

Contiene un puntero `CPrintDialog` al objeto utilizado para mostrar el cuadro de diálogo Imprimir para el trabajo de impresión.

### <a name="remarks"></a>Observaciones

El `m_pPD` miembro es una variable pública `CPrintDialog`declarada como un puntero a .

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a>CPrintInfo::m_rectDraw

Especifica el área de dibujo utilizable de la página en coordenadas lógicas.

### <a name="remarks"></a>Observaciones

Es posible que desee hacer `CView::OnPrint`referencia a esto en su anulación de . Puede utilizar este miembro para realizar un seguimiento de qué área sigue siendo utilizable después de imprimir encabezados, pies de página, etc. El `m_rectDraw` miembro es una `CRect`variable pública de tipo .

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc

Contiene una cadena de formato utilizada para mostrar los números de página durante la vista previa de impresión; esta cadena consta de dos subcadenas, una para la visualización de una sola página y otra para la visualización de doble página, cada una terminada por un carácter 'n'.

### <a name="remarks"></a>Observaciones

El marco de trabajo usa "Página %u-nPáginas %u-%u-n" como valor predeterminado. Si desea un formato diferente para los números de `CView::OnPreparePrinting`página, especifique una cadena de formato en la invalidación de . El `m_strPageDesc` miembro es una `CString`variable pública de tipo .

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::SetMaxPage

Llame a esta función para especificar el número de la última página del documento.

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>Parámetros

*nMaxPage*<br/>
Número de la última página del documento.

### <a name="remarks"></a>Observaciones

Este valor se `CPrintDialog` almacena en `m_pPD` el objeto al que hace referencia el miembro. Si se conoce la longitud del documento antes de imprimirlo, `CView::OnPreparePrinting`llame a esta función desde la invalidación de . Si la longitud del documento depende de una configuración especificada por el usuario en `CView::OnBeginPrinting`el cuadro de diálogo Imprimir, llame a esta función desde la invalidación de . Si la longitud del documento no se conoce hasta `m_bContinuePrinting` que se imprime, utilice el miembro para controlar el bucle de impresión.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo::SetMinPage

Llame a esta función para especificar el número de la primera página del documento.

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>Parámetros

*nMinPage*<br/>
Número de la primera página del documento.

### <a name="remarks"></a>Observaciones

Los números de página normalmente comienzan en 1. Este valor se `CPrintDialog` almacena en `m_pPD` el objeto al que hace referencia el miembro.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
