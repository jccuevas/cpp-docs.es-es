---
title: CFontDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: b711ca65e552d495e466ea2e46a6779cf43ecbe3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767749"
---
# <a name="cfontdialog-class"></a>CFontDialog (clase)

Permite incorporar un cuadro de diálogo de selección de fuente en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Construye un objeto `CFontDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[CFontDialog::GetCharFormat](#getcharformat)|Recupera el formato de caracteres de la fuente seleccionada.|
|[CFontDialog::GetColor](#getcolor)|Devuelve el color de la fuente seleccionada.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Asigna las características de la fuente seleccionada actualmente a un `LOGFONT` estructura.|
|[CFontDialog::GetFaceName](#getfacename)|Devuelve el nombre de fuente de la fuente seleccionada.|
|[CFontDialog::GetSize](#getsize)|Devuelve el tamaño de punto de la fuente seleccionada.|
|[CFontDialog::GetStyleName](#getstylename)|Devuelve el nombre del estilo de la fuente seleccionada.|
|[CFontDialog::GetWeight](#getweight)|Devuelve el grosor de la fuente seleccionada.|
|[CFontDialog::IsBold](#isbold)|Determina si la fuente es negrita.|
|[CFontDialog::IsItalic](#isitalic)|Determina si la fuente es cursiva.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Determina si la fuente se muestra con el tachado.|
|[CFontDialog::IsUnderline](#isunderline)|Determina si la fuente está subrayada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Una estructura utilizada para personalizar un `CFontDialog` objeto.|

## <a name="remarks"></a>Comentarios

Un `CFontDialog` objeto es un cuadro de diálogo con una lista de fuentes que están instalados actualmente en el sistema. El usuario puede seleccionar una fuente concreta en la lista, y esta selección es, a continuación, informar a la aplicación.

Para construir un `CFontDialog` de objeto, utilice el constructor proporcionado o derivar una nueva subclase y usar su propio constructor personalizado.

Una vez un `CFontDialog` se ha construido el objeto, puede usar el `m_cf` estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. El [m_cf](#m_cf) estructura es de tipo [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta). Para obtener más información sobre esta estructura, consulte el SDK de Windows.

Después de inicializar los controles del objeto de cuadro de diálogo, llame a la `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar una fuente. `DoModal` Devuelve si el usuario seleccionó el botón Aceptar (IDOK) o Cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede usar uno de `CFontDialog`de las funciones miembro para recuperar la información de entrada por el usuario.

Puede usar el Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) función para determinar si se produjo un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, consulte el SDK de Windows.

`CFontDialog` se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase de `CFontDialog`, proporcione una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base.

Personalización de la función de enlace no es necesario.

Para obtener más información sobre el uso de `CFontDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog

Construye un objeto `CFontDialog`.

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*plfInitial*<br/>
Un puntero a un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura de datos que le permite establecer algunas de las características de la fuente.

*charFormat*<br/>
Un puntero a un [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) estructura de datos que le permite establecer algunas de las características de la fuente en un amplio control de edición.

*dwFlags*<br/>
Especifica uno o más marcadores CHOOSEFONT. Se pueden combinar uno o más valores preestablecidos mediante el operador bit a bit OR. Si modifica el miembro de estructura de `m_cf.Flag`, procure usar un operador bit a bit OR en los cambios que realice para que el comportamiento predeterminado siga intacto. Para obtener más información sobre cada una de estas marcas, vea la descripción de la [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) estructura en el SDK de Windows.

*pdcPrinter*<br/>
Puntero a un contexto de dispositivo de impresora. Si se suministra, este parámetro apunta a un contexto de dispositivo de impresora correspondiente a la impresora en la que las fuentes se van a seleccionar.

*pParentWnd*<br/>
Puntero a la ventana principal o propietaria del cuadro de diálogo de fuentes.

### <a name="remarks"></a>Comentarios

Observe que el constructor rellena automáticamente los miembros de la estructura `CHOOSEFONT`. Esto solo debe modificarse en caso de que quiera un cuadro de diálogo de fuentes distinto al predeterminado.

> [!NOTE]
>  La primera versión de esta función solo existe cuando no hay compatibilidad con el control de edición enriquecida.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>  CFontDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo de fuentes comunes de Windows y permitir al usuario elegir una fuente.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) función para determinar si se produjo un error.

IDOK e IDCANCEL son las constantes que indican si el usuario seleccionó el botón Aceptar o Cancelar.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo fuente mediante el establecimiento de los miembros de la [m_cf](#m_cf) estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, se puede llamar a otra funciones miembro para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.

### <a name="example"></a>Ejemplo

  Consulte los ejemplos de [CFontDialog::CFontDialog](#cfontdialog) y [CFontDialog::GetColor](#getcolor).

##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat

Recupera el formato de caracteres de la fuente seleccionada.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parámetros

*cf*<br/>
Un [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) estructura que contiene información sobre el formato de caracteres de la fuente seleccionada.

##  <a name="getcolor"></a>  CFontDialog::GetColor

Llame a esta función para recuperar el color de fuente seleccionado.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Color de la fuente seleccionada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont

Llame a esta función para asignar las características de la fuente seleccionada actualmente a los miembros de un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) estructura.

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parámetros

*lplf*<br/>
Un puntero a un `LOGFONT` estructura.

### <a name="remarks"></a>Comentarios

Otros `CFontDialog` se proporcionan funciones de miembro para tener acceso a características individuales de la fuente actual.

Si esta función se llama durante una llamada a [DoModal](#domodal), devuelve la selección actual en el momento (lo que ve el usuario o ha cambiado en el cuadro de diálogo). Si se llama a esta función después de llamar a `DoModal` (solo si `DoModal` devuelve IDOK), devuelve lo que el usuario realmente está seleccionado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>  CFontDialog::GetFaceName

Llame a esta función para recuperar el nombre de fuente de la fuente seleccionada.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de fuente de la fuente seleccionada en el `CFontDialog` cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>  CFontDialog::GetSize

Llame a esta función para recuperar el tamaño de la fuente seleccionada.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de fuente, en décimas de un punto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>  CFontDialog::GetStyleName

Llame a esta función para recuperar el nombre del estilo de la fuente seleccionada.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de estilo de la fuente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>  CFontDialog::GetWeight

Llame a esta función para recuperar el peso de la fuente seleccionada.

```
int GetWeight() const;
```

### <a name="return-value"></a>Valor devuelto

El peso de la fuente seleccionada.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre el peso de una fuente, consulte [CFont:: CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>  CFontDialog::IsBold

Llame a esta función para determinar si la fuente seleccionada está en negrita.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene la característica de negrita habilitada; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>  CFontDialog::IsItalic

Llame a esta función para determinar si la fuente seleccionada está en cursiva.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene la característica de cursiva habilitada; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut

Llame a esta función para determinar si la fuente seleccionada se muestra con el tachado.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene la característica de tachado habilitada; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>  CFontDialog::IsUnderline

Llame a esta función para determinar si la fuente seleccionada está subrayada.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene la característica de subrayado habilitada; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

Una estructura cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Comentarios

Después de crear un `CFontDialog` objeto, puede usar `m_cf` modificar varios aspectos del cuadro de diálogo antes de llamar a la `DoModal` función miembro. Para obtener más información sobre esta estructura, vea [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
