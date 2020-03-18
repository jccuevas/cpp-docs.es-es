---
title: CEditView (clase)
ms.date: 11/04/2016
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
ms.openlocfilehash: e9b7dea980e607c776e2d50c679042c765080fdb
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424426"
---
# <a name="ceditview-class"></a>CEditView (clase)

Un tipo de clase de vista que proporciona la funcionalidad de un control de edición de Windows y se puede utilizar para implementar funcionalidad de editor de texto simple.

## <a name="syntax"></a>Sintaxis

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView:: CEditView](#ceditview)|Construye un objeto de tipo `CEditView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView:: FindText](#findtext)|Busca una cadena en el texto.|
|[CEditView:: GetBufferLength](#getbufferlength)|Obtiene la longitud del búfer de caracteres.|
|[CEditView:: GetEditCtrl](#geteditctrl)|Proporciona acceso a la parte `CEdit` de un objeto `CEditView` (el control de edición de Windows).|
|[CEditView:: GetPrinterFont](#getprinterfont)|Recupera la fuente de la impresora actual.|
|[CEditView:: GetSelectedText](#getselectedtext)|Recupera la selección de texto actual.|
|[CEditView:: LockBuffer](#lockbuffer)|Bloquea el búfer.|
|[CEditView::P rintInsideRect](#printinsiderect)|Representa el texto dentro de un rectángulo determinado.|
|[CEditView:: SerializeRaw](#serializeraw)|Serializa un objeto `CEditView` en el disco como texto sin formato.|
|[CEditView:: SetPrinterFont](#setprinterfont)|Establece una nueva fuente de impresora.|
|[CEditView:: SetTabStops](#settabstops)|Establece las tabulaciones para la presentación en pantalla y la impresión.|
|[CEditView:: UnlockBuffer](#unlockbuffer)|Desbloquea el búfer.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView:: OnFindNext](#onfindnext)|Busca la siguiente repetición de una cadena de texto.|
|[CEditView:: OnReplaceAll](#onreplaceall)|Reemplaza todas las apariciones de una cadena determinada por una nueva cadena.|
|[CEditView:: OnReplaceSel](#onreplacesel)|Reemplaza la selección actual.|
|[CEditView:: OnTextNotFound](#ontextnotfound)|Se llama cuando una operación de búsqueda no coincide con ningún texto adicional.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView::d wStyleDefault](#dwstyledefault)|Estilo predeterminado para los objetos de tipo `CEditView`.|

## <a name="remarks"></a>Observaciones

La clase `CEditView` proporciona las siguientes funciones adicionales:

- Impresión.

- Busque y reemplace.

Dado que la clase `CEditView` es un derivado de la clase `CView`, los objetos de la clase `CEditView` se pueden usar con documentos y plantillas de documento.

Cada `CEditView` texto del control se mantiene en su propio objeto de memoria global. La aplicación puede tener cualquier número de objetos de `CEditView`.

Cree objetos de tipo `CEditView` si desea una ventana de edición con la funcionalidad agregada indicada anteriormente, o si desea una funcionalidad de editor de texto simple. Un objeto `CEditView` puede ocupar todo el área cliente de una ventana. Derive sus propias clases de `CEditView` para agregar o modificar la funcionalidad básica o para declarar las clases que se pueden agregar a una plantilla de documento.

La implementación predeterminada de la clase `CEditView` controla los siguientes comandos: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT y ID_FILE_PRINT.

El límite de caracteres predeterminado para `CEditView` es (1024 \* 1024-1 = 1048575). Esto se puede cambiar mediante una llamada a la función EM_LIMITTEXT del control de edición subyacente. Sin embargo, los límites son diferentes según el sistema operativo y el tipo de control de edición (único o multilínea). Para obtener más información sobre estos límites, vea [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Para cambiar este límite en el control, invalide la función `OnCreate()` para la clase `CEditView` e inserte la siguiente línea de código:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Los objetos de tipo `CEditView` (o de tipos derivados de `CEditView`) tienen las siguientes limitaciones:

- `CEditView` no implementa lo que se ve es lo que se ve es lo que se obtiene (WYSIWYG) editando. Cuando hay una opción entre la legibilidad de la pantalla y la coincidencia de la salida impresa, `CEditView` opta por la legibilidad de la pantalla.

- `CEditView` solo puede mostrar texto en una fuente única. No se admite el formato de caracteres especiales. Vea la clase [CRichEditView](../../mfc/reference/cricheditview-class.md) para obtener una mayor capacidad.

- La cantidad de texto que puede contener un `CEditView` es limitado. Los límites son los mismos que para el control de `CEdit`.

Para obtener más información sobre `CEditView`, vea [clases de vistas derivadas disponibles en MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="ceditview"></a>CEditView:: CEditView

Construye un objeto de tipo `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Observaciones

Después de construir el objeto, debe llamar a la función [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) antes de usar el control de edición. Si se deriva una clase de `CEditView` y se agrega a la plantilla mediante `CWinApp::AddDocTemplate`, el marco de trabajo llama a este constructor y a la función `Create`.

##  <a name="dwstyledefault"></a>CEditView::d wStyleDefault

Contiene el estilo predeterminado del objeto `CEditView`.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Observaciones

Pase este miembro estático como el parámetro *dwStyle* de la función `Create` para obtener el estilo predeterminado para el objeto `CEditView`.

##  <a name="findtext"></a>CEditView:: FindText

Llame a la función `FindText` para buscar en el búfer de texto del objeto `CEditView`.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que se va a buscar.

*bNext*<br/>
Especifica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda está hacia el final del búfer. Si es FALSE, la dirección de búsqueda está hacia el principio del búfer.

*bCase*<br/>
Especifica si la búsqueda distingue entre mayúsculas y minúsculas. Si es TRUE, la búsqueda distingue entre mayúsculas y minúsculas. Si es FALSE, la búsqueda no distingue entre mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el texto de búsqueda; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función busca en el texto del búfer el texto especificado por *lpszFind*, a partir de la selección actual, en la dirección especificada por *bNext*y con la distinción entre mayúsculas y minúsculas especificada por *bCase*. Si se encuentra el texto, establece la selección en el texto encontrado y devuelve un valor distinto de cero. Si no se encuentra el texto, la función devuelve 0.

Normalmente no es necesario llamar a la función `FindText` a menos que se invalide `OnFindNext`, que llama a `FindText`.

##  <a name="getbufferlength"></a>CEditView:: GetBufferLength

Llame a esta función miembro para obtener el número de caracteres que hay actualmente en el búfer del control de edición, sin incluir el terminador null.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud de la cadena en el búfer.

##  <a name="geteditctrl"></a>CEditView:: GetEditCtrl

Llame a `GetEditCtrl` para obtener una referencia al control de edición que usa la vista de edición.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto `CEdit`.

### <a name="remarks"></a>Observaciones

Este control es de tipo [CEDIT](../../mfc/reference/cedit-class.md), por lo que puede manipular el control de edición de Windows directamente mediante las funciones miembro de `CEdit`.

> [!CAUTION]
>  El uso del objeto `CEdit` puede cambiar el estado del control de edición de Windows subyacente. Por ejemplo, no debe cambiar la configuración de la pestaña con la función [CEDIT:: SetTabStops](../../mfc/reference/cedit-class.md#settabstops) porque `CEditView` almacena en caché estos valores para usarlos en el control de edición y en la impresión. En su lugar, use [CEditView:: SetTabStops](#settabstops).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>CEditView:: GetPrinterFont

Llame a `GetPrinterFont` para obtener un puntero a un objeto [Cfont (](../../mfc/reference/cfont-class.md) que describe la fuente de la impresora actual.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CFont` que especifica la fuente de la impresora actual; ES NULL si no se ha establecido la fuente de la impresora. El puntero puede ser temporal y no se debe almacenar para su uso posterior.

### <a name="remarks"></a>Observaciones

Si no se ha establecido la fuente de la impresora, el comportamiento de impresión predeterminado de la clase `CEditView` es imprimir con la misma fuente que se usa para la presentación.

Utilice esta función para determinar la fuente de la impresora actual. Si no es la fuente de impresora deseada, use [CEditView:: SetPrinterFont](#setprinterfont) para cambiarla.

##  <a name="getselectedtext"></a>CEditView:: GetSelectedText

Llame a `GetSelectedText` para copiar el texto seleccionado en un objeto `CString`, hasta el final de la selección o el carácter que precede al primer carácter de retorno de carro en la selección.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parámetros

*strResult*<br/>
Referencia al objeto `CString` que va a recibir el texto seleccionado.

##  <a name="lockbuffer"></a>CEditView:: LockBuffer

Llame a esta función miembro para obtener un puntero al búfer. No se debe modificar el búfer.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al búfer del control de edición.

##  <a name="onfindnext"></a>CEditView:: OnFindNext

Busca en el texto del búfer el texto especificado por *lpszFind*, en la dirección especificada por *bNext*, con distinción de mayúsculas y minúsculas especificada por *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que se va a buscar.

*bNext*<br/>
Especifica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda está hacia el final del búfer. Si es FALSE, la dirección de búsqueda está hacia el principio del búfer.

*bCase*<br/>
Especifica si la búsqueda distingue entre mayúsculas y minúsculas. Si es TRUE, la búsqueda distingue entre mayúsculas y minúsculas. Si es FALSE, la búsqueda no distingue entre mayúsculas y minúsculas.

### <a name="remarks"></a>Observaciones

La búsqueda comienza al principio de la selección actual y se realiza a través de una llamada a [FindText](#findtext). En la implementación predeterminada, `OnFindNext` llama a [OnTextNotFound](#ontextnotfound) si no se encuentra el texto.

Invalide `OnFindNext` para cambiar la forma en que un objeto derivado de `CEditView`busca en el texto. `CEditView` llama a `OnFindNext` cuando el usuario elige el botón Buscar siguiente en el cuadro de diálogo Buscar estándar.

##  <a name="onreplaceall"></a>CEditView:: OnReplaceAll

`CEditView` llama `OnReplaceAll` cuando el usuario selecciona el botón reemplazar todo en el cuadro de diálogo reemplazar estándar.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que se va a buscar.

*lpszReplace*<br/>
Texto en el que se va a reemplazar el texto de búsqueda.

*bCase*<br/>
Especifica si la búsqueda distingue entre mayúsculas y minúsculas. Si es TRUE, la búsqueda distingue entre mayúsculas y minúsculas. Si es FALSE, la búsqueda no distingue entre mayúsculas y minúsculas.

### <a name="remarks"></a>Observaciones

`OnReplaceAll` busca en el texto del búfer el texto especificado por *lpszFind*, con distinción de mayúsculas y minúsculas especificada por *bCase*. La búsqueda comienza al principio de la selección actual. Cada vez que se encuentra el texto de búsqueda, esta función reemplaza la aparición del texto por el texto especificado por *lpszReplace*. La búsqueda se realiza a través de una llamada a [FindText](#findtext). En la implementación predeterminada, se llama a [OnTextNotFound](#ontextnotfound) si no se encuentra el texto.

Si la selección actual no coincide con *lpszFind*, la selección se actualiza a la primera aparición del texto especificado por *lpszFind* y no se realiza un reemplazo. Esto permite al usuario confirmar que es lo que desea hacer cuando la selección no coincide con el texto que se va a reemplazar.

Invalide `OnReplaceAll` para cambiar la forma en que un objeto derivado de `CEditView`reemplaza el texto.

##  <a name="onreplacesel"></a>CEditView:: OnReplaceSel

`CEditView` llama `OnReplaceSel` cuando el usuario selecciona el botón reemplazar en el cuadro de diálogo reemplazar estándar.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que se va a buscar.

*bNext*<br/>
Especifica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda está hacia el final del búfer. Si es FALSE, la dirección de búsqueda está hacia el principio del búfer.

*bCase*<br/>
Especifica si la búsqueda distingue entre mayúsculas y minúsculas. Si es TRUE, la búsqueda distingue entre mayúsculas y minúsculas. Si es FALSE, la búsqueda no distingue entre mayúsculas y minúsculas.

*lpszReplace*<br/>
Texto en el que se va a reemplazar el texto encontrado.

### <a name="remarks"></a>Observaciones

Después de reemplazar la selección, esta función busca en el texto del búfer la siguiente aparición del texto especificado por *lpszFind*, en la dirección especificada por *bNext*, con distinción de mayúsculas y minúsculas especificada por *bCase*. La búsqueda se realiza a través de una llamada a [FindText](#findtext). Si no se encuentra el texto, se llama a [OnTextNotFound](#ontextnotfound) .

Invalide `OnReplaceSel` para cambiar la forma en que un objeto derivado de `CEditView`reemplaza el texto seleccionado.

##  <a name="ontextnotfound"></a>CEditView:: OnTextNotFound

Invalide esta función para cambiar la implementación predeterminada, que llama a la función de Windows `MessageBeep`.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que se va a buscar.

##  <a name="printinsiderect"></a>CEditView::P rintInsideRect

Llame a `PrintInsideRect` para imprimir texto en el rectángulo especificado por *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero en el contexto del dispositivo de impresora.

*rectLayout*<br/>
Referencia a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una [estructura Rect](/windows/win32/api/windef/ns-windef-rect) que especifica el rectángulo en el que se va a representar el texto.

*nIndexStart*<br/>
Índice dentro del búfer del primer carácter que se va a representar.

*nIndexStop*<br/>
Índice en el búfer del carácter que sigue al último carácter que se va a representar.

### <a name="return-value"></a>Valor devuelto

Índice del siguiente carácter que se va a imprimir (es decir, el carácter que sigue al último carácter representado).

### <a name="remarks"></a>Observaciones

Si el control de `CEditView` no tiene el estilo ES_AUTOHSCROLL, el texto se ajusta dentro del rectángulo de representación. Si el control tiene el estilo ES_AUTOHSCROLL, el texto se recorta en el borde derecho del rectángulo.

Se cambia el elemento `rect.bottom` del objeto *rectLayout* para que las dimensiones del rectángulo definan la parte del rectángulo original ocupada por el texto.

##  <a name="serializeraw"></a>CEditView:: SerializeRaw

Llame a `SerializeRaw` para tener un objeto `CArchive` leer o escribir el texto del objeto `CEditView` en un archivo de texto.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*analítico*<br/>
Referencia al objeto `CArchive` que almacena el texto serializado.

### <a name="remarks"></a>Observaciones

`SerializeRaw` difiere de la implementación interna de `CEditView`de `Serialize` en que lee y escribe solo el texto, sin datos de descripción de objeto anteriores.

##  <a name="setprinterfont"></a>CEditView:: SetPrinterFont

Llame a `SetPrinterFont` para establecer la fuente de la impresora en la fuente especificada por *pFont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
Un puntero a un objeto de tipo `CFont`. Si es NULL, la fuente utilizada para imprimir se basa en la fuente de la pantalla.

### <a name="remarks"></a>Observaciones

Si desea que la vista siempre use una fuente determinada para imprimir, incluya una llamada a `SetPrinterFont` en la función de `OnPreparePrinting` de su clase. Se llama a esta función virtual antes de que se produzca la impresión, por lo que el cambio de fuente tiene lugar antes de que se imprima el contenido de la vista.

##  <a name="settabstops"></a>CEditView:: SetTabStops

Llame a esta función para establecer las tabulaciones que se usan para mostrar e imprimir.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parámetros

*nTabStops*<br/>
Ancho de cada tabulación, en unidades de cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Solo se admite un ancho de detención de tabulación. (los objetos `CEdit` admiten varios anchos de pestaña). Los anchos están en unidades de cuadro de diálogo, que son iguales a una cuarta parte del ancho promedio de caracteres (solo en caracteres alfabéticos en mayúsculas y minúsculas) de la fuente utilizada en el momento de la impresión o la visualización. No debe utilizar `CEdit::SetTabStops` porque `CEditView` debe almacenar en caché el valor de tabulación.

Esta función modifica únicamente las pestañas del objeto para el que se llama. Para cambiar las tabulaciones de cada objeto de `CEditView` de la aplicación, llame a la función `SetTabStops` de cada objeto.

### <a name="example"></a>Ejemplo

Este fragmento de código establece los puntos de tabulación del control en cada cuarto carácter al medir cuidadosamente la fuente que el control utiliza.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>CEditView:: UnlockBuffer

Llame a esta función miembro para desbloquear el búfer.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Observaciones

Llame a `UnlockBuffer` después de haber terminado de usar el puntero devuelto por [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Consulte también

[Ejemplo SUPERPAD de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView (clase)](../../mfc/reference/cctrlview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CCtrlView (clase)](../../mfc/reference/cctrlview-class.md)<br/>
[CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)
