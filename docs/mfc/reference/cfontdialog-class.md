---
title: Clase CFontDialog
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
ms.openlocfilehash: 6a8e24b68f377235c1f1e21fbcd5618aebbe299a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755012"
---
# <a name="cfontdialog-class"></a>Clase CFontDialog

Le permite incorporar un cuadro de diálogo de selección de fuentes en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Construye un objeto `CFontDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[CFontDialog::GetCharFormat](#getcharformat)|Recupera el formato de caracteres de la fuente seleccionada.|
|[CFontDialog::GetColor](#getcolor)|Devuelve el color de la fuente seleccionada.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Asigna las características de la fuente `LOGFONT` seleccionada actualmente a una estructura.|
|[CFontDialog::GetFaceName](#getfacename)|Devuelve el nombre de la cara de la fuente seleccionada.|
|[CFontDialog::GetSize](#getsize)|Devuelve el tamaño de punto de la fuente seleccionada.|
|[CFontDialog::GetStyleName](#getstylename)|Devuelve el nombre de estilo de la fuente seleccionada.|
|[CFontDialog::GetWeight](#getweight)|Devuelve el peso de la fuente seleccionada.|
|[CFontDialog::IsBold](#isbold)|Determina si la fuente está en negrita.|
|[CFontDialog::Isitalic](#isitalic)|Determina si la fuente está en cursiva.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Determina si la fuente se muestra con tachado.|
|[CFontDialog::IsUnderline](#isunderline)|Determina si la fuente está subrayada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Estructura utilizada para `CFontDialog` personalizar un objeto.|

## <a name="remarks"></a>Observaciones

Un `CFontDialog` objeto es un cuadro de diálogo con una lista de fuentes que están instaladas actualmente en el sistema. El usuario puede seleccionar una fuente determinada de la lista y, a continuación, esta selección se notifica a la aplicación.

Para construir `CFontDialog` un objeto, utilice el constructor proporcionado o derive una nueva subclase y utilice su propio constructor personalizado.

Una `CFontDialog` vez construido un objeto, puede `m_cf` utilizar la estructura para inicializar los valores o estados de los controles en el cuadro de diálogo. La estructura [m_cf](#m_cf) es de tipo [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Para obtener más información sobre esta estructura, consulte el Windows SDK.

Después de inicializar los controles del `DoModal` objeto de cuadro de diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar una fuente. `DoModal`devuelve si el usuario ha seleccionado el botón Aceptar (IDOK) o Cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede `CFontDialog`usar una de las funciones miembro de 's para recuperar la información introducida por el usuario.

Puede usar la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, consulte el Windows SDK.

`CFontDialog`depende del COMMDLG. DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de `CFontDialog`diálogo, derive una clase de , proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes sin procesar deben pasarse a la clase base.

No es necesario personalizar la función de gancho.

Para obtener más `CFontDialog`información sobre el uso de , vea [Clases](../../mfc/common-dialog-classes.md)de cuadro de diálogo comunes .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a>CFontDialog::CFontDialog

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
Puntero a una estructura de datos [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) que permite establecer algunas de las características de la fuente.

*charFormat*<br/>
Puntero a una estructura de datos [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) que permite establecer algunas de las características de la fuente en un control de edición enriquecido.

*dwFlags*<br/>
Especifica uno o más marcadores CHOOSEFONT. Se pueden combinar uno o más valores preestablecidos mediante el operador bit a bit OR. Si modifica el miembro de estructura de `m_cf.Flag`, procure usar un operador bit a bit OR en los cambios que realice para que el comportamiento predeterminado siga intacto. Para obtener más información sobre cada una de estas marcas, consulte la descripción de la estructura [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) en el Windows SDK.

*pdcPrinter*<br/>
Puntero a un contexto de dispositivo de impresora. Si se suministra, este parámetro apunta a un contexto de dispositivo de impresora correspondiente a la impresora en la que las fuentes se van a seleccionar.

*pParentWnd*<br/>
Puntero a la ventana principal o propietaria del cuadro de diálogo de fuentes.

### <a name="remarks"></a>Observaciones

Observe que el constructor rellena automáticamente los miembros de la estructura `CHOOSEFONT`. Esto solo debe modificarse en caso de que quiera un cuadro de diálogo de fuentes distinto al predeterminado.

> [!NOTE]
> La primera versión de esta función solo existe cuando no hay compatibilidad con el control de edición enriquecida.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a>CFontDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo de fuente común de Windows y permitir al usuario elegir una fuente.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK e IDCANCEL son constantes que indican si el usuario ha seleccionado el botón Aceptar o Cancelar.

### <a name="remarks"></a>Observaciones

Si desea inicializar los distintos controles de cuadro de diálogo de fuente `DoModal`estableciendo miembros de la [estructura m_cf,](#m_cf) debe hacerlo antes de llamar a , pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la configuración o la información introducida por el usuario en el cuadro de diálogo.

### <a name="example"></a>Ejemplo

  Vea los ejemplos de [CFontDialog::CFontDialog](#cfontdialog) y [CFontDialog::GetColor](#getcolor).

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a>CFontDialog::GetCharFormat

Recupera el formato de caracteres de la fuente seleccionada.

```cpp
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parámetros

