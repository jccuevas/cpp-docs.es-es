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
ms.openlocfilehash: c0d0c37d055d9b337f7b709b4ee3d299daae7658
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741558"
---
# <a name="cfontdialog-class"></a>Clase CFontDialog

Permite incorporar un cuadro de diálogo de selección de fuente en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Construye un objeto `CFontDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite que el usuario realice una selección.|
|[CFontDialog::GetCharFormat](#getcharformat)|Recupera el formato de caracteres de la fuente seleccionada.|
|[CFontDialog::GetColor](#getcolor)|Devuelve el color de la fuente seleccionada.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Asigna las características de la fuente seleccionada actualmente a una `LOGFONT` estructura.|
|[CFontDialog::GetFaceName](#getfacename)|Devuelve el nombre de la fuente seleccionada.|
|[CFontDialog::GetSize](#getsize)|Devuelve el tamaño en puntos de la fuente seleccionada.|
|[CFontDialog::GetStyleName](#getstylename)|Devuelve el nombre de estilo de la fuente seleccionada.|
|[CFontDialog::GetWeight](#getweight)|Devuelve el peso de la fuente seleccionada.|
|[CFontDialog::IsBold](#isbold)|Determina si la fuente está en negrita.|
|[CFontDialog::IsItalic](#isitalic)|Determina si la fuente está en cursiva.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Determina si la fuente se muestra con tachado.|
|[CFontDialog::IsUnderline](#isunderline)|Determina si la fuente está subrayada.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Estructura utilizada para personalizar un `CFontDialog` objeto.|

## <a name="remarks"></a>Comentarios

Un `CFontDialog` objeto es un cuadro de diálogo con una lista de fuentes actualmente instaladas en el sistema. El usuario puede seleccionar una fuente determinada de la lista y, a continuación, esta selección se devuelve a la aplicación.

Para construir un `CFontDialog` objeto, use el constructor proporcionado o derive una nueva subclase y use su propio constructor personalizado.

Una vez `CFontDialog` construido un objeto, puede utilizar la `m_cf` estructura para inicializar los valores o los Estados de los controles en el cuadro de diálogo. La estructura [m_cf](#m_cf) es de tipo [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Para obtener más información sobre esta estructura, vea el Windows SDK.

Después de inicializar los controles del objeto de cuadro `DoModal` de diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir que el usuario seleccione una fuente. `DoModal`Devuelve si el usuario seleccionó el botón Aceptar (IDOK) o cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede usar una de las `CFontDialog`funciones miembro de para recuperar la información introducida por el usuario.

Puede usar la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, vea el Windows SDK.

`CFontDialog`se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3,1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase `CFontDialog`de, proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base.

No es necesaria la personalización de la función de enlace.

Para obtener más información sobre `CFontDialog`el uso de, vea [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs. h

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
Puntero a una estructura de datos [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) que permite establecer algunas de las características de la fuente.

*charFormat*<br/>
Puntero a una estructura de datos [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) que permite establecer algunas de las características de la fuente en un control Rich Edit.

*dwFlags*<br/>
Especifica uno o más marcadores CHOOSEFONT. Se pueden combinar uno o más valores preestablecidos mediante el operador bit a bit OR. Si modifica el miembro de estructura de `m_cf.Flag`, procure usar un operador bit a bit OR en los cambios que realice para que el comportamiento predeterminado siga intacto. Para obtener más información sobre cada una de estas marcas, consulte la descripción de la estructura [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) en el Windows SDK.

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

Llame a esta función para mostrar el cuadro de diálogo fuente común de Windows y permitir que el usuario elija una fuente.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK y IDCANCEL son constantes que indican si el usuario seleccionó el botón Aceptar o cancelar.

### <a name="remarks"></a>Comentarios

Si desea inicializar los distintos controles de cuadro de diálogo de fuente estableciendo los miembros de la estructura [m_cf](#m_cf) , debe hacerlo antes `DoModal`de llamar a, pero después de que se construya el objeto de cuadro de diálogo.

Si `DoModal` devuelve IDOK, puede llamar a otras funciones miembro para recuperar la información de configuración o la entrada del usuario en el cuadro de diálogo.

### <a name="example"></a>Ejemplo

  Vea los ejemplos de [CFontDialog:: CFontDialog](#cfontdialog) y [CFontDialog:: GetColor](#getcolor).

##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat

Recupera el formato de caracteres de la fuente seleccionada.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parámetros

*cf*<br/>
Estructura [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) que contiene información sobre el formato de caracteres de la fuente seleccionada.

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

Llame a esta función para asignar las características de la fuente seleccionada actualmente a los miembros de una estructura [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parámetros

*lplf*<br/>
Puntero a una `LOGFONT` estructura.

### <a name="remarks"></a>Comentarios

Se `CFontDialog` proporcionan otras funciones miembro para tener acceso a características individuales de la fuente actual.

Si se llama a esta función durante una llamada a [DoModal](#domodal), devuelve la selección actual en el momento (lo que el usuario ve o ha cambiado en el cuadro de diálogo). Si se llama a esta función después de una `DoModal` llamada a ( `DoModal` solo si devuelve IDOK), devuelve lo que el usuario seleccionó realmente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>  CFontDialog::GetFaceName

Llame a esta función para recuperar el nombre de la fuente seleccionada.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre de la fuente seleccionada en el `CFontDialog` cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>  CFontDialog::GetSize

Llame a esta función para recuperar el tamaño de la fuente seleccionada.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño de la fuente, en décimas de punto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>  CFontDialog::GetStyleName

Llame a esta función para recuperar el nombre de estilo de la fuente seleccionada.

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

Peso de la fuente seleccionada.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre el peso de una fuente, vea [Cfont (:: CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>  CFontDialog::IsBold

Llame a esta función para determinar si la fuente seleccionada está en negrita.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene habilitada la característica negrita; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>  CFontDialog::IsItalic

Llame a esta función para determinar si la fuente seleccionada está en cursiva.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene habilitada la característica cursiva; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut

Llame a esta función para determinar si la fuente seleccionada se muestra con tachado.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene habilitada la característica de tachado; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>  CFontDialog::IsUnderline

Llame a esta función para determinar si la fuente seleccionada está subrayada.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la fuente seleccionada tiene habilitada la característica de subrayado; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

Estructura cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Comentarios

Después de construir un `CFontDialog` objeto, puede utilizar `m_cf` para modificar diversos aspectos del cuadro de diálogo antes de llamar a `DoModal` la función miembro. Para obtener más información sobre esta estructura, vea [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
