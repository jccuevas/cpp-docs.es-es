---
title: Clase CEditView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38b8389418657499d43263399f1a05b3a0326c84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ceditview-class"></a>Clase CEditView
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
|[CEditView::FindText](#findtext)|Busca una cadena en el texto.|  
|[CEditView::GetBufferLength](#getbufferlength)|Obtiene la longitud del búfer de caracteres.|  
|[CEditView::GetEditCtrl](#geteditctrl)|Proporciona acceso a la `CEdit` parte de una `CEditView` objeto (control de edición de Windows).|  
|[CEditView::GetPrinterFont](#getprinterfont)|Recupera la fuente actual de la impresora.|  
|[CEditView::GetSelectedText](#getselectedtext)|Recupera la selección de texto actual.|  
|[CEditView::LockBuffer](#lockbuffer)|Bloquea el búfer.|  
|[CEditView::PrintInsideRect](#printinsiderect)|Representa el texto dentro de un rectángulo determinado.|  
|[CEditView:: SerializeRaw](#serializeraw)|Serializa un `CEditView` objeto en el disco como texto sin formato.|  
|[CEditView::SetPrinterFont](#setprinterfont)|Establece una nueva fuente de impresora.|  
|[CEditView::SetTabStops](#settabstops)|Establece las tabulaciones de pantalla e impresión.|  
|[CEditView::UnlockBuffer](#unlockbuffer)|Desbloquea el búfer.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|Busca la siguiente aparición de una cadena de texto.|  
|[CEditView::OnReplaceAll](#onreplaceall)|Reemplaza todas las apariciones de una cadena determinada con una nueva cadena.|  
|[CEditView::OnReplaceSel](#onreplacesel)|Reemplaza la selección actual.|  
|[CEditView::OnTextNotFound](#ontextnotfound)|Se llama cuando se produce un error en una operación de búsqueda para que coincida con cualquier texto adicional.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|Estilo predeterminado para objetos de tipo **CEditView.**|  
  
## <a name="remarks"></a>Comentarios  
 La `CEditView` clase proporciona las siguientes funciones adicionales:  
  
-   Imprimir.  
  
-   Buscar y reemplazar.  
  
 Dado que clase `CEditView` es un derivado de la clase `CView`, objetos de la clase `CEditView` puede utilizarse con documentos y plantillas de documento.  
  
 Cada `CEditView` texto del control se mantiene en su propio objeto de memoria global. La aplicación puede tener cualquier número de `CEditView` objetos.  
  
 Crear objetos de tipo `CEditView` si desea que una ventana de edición con la funcionalidad agregada mencionada anteriormente, o si desea que la funcionalidad de editor de texto simple. Un `CEditView` objeto puede ocupar toda el área cliente de una ventana. Derivar sus propias clases de `CEditView` para agregar o modificar la funcionalidad básica, o para declarar las clases que pueden agregarse a una plantilla de documento.  
  
 La implementación predeterminada de la clase `CEditView` controla los comandos siguientes: **ID_EDIT_SELECT_ALL**, **ID_EDIT_FIND**, **ID_EDIT_REPLACE**, **ID_EDIT_REPEAT**, y **ID_FILE_PRINT**.  
  
 El límite de caracteres predeterminado de `CEditView` es (1024 \* 1024-1 = 1048575). Esto puede cambiarse mediante una llamada a la **EM_LIMITTEXT** control de edición de la función de subyacente. Sin embargo, los límites son diferentes según el sistema operativo y el tipo de edición control (simples o varias líneas). Para obtener más información sobre estos límites, consulte [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607).  
  
 Para cambiar este límite en el control, reemplace el `OnCreate()` funciona para su `CEditView` clase e inserte la siguiente línea de código:  
  
 [!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 Objetos de tipo `CEditView` (o de tipos derivados de `CEditView`) tienen las siguientes limitaciones:  
  
- `CEditView`implementar true lo que ve es lo que se obtiene (WYSIWYG) de edición. Cuando hay una opción entre la legibilidad en la pantalla y la salida impresa coincidente, `CEditView` opta por lectura en pantalla.  
  
- `CEditView`puede mostrar texto en solo una única fuente. No se admite ningún formato de carácter especial. Vea la clase [CRichEditView](../../mfc/reference/cricheditview-class.md) capacidades mayor.  
  
-   La cantidad de texto un `CEditView` puede contener está limitado. Los límites son los mismos que para el `CEdit` control.  
  
 Para obtener más información sobre `CEditView`, consulte [derivadas vista de clases disponibles en MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="ceditview"></a>CEditView::CEditView  
 Construye un objeto de tipo `CEditView`.  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el objeto, se debe llamar a la [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) función antes de que se usa el control de edición. Si se deriva una clase de `CEditView` y lo agrega a la plantilla desde `CWinApp::AddDocTemplate`, el marco de trabajo llama a este constructor de ambos y **crear** (función).  
  
##  <a name="dwstyledefault"></a>CEditView::dwStyleDefault  
 Contiene el estilo predeterminado de la `CEditView` objeto.  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>Comentarios  
 Pasar este miembro estático como el `dwStyle` parámetro de la **crear** función para obtener el estilo predeterminado para el `CEditView` objeto.  
  
##  <a name="findtext"></a>CEditView::FindText  
 Llame a la `FindText` función para buscar el `CEditView` búfer de texto del objeto.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFind`  
 El texto que se encuentra.  
  
 `bNext`  
 Especifica la dirección de la búsqueda. Si **TRUE**, la dirección de búsqueda es hacia el final del búfer. Si **FALSE**, la dirección de búsqueda es hacia el principio del búfer.  
  
 `bCase`  
 Especifica si la búsqueda distingue entre mayúsculas y minúsculas. Si **TRUE**, la búsqueda no distingue entre mayúsculas y minúsculas. Si **FALSE**, la búsqueda no distingue entre mayúsculas y minúsculas.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se encuentra el texto de búsqueda; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función busca en el texto en el búfer para el texto especificado por `lpszFind`, empezando por la selección actual, en la dirección especificada por `bNext`y entre mayúsculas y minúsculas especificados por `bCase`. Si se encuentra el texto, la selección se establece en el texto se encuentra y devuelve un valor distinto de cero. Si no se encuentra el texto, la función devuelve 0.  
  
 Normalmente no es necesario llamar a la `FindText` función a menos que invalide `OnFindNext`, que llama `FindText`.  
  
##  <a name="getbufferlength"></a>CEditView::GetBufferLength  
 Llame a esta función miembro para obtener el número de caracteres actualmente en el búfer del control de edición, sin incluir el terminador nulo.  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la cadena en el búfer.  
  
##  <a name="geteditctrl"></a>CEditView::GetEditCtrl  
 Llame a `GetEditCtrl` para obtener una referencia al control de edición utilizado por la vista de edición.  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia a un objeto `CEdit`.  
  
### <a name="remarks"></a>Comentarios  
 Este control es de tipo [CEdit](../../mfc/reference/cedit-class.md), por lo que se puede manipular el control de edición de Windows directamente mediante el `CEdit` funciones miembro.  
  
> [!CAUTION]
>  Mediante la `CEdit` objeto puede cambiar el estado de las ventanas subyacentes del control de edición. Por ejemplo, no debe cambiar la configuración de las tabulaciones con la [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) funcione porque `CEditView` almacena en caché estos valores para su uso en el control de edición y en la impresión. En su lugar, use [CEditView::SetTabStops](#settabstops).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>CEditView::GetPrinterFont  
 Llame a `GetPrinterFont` para obtener un puntero a un [CFont](../../mfc/reference/cfont-class.md) objeto que describe la fuente actual de la impresora.  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CFont` objeto que especifica la fuente actual de la impresora; **NULL** si no se ha establecido la fuente de impresora. El puntero puede ser temporal y no se debe almacenar para su uso posterior.  
  
### <a name="remarks"></a>Comentarios  
 Si la fuente de impresora no se estableció, el valor predeterminado imprimir el comportamiento de la `CEditView` clase es imprimir con la misma fuente que se usa para mostrar.  
  
 Utilice esta función para determinar la fuente actual de la impresora. Si no es la fuente de la impresora deseada, utilice [CEditView::SetPrinterFont](#setprinterfont) para cambiarlo.  
  
##  <a name="getselectedtext"></a>CEditView::GetSelectedText  
 Llame a `GetSelectedText` para copiar el texto seleccionado en un `CString` objeto, hasta el final de la selección o el carácter que precede el primer carácter de retorno de carro de la selección.  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `strResult`  
 Una referencia a la `CString` objeto que va a recibir el texto seleccionado.  
  
##  <a name="lockbuffer"></a>CEditView::LockBuffer  
 Llame a esta función miembro para obtener un puntero al búfer. No se debe modificar el búfer.  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al búfer del control de edición.  
  
##  <a name="onfindnext"></a>CEditView::OnFindNext  
 Busca el texto en el búfer para el texto especificado por `lpszFind`, en la dirección especificada por `bNext`, con mayúsculas y minúsculas especificados por `bCase`.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFind`  
 El texto que se encuentra.  
  
 `bNext`  
 Especifica la dirección de la búsqueda. Si **TRUE**, la dirección de búsqueda es hacia el final del búfer. Si **FALSE**, la dirección de búsqueda es hacia el principio del búfer.  
  
 `bCase`  
 Especifica si la búsqueda distingue entre mayúsculas y minúsculas. Si **TRUE**, la búsqueda no distingue entre mayúsculas y minúsculas. Si **FALSE**, la búsqueda no distingue entre mayúsculas y minúsculas.  
  
### <a name="remarks"></a>Comentarios  
 La búsqueda comienza al principio de la selección actual y se logra a través de una llamada a [FindText](#findtext). En la implementación predeterminada, `OnFindNext` llamadas [OnTextNotFound](#ontextnotfound) si no se encuentra el texto.  
  
 Invalidar `OnFindNext` para cambiar la forma en que un `CEditView`-objeto derivado busca texto. `CEditView`llamadas `OnFindNext` cuando el usuario elige el botón Buscar siguiente en el cuadro de diálogo de búsqueda estándar.  
  
##  <a name="onreplaceall"></a>CEditView::OnReplaceAll  
 `CEditView`llamadas `OnReplaceAll` cuando el usuario selecciona el botón Reemplazar todo en el cuadro de diálogo Reemplazar estándar.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFind`  
 El texto que se encuentra.  
  
 `lpszReplace`  
 El texto que reemplazará el texto de búsqueda.  
  
 `bCase`  
 Especifica si la búsqueda distingue mayúsculas de minúsculas. Si **TRUE**, la búsqueda no distingue entre mayúsculas y minúsculas. Si **FALSE**, la búsqueda no distingue entre mayúsculas y minúsculas.  
  
### <a name="remarks"></a>Comentarios  
 `OnReplaceAll`busca el texto en el búfer para el texto especificado por `lpszFind`, con mayúsculas y minúsculas especificados por `bCase`. La búsqueda comienza al principio de la selección actual. Cada vez que se encuentra el texto de búsqueda, esta función reemplaza esa aparición del texto con el texto especificado por `lpszReplace`. La búsqueda se logra a través de una llamada a [FindText](#findtext). En la implementación predeterminada, [OnTextNotFound](#ontextnotfound) se llama si no se encuentra el texto.  
  
 Si la selección actual no coincide con `lpszFind`, se actualiza la selección a la primera aparición del texto especificado por `lpszFind` y no se realiza un reemplazo. Esto permite al usuario confirmar que esto es lo desean hacer cuando la selección no coincide con el texto que se debe reemplazar.  
  
 Invalidar `OnReplaceAll` para cambiar la forma en que un `CEditView`-objeto derivado reemplaza el texto.  
  
##  <a name="onreplacesel"></a>CEditView::OnReplaceSel  
 `CEditView`llamadas `OnReplaceSel` cuando el usuario selecciona el botón Reemplazar en el cuadro de diálogo Reemplazar estándar.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFind`  
 El texto que se encuentra.  
  
 `bNext`  
 Especifica la dirección de la búsqueda. Si **TRUE**, la dirección de búsqueda es hacia el final del búfer. Si **FALSE**, la dirección de búsqueda es hacia el principio del búfer.  
  
 `bCase`  
 Especifica si la búsqueda distingue entre mayúsculas y minúsculas. Si **TRUE**, la búsqueda no distingue entre mayúsculas y minúsculas. Si **FALSE**, la búsqueda no distingue entre mayúsculas y minúsculas.  
  
 `lpszReplace`  
 El texto que reemplazará el texto encontrado.  
  
### <a name="remarks"></a>Comentarios  
 Después de reemplazar la selección, esta función busca en el búfer para la siguiente repetición del texto especificado por el texto `lpszFind`, en la dirección especificada por `bNext`, con mayúsculas y minúsculas especificados por `bCase`. La búsqueda se logra a través de una llamada a [FindText](#findtext). Si no se encuentra el texto, [OnTextNotFound](#ontextnotfound) se llama.  
  
 Invalidar `OnReplaceSel` para cambiar la forma en que un `CEditView`-objeto derivado reemplaza el texto seleccionado.  
  
##  <a name="ontextnotfound"></a>CEditView::OnTextNotFound  
 Reemplace esta función para cambiar la implementación predeterminada, que llama a la función de Windows **MessageBeep**.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszFind`  
 El texto que se encuentra.  
  
##  <a name="printinsiderect"></a>CEditView::PrintInsideRect  
 Llame a `PrintInsideRect` para imprimir texto en el rectángulo especificado por *rectLayout*.  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero al contexto de dispositivo de impresora.  
  
 *rectLayout*  
 Referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o [estructura RECT](../../mfc/reference/rect-structure1.md) especifica el rectángulo en el que es el texto que se representará.  
  
 `nIndexStart`  
 Índice en el búfer del primer carácter que se representará.  
  
 `nIndexStop`  
 Índice en el búfer del carácter siguiente al último carácter que se representará.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del siguiente carácter que se va a imprimir (es decir, el carácter siguiente al último carácter representando).  
  
### <a name="remarks"></a>Comentarios  
 Si el `CEditView` control no tiene el estilo **ES_AUTOHSCROLL**, el texto se ajusta dentro del rectángulo de presentación. Si el control tiene el estilo **ES_AUTOHSCROLL**, el texto se recorta en el borde derecho del rectángulo.  
  
 El **rect.bottom** elemento de la *rectLayout* objeto se cambia para que las dimensiones del rectángulo definen la parte del rectángulo original que está ocupada por el texto.  
  
##  <a name="serializeraw"></a>CEditView:: SerializeRaw  
 Llame a `SerializeRaw` tener un `CArchive` objeto leer o escribir el texto en la `CEditView` objeto en un archivo de texto.  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 `ar`  
 Referencia a la `CArchive` objeto que almacena el texto serializado.  
  
### <a name="remarks"></a>Comentarios  
 `SerializeRaw`difiere de `CEditView`de implementación interna de `Serialize` en que se lee y escribe sólo el texto, sin anteponer datos de la descripción del objeto.  
  
##  <a name="setprinterfont"></a>CEditView::SetPrinterFont  
 Llame a `SetPrinterFont` para establecer la fuente de la impresora para la fuente especificada por `pFont`.  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFont`  
 Un puntero a un objeto de tipo `CFont`. Si **NULL**, la fuente utilizada para la impresión se basa en la fuente de pantalla.  
  
### <a name="remarks"></a>Comentarios  
 Si desea que la vista que utilice siempre una fuente concreta para impresión, incluya una llamada a `SetPrinterFont` en la clase `OnPreparePrinting` (función). Esta función virtual se llama antes de que se produce la impresión, por lo que el cambio de fuente tiene lugar antes de que se imprime el contenido de la vista.  
  
##  <a name="settabstops"></a>CEditView::SetTabStops  
 Llame a esta función para establecer las posiciones de tabulación utilizadas para mostrar e imprimirlos.  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>Parámetros  
 `nTabStops`  
 Ancho de cada tabulación, en unidades de cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Se admite solo un único ancho de tabulación. ( `CEdit` objetos admiten varios anchos de ficha.) Anchos se encuentran en unidades de cuadro de diálogo, que ser igual a un cuarto del ancho promedio de los caracteres (basado en caracteres en mayúsculas y minúsculas es un carácter alfabético solo) de la fuente utilizada en el momento de impresión o mostrar. No se debe usar `CEdit::SetTabStops` porque `CEditView` debe almacenar en caché el valor de tabulación.  
  
 Esta función modifica sólo las fichas del objeto para el que se llama. Para cambiar la ficha tabulaciones para cada `CEditView` de objetos en la aplicación, llamar a cada objeto `SetTabStops` función.  
  
### <a name="example"></a>Ejemplo  
 Este fragmento de código establece las posiciones de tabulación del control para cada cuarto carácter midiendo cuidadosamente la fuente que utiliza el control.  
  
 [!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>CEditView::UnlockBuffer  
 Llame a esta función miembro para desbloquear el búfer.  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a `UnlockBuffer` después de que haya terminado de utilizar el puntero devuelto por [LockBuffer](#lockbuffer).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC SUPERPAD](../../visual-cpp-samples.md)   
 [Clase de CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [Clase de CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)
