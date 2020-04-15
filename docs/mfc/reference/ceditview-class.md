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
ms.openlocfilehash: 8fbb2dc569e675ecff4ce04758a4eced40505bf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373966"
---
# <a name="ceditview-class"></a>CEditView (clase)

Un tipo de clase de vista que proporciona la funcionalidad de un control de edición de Windows y se puede utilizar para implementar funcionalidad de editor de texto simple.

## <a name="syntax"></a>Sintaxis

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|Construye un objeto de tipo `CEditView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView::FindText](#findtext)|Busca una cadena dentro del texto.|
|[CEditView::GetBufferLength](#getbufferlength)|Obtiene la longitud del búfer de caracteres.|
|[CEditView::GetEditCtrl](#geteditctrl)|Proporciona acceso `CEdit` a la `CEditView` parte de un objeto (el control de edición de Windows).|
|[CEditView::GetPrinterFont](#getprinterfont)|Recupera la fuente de impresora actual.|
|[CEditView::GetSelectedText](#getselectedtext)|Recupera la selección de texto actual.|
|[CEditView::LockBuffer](#lockbuffer)|Bloquea el búfer.|
|[CEditView::PrintInsideRect](#printinsiderect)|Representa texto dentro de un rectángulo determinado.|
|[CEditView::SerializeRaw](#serializeraw)|Serializa un `CEditView` objeto en el disco como texto sin formato.|
|[CEditView::SetPrinterFont](#setprinterfont)|Establece una nueva fuente de impresora.|
|[CEditView::SetTabStops](#settabstops)|Establece tabulaciones tanto para la visualización de la pantalla como para la impresión.|
|[CEditView::UnlockBuffer](#unlockbuffer)|Desbloquea el búfer.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Busca la siguiente aparición de una cadena de texto.|
|[CEditView::OnReplaceAll](#onreplaceall)|Reemplaza todas las apariciones de una cadena determinada con una nueva cadena.|
|[CEditView::OnReplaceSel](#onreplacesel)|Reemplaza la selección actual.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Se llama cuando una operación de búsqueda no coincide con ningún texto adicional.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Estilo predeterminado para `CEditView`objetos de tipo .|

## <a name="remarks"></a>Observaciones

La `CEditView` clase proporciona las siguientes funciones adicionales:

- Impresión.

- Busque y reemplace.

Dado `CEditView` que class es `CView`una derivada `CEditView` de class , los objetos de clase se pueden utilizar con documentos y plantillas de documento.

El `CEditView` texto de cada control se mantiene en su propio objeto de memoria global. La aplicación puede tener `CEditView` cualquier número de objetos.

Cree objetos `CEditView` de tipo si desea una ventana de edición con la funcionalidad agregada enumerada anteriormente, o si desea una funcionalidad de editor de texto simple. Un `CEditView` objeto puede ocupar todo el área de cliente de una ventana. Derive sus propias clases de agregar o modificar la funcionalidad básica, o para declarar clases que se pueden agregar a una plantilla de `CEditView` documento.

La implementación `CEditView` predeterminada de class controla los siguientes comandos: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT y ID_FILE_PRINT.

El límite de `CEditView` caracteres predeterminado \* para es (1024 1024 - 1 - 1048575). Esto se puede cambiar llamando a la EM_LIMITTEXT función del control de edición subyacente. Sin embargo, los límites son diferentes dependiendo del sistema operativo y el tipo de control de edición (una o varias líneas). Para obtener más información sobre estos límites, consulte [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Para cambiar este límite en `OnCreate()` el control, reemplace la función de la `CEditView` clase e inserte la siguiente línea de código:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Los objetos de tipo `CEditView` (o de tipos derivados de `CEditView`) tienen las siguientes limitaciones:

- `CEditView`no implementa la verdadera lo que ves es lo que obtienes (WYSIWYG) edición. Cuando hay una opción entre la legibilidad en `CEditView` la pantalla y la salida impresa coincidente, opta por la legibilidad de la pantalla.

- `CEditView`puede mostrar texto en una sola fuente. No se admite ningún formato de caracteres especial. Consulte la clase [CRichEditView](../../mfc/reference/cricheditview-class.md) para obtener más capacidades.

- La cantidad de `CEditView` texto que puede contener es limitada. Los límites son los `CEdit` mismos que para el control.

Para obtener `CEditView`más información sobre , vea Clases de [vista derivadas disponibles en MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="ceditviewceditview"></a><a name="ceditview"></a>CEditView::CEditView

Construye un objeto de tipo `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Observaciones