*Cf*<br/>
Estructura [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) que contiene información sobre el formato de caracteres de la fuente seleccionada.

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a>CFontDialog::GetColor

Llame a esta función para recuperar el color de fuente seleccionado.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Color de la fuente seleccionada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

Llame a esta función para asignar las características de la fuente seleccionada actualmente a los miembros de una estructura [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```cpp
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parámetros

*lplf*<br/>
Un puntero `LOGFONT` a una estructura.

### <a name="remarks"></a>Observaciones

Se `CFontDialog` proporcionan otras funciones miembro para acceder a las características individuales de la fuente actual.

Si se llama a esta función durante una llamada a [DoModal](#domodal), devuelve la selección actual en el momento (lo que el usuario ve o ha cambiado en el cuadro de diálogo). Si se llama a esta `DoModal` función `DoModal` después de una llamada a (solo si devuelve IDOK), devuelve lo que el usuario realmente seleccionó.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a>CFontDialog::GetFaceName

Llame a esta función para recuperar el nombre de la cara de la fuente seleccionada.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la cara `CFontDialog` de la fuente seleccionada en el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a>CFontDialog::GetSize

Llame a esta función para recuperar el tamaño de la fuente seleccionada.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de la fuente, en décimas de punto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a>CFontDialog::GetStyleName

Llame a esta función para recuperar el nombre de estilo de la fuente seleccionada.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de estilo de la fuente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a>CFontDialog::GetWeight

Llame a esta función para recuperar el peso de la fuente seleccionada.

```
int GetWeight() const;
```

### <a name="return-value"></a>Valor devuelto

El peso de la fuente seleccionada.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre el peso de una fuente, vea [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a>CFontDialog::IsBold

Llame a esta función para determinar si la fuente seleccionada está en negrita.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene habilitada la característica Negrita; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a>CFontDialog::Isitalic

Llame a esta función para determinar si la fuente seleccionada está en cursiva.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene habilitada la característica cursiva; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a>CFontDialog::IsStrikeOut

Llame a esta función para determinar si la fuente seleccionada se muestra con tachado.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene activada la característica Strikeout; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a>CFontDialog::IsUnderline

Llame a esta función para determinar si la fuente seleccionada está subrayada.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene habilitada la característica Subrayado; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a>CFontDialog::m_cf

Estructura cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Observaciones

Después de `CFontDialog` construir un `m_cf` objeto, puede usar para modificar varios `DoModal` aspectos del cuadro de diálogo antes de llamar a la función miembro. Para obtener más información sobre esta estructura, vea [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