Después de construir el objeto, debe llamar a la [CWnd::Create](../../mfc/reference/cwnd-class.md#create) función antes de que se utilice el control de edición. Si deriva una `CEditView` clase de y la `CWinApp::AddDocTemplate`agrega a la plantilla `Create` mediante , el marco de trabajo llama a este constructor y a la función.

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView::dwStyleDefault

Contiene el estilo `CEditView` predeterminado del objeto.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Observaciones

Pase este miembro estático como el `Create` *dwStyle* parámetro de `CEditView` la función para obtener el estilo predeterminado para el objeto.

## <a name="ceditviewfindtext"></a><a name="findtext"></a>CEditView::FindText

Llame `FindText` a la `CEditView` función para buscar el búfer de texto del objeto.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
El texto que se va a encontrar.

*bSiguiente*<br/>
Especifica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda es hacia el final del búfer. Si FALSE, la dirección de búsqueda es hacia el principio del búfer.

*bCase*<br/>
Especifica si la búsqueda distingue mayúsculas de minúsculas. Si es TRUE, la búsqueda distingue mayúsculas de minúsculas. Si FALSE, la búsqueda no distingue mayúsculas de minúsculas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el texto de búsqueda; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función busca en el texto del búfer el texto especificado por *lpszFind*, comenzando en la selección actual, en la dirección especificada por *bNext*y con la sensibilidad a mayúsculas y minúsculas especificada por *bCase*. Si se encuentra el texto, establece la selección en el texto encontrado y devuelve un valor distinto de cero. Si no se encuentra el texto, la función devuelve 0.

Normalmente no es necesario `FindText` llamar a `OnFindNext`la `FindText`función a menos que invalide , que llama a .

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a>CEditView::GetBufferLength

Llame a esta función miembro para obtener el número de caracteres actualmente en el búfer del control de edición, sin incluir el terminador nulo.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud de la cadena en el búfer.

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a>CEditView::GetEditCtrl

Llame `GetEditCtrl` para obtener una referencia al control de edición utilizado por la vista de edición.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto `CEdit`.

### <a name="remarks"></a>Observaciones

Este control es de tipo [CEdit](../../mfc/reference/cedit-class.md), por lo `CEdit` que puede manipular el control de edición de Windows directamente mediante las funciones miembro.

> [!CAUTION]
> El `CEdit` uso del objeto puede cambiar el estado del control de edición de Windows subyacente. Por ejemplo, no debe cambiar la configuración de ficha mediante `CEditView` la función [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) porque almacena en caché esta configuración para su uso tanto en el control de edición como en la impresión. En su lugar, utilice [CEditView::SetTabStops](#settabstops).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a>CEditView::GetPrinterFont

Llame `GetPrinterFont` para obtener un puntero a un [CFont](../../mfc/reference/cfont-class.md) objeto que describe la fuente de impresora actual.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a `CFont` un objeto que especifica la fuente de impresora actual; NULL si no se ha establecido la fuente de la impresora. El puntero puede ser temporal y no se debe almacenar para su uso posterior.

### <a name="remarks"></a>Observaciones

Si no se ha establecido la fuente de `CEditView` la impresora, el comportamiento de impresión predeterminado de la clase es imprimir utilizando la misma fuente utilizada para la visualización.

Utilice esta función para determinar la fuente de impresora actual. Si no es la fuente de impresora deseada, utilice [CEditView::SetPrinterFont](#setprinterfont) para cambiarla.

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a>CEditView::GetSelectedText

Llamada `GetSelectedText` para copiar el `CString` texto seleccionado en un objeto, hasta el final de la selección o el carácter que precede al primer carácter de retorno de carro de la selección.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parámetros

*strResult*<br/>
Una referencia `CString` al objeto que va a recibir el texto seleccionado.

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView::LockBuffer

Llame a esta función miembro para obtener un puntero al búfer. El búfer no debe modificarse.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al búfer del control de edición.

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a>CEditView::OnFindNext

Busca en el texto del búfer el texto especificado por *lpszFind*, en la dirección especificada por *bNext*, con la sensibilidad de mayúsculas y minúsculas especificada por *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
El texto que se va a encontrar.

*bSiguiente*<br/>
Especifica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda es hacia el final del búfer. Si FALSE, la dirección de búsqueda es hacia el principio del búfer.

*bCase*<br/>
Especifica si la búsqueda distingue mayúsculas de minúsculas. Si es TRUE, la búsqueda distingue mayúsculas de minúsculas. Si FALSE, la búsqueda no distingue mayúsculas de minúsculas.

### <a name="remarks"></a>Observaciones

La búsqueda comienza al principio de la selección actual y se realiza a través de una llamada a [FindText](#findtext). En la implementación predeterminada, `OnFindNext` llama a [OnTextNotFound](#ontextnotfound) si no se encuentra el texto.

Reemplazar `OnFindNext` para cambiar `CEditView`la forma en que un objeto derivado busca texto. `CEditView`llamadas `OnFindNext` cuando el usuario elige el botón Buscar siguiente en el cuadro de diálogo Buscar estándar.

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a>CEditView::OnReplaceAll

`CEditView`llamadas `OnReplaceAll` cuando el usuario selecciona el botón Reemplazar todo en el cuadro de diálogo Reemplazar estándar.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
El texto que se va a encontrar.

*lpszReplace*<br/>
El texto para reemplazar el texto de búsqueda.

*bCase*<br/>
Especifica si la búsqueda distingue mayúsculas de minúsculas. Si es TRUE, la búsqueda distingue mayúsculas de minúsculas. Si FALSE, la búsqueda no distingue mayúsculas de minúsculas.

### <a name="remarks"></a>Observaciones

`OnReplaceAll`busca en el texto del búfer el texto especificado por *lpszFind*, con la sensibilidad a mayúsculas y minúsculas especificada por *bCase*. La búsqueda comienza al principio de la selección actual. Cada vez que se encuentra el texto de búsqueda, esta función reemplaza esa aparición del texto con el texto especificado por *lpszReplace*. La búsqueda se realiza a través de una llamada a [FindText](#findtext). En la implementación predeterminada, [OnTextNotFound](#ontextnotfound) se llama si no se encuentra el texto.

Si la selección actual no coincide con *lpszFind*, la selección se actualiza a la primera aparición del texto especificado por *lpszFind* y no se realiza una sustitución. Esto permite al usuario confirmar que esto es lo que quiere hacer cuando la selección no coincide con el texto que se va a reemplazar.

Reemplazar `OnReplaceAll` para cambiar `CEditView`la forma en que un objeto derivado reemplaza el texto.

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a>CEditView::OnReplaceSel

`CEditView`llamadas `OnReplaceSel` cuando el usuario selecciona el botón Reemplazar en el cuadro de diálogo Reemplazar estándar.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
El texto que se va a encontrar.

*bSiguiente*<br/>
Especifica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda es hacia el final del búfer. Si FALSE, la dirección de búsqueda es hacia el principio del búfer.

*bCase*<br/>
Especifica si la búsqueda distingue mayúsculas de minúsculas. Si es TRUE, la búsqueda distingue mayúsculas de minúsculas. Si FALSE, la búsqueda no distingue mayúsculas de minúsculas.

*lpszReplace*<br/>
Texto para reemplazar el texto encontrado.

### <a name="remarks"></a>Observaciones

Después de reemplazar la selección, esta función busca en el texto del búfer la siguiente aparición del texto especificado por *lpszFind*, en la dirección especificada por *bNext*, con la sensibilidad a mayúsculas y minúsculas especificada por *bCase*. La búsqueda se realiza a través de una llamada a [FindText](#findtext). Si no se encuentra el texto, [OnTextNotFound](#ontextnotfound) se llama.

Reemplazar `OnReplaceSel` para cambiar `CEditView`la forma en que un objeto derivado reemplaza el texto seleccionado.

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a>CEditView::OnTextNotFound

Invalide esta función para cambiar la `MessageBeep`implementación predeterminada, que llama a la función de Windows.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
El texto que se va a encontrar.

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView::PrintInsideRect

Llame `PrintInsideRect` para imprimir texto en el rectángulo especificado por *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto del dispositivo de impresora.

*rectLayout*<br/>
Referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o [RECT estructura](/windows/win32/api/windef/ns-windef-rect) que especifica el rectángulo en el que se va a representar el texto.

*nIndexStart*<br/>
Index dentro del búfer del primer carácter que se va a representar.

*nIndexStop*<br/>
Index dentro del búfer del carácter que sigue al último carácter que se va a representar.

### <a name="return-value"></a>Valor devuelto

El índice del siguiente carácter que se va a imprimir (es decir, el carácter que sigue al último carácter representado).

### <a name="remarks"></a>Observaciones

Si `CEditView` el control no tiene el estilo ES_AUTOHSCROLL, el texto se ajusta dentro del rectángulo de representación. Si el control tiene el estilo ES_AUTOHSCROLL, el texto se recorta en el borde derecho del rectángulo.

El `rect.bottom` elemento del objeto *rectLayout* se cambia para que las dimensiones del rectángulo definan la parte del rectángulo original que ocupa el texto.

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView::SerializeRaw

Llame `SerializeRaw` para `CArchive` que un objeto lea `CEditView` o escriba el texto del objeto en un archivo de texto.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
Referencia al `CArchive` objeto que almacena el texto serializado.

### <a name="remarks"></a>Observaciones

`SerializeRaw`difiere de `CEditView`la implementación `Serialize` interna de en que lee y escribe sólo el texto, sin datos anteriores de descripción de objetos.

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a>CEditView::SetPrinterFont

Llame `SetPrinterFont` para establecer la fuente de la impresora en la fuente especificada por *pFont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
Puntero a un objeto `CFont`de tipo . Si ES NULL, la fuente utilizada para imprimir se basa en la fuente de visualización.

### <a name="remarks"></a>Observaciones

Si desea que la vista utilice siempre una fuente `SetPrinterFont` determinada para imprimir, incluya una llamada a la función de la `OnPreparePrinting` clase. Se llama a esta función virtual antes de que se produzca la impresión, por lo que el cambio de fuente tiene lugar antes de imprimir el contenido de la vista.

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a>CEditView::SetTabStops

Llame a esta función para establecer las tabulaciones utilizadas para la visualización y la impresión.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parámetros

*nTabStops*<br/>
Anchura de cada tabulación, en unidades de diálogo.

### <a name="remarks"></a>Observaciones

Solo se admite un ancho de tabulación único. ( `CEdit` los objetos admiten varios anchos de tabulación.) Las anchuras se encuentran en unidades de cuadro de diálogo, que equivalen a una cuarta parte del ancho medio de caracteres (solo en mayúsculas y minúsculas alfabéticas) de la fuente utilizada en el momento de imprimir o mostrar. No debe `CEdit::SetTabStops` usar `CEditView` porque debe almacenar en caché el valor de tabulación.

Esta función modifica sólo las fichas del objeto para el que se llama. Para cambiar las tabulaciones de cada `CEditView` objeto de `SetTabStops` la aplicación, llame a la función de cada objeto.

### <a name="example"></a>Ejemplo

Este fragmento de código establece las tabulaciones del control en cada cuarto carácter midiendo cuidadosamente la fuente que utiliza el control.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView::UnlockBuffer

Llame a esta función miembro para desbloquear el búfer.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Observaciones

Llame `UnlockBuffer` después de haber terminado de usar el puntero devuelto por [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[Clase CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Clase CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Clase CRichEditView](../../mfc/reference/cricheditview-class.md)
