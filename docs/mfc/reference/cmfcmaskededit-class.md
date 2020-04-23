---
title: CMFCMaskedEdit (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
ms.openlocfilehash: 26617f10605fe2a8a94adcc477cccab7e2ba4919
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754223"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit (clase)

La `CMFCMaskedEdit` clase admite un control de edición enmascarado, que valida la entrada del usuario con una máscara y muestra los resultados validados según una plantilla.

## <a name="syntax"></a>Sintaxis

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|Constructor predeterminado.|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCMaskedEdit::DisableMask](#disablemask)|Deshabilita la validación de la entrada del usuario.|
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Especifica si `GetWindowText` el método recupera solo caracteres enmascarados.|
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicializa el control de edición enmascarado.|
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Especifica si el control de edición enmascarado selecciona determinados grupos de entrada de usuario o todas las entradas del usuario.|
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Especifica si el texto se valida solo con caracteres enmascarados o con toda la máscara.|
|`CMFCMaskedEdit::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Recupera texto validado del control de edición enmascarado.|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Especifica una cadena de caracteres válidos que el usuario puede escribir.|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Muestra una solicitud en el control de edición enmascarado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Llamado por el marco de trabajo para validar el carácter especificado con el carácter de máscara correspondiente.|

## <a name="remarks"></a>Observaciones

Realice los pasos `CMFCMaskedEdit` siguientes para utilizar el control en la aplicación:

1. Incruste un `CMFCMaskedEdit` objeto en la clase de ventana.

2. Llame al método [CMFCMaskedEdit::EnableMask](#enablemask) para especificar la máscara.

3. Llame al método [CMFCMaskedEdit::SetValidChars](#setvalidchars) para especificar la lista de caracteres válidos.

4. Llame a la [CMFCMaskedEdit::SetWindowText](#setwindowtext) método para especificar el texto predeterminado para el control de edición enmascarado.

5. Llame al método [CMFCMaskedEdit::GetWindowText](#getwindowtext) para recuperar el texto validado.

Si no llama a uno o más métodos para inicializar la máscara, los caracteres válidos y el texto predeterminado, el control de edición enmascarado se comporta igual que el control de edición estándar se comporta.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar una máscara (por ejemplo, un número de teléfono) mediante el `EnableMask` método para crear la máscara para el control de edición enmascarado, el `SetValidChars` método para especificar una cadena de caracteres válidos que el usuario puede escribir y `SetWindowText` el método para mostrar un mensaje en el control de edición enmascarado. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmaskededit.h

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a>CMFCMaskedEdit::DisableMask

Deshabilita la validación de la entrada del usuario.

```cpp
void DisableMask();
```

### <a name="remarks"></a>Observaciones

Si la validación de entrada de usuario está deshabilitada, el control de edición enmascarado se comporta como el control de edición estándar.

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly

Especifica si `GetWindowText` el método recupera solo caracteres enmascarados.

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para especificar que el [CMFCMaskedEdit::GetWindowText](#getwindowtext) método recuperar sólo caracteres enmascarados; FALSE para especificar que el método recuperar todo el texto. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

Utilice este método para habilitar la recuperación de caracteres enmascarados. A continuación, cree un control de edición enmascarado que corresponda al número de teléfono, como (425) 555-0187. Si llama `GetWindowText` al método, devuelve "4255550187". Si deshabilita la recuperación de `GetWindowText` caracteres enmascarados, el método devuelve el texto que se muestra en el control de edición, por ejemplo "(425) 555-0187".

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a>CMFCMaskedEdit::EnableMask

Inicializa el control de edición enmascarado.

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszMask*<br/>
[en] Cadena de máscara que especifica el tipo de carácter que puede aparecer en cada posición de la entrada del usuario. La longitud de las cadenas de parámetro *lpszInputTemplate* y *lpszMask* debe ser la misma. Consulte la sección Comentarios para obtener más detalles sobre los caracteres de máscara.

*lpszInputTemplate*<br/>
[en] Cadena de plantilla de máscara que especifica los caracteres literales que pueden aparecer en cada posición de la entrada del usuario. Utilice el carácter de subrayado ('_') como marcador de posición de caracteres. La longitud de las cadenas de parámetro *lpszInputTemplate* y *lpszMask* debe ser la misma.

*chMaskInputTemplate*<br/>
[en] Carácter predeterminado que el marco de trabajo sustituye para cada carácter no válido en la entrada del usuario. El valor predeterminado de este parámetro es el carácter de subrayado ('_').

*lpszValid*<br/>
[en] Cadena que contiene un conjunto de caracteres válidos. NULL indica que todos los caracteres son válidos. El valor predeterminado de este parámetro es NULL.

### <a name="remarks"></a>Observaciones

Utilice este método para crear la máscara para el control de edición enmascarado. Derive una clase `CMFCMaskedEdit` de la clase e invalide el método [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) para usar su propio código para el procesamiento de máscaras personalizadas.

En la tabla siguiente se enumeran los caracteres de máscara predeterminados:

|Personaje de máscara|Definición|
|--------------------|----------------|
|D|Dígitos.|
|d|Dígito o espacio.|
|+|Más ('+'), menos ('-') o espacio.|
|C|Carácter alfabético.|
|c|Carácter o espacio alfabético.|
|Un|Carácter alfanumérico.|
|a|Carácter alfanumérico o espacio.|
|*|Un carácter imprimible.|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup

Especifica si el control de edición enmascarado permite al usuario seleccionar una entrada de grupos concretos o todas las entradas.

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para seleccionar solo grupos; FALSE para seleccionar todo el texto. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

Utilice esta función para especificar si el control de edición enmascarado permite a un usuario seleccionar por grupo o todo el texto.

De forma predeterminada, la selección por grupo está habilitada. En este caso, el usuario solo puede seleccionar grupos continuos de caracteres válidos.

Por ejemplo, puede utilizar el siguiente control de edición enmascarado para validar un número de teléfono:

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Si la selección por grupo está habilitada, el usuario solo puede recuperar los grupos de cadenas "425", "555" o "0187". Si la selección de grupo está deshabilitada, el usuario puede recuperar el texto completo del número de teléfono: "(425) 555-0187".

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly

Especifica si el texto se valida solo con los caracteres enmascarados o con toda la máscara.

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para validar la entrada del usuario con solo caracteres enmascarados; FALSE para validar con toda la máscara. El valor predeterminado es TRUE.

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText

Recupera texto validado del control de edición enmascarado.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Parámetros

*lpszStringBuf*<br/>
[fuera] Puntero a un búfer que recibe el texto del control de edición.

*nMaxCount*<br/>
[en] El número máximo de caracteres que se recibirán.

*rstrString*<br/>
[fuera] Una referencia al objeto de cadena que recibe el texto del control de edición.

### <a name="return-value"></a>Valor devuelto

La primera sobrecarga del método devuelve el número de bytes de la cadena que se copia en el búfer de *parámetrolpszStringBuf;* 0 si el control de edición enmascarado no tiene texto.

### <a name="remarks"></a>Observaciones

Este método copia el texto del control de edición enmascarado en el búfer *lpszStringBuf* o la cadena *rstrString.*

Este método redefine [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar

Llamado por el marco de trabajo para validar el carácter especificado con el carácter de máscara correspondiente.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Parámetros

*chChar*<br/>
[en] El carácter que se va a validar.

*chMaskChar*<br/>
[en] El carácter correspondiente de la cadena de máscara.

### <a name="return-value"></a>Valor devuelto

TRUESi el *parámetro chChar* es el tipo de carácter permitido por el parámetro *chMaskChar;* de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Invalide este método para validar los caracteres de entrada por su cuenta. Para obtener más información acerca de los caracteres de máscara, vea el [CMFCMaskedEdit::EnableMask](#enablemask) método.

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars

Especifica una cadena de caracteres válidos que el usuario puede escribir.

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszValid*<br/>
[en] Cadena que contiene el conjunto de caracteres de entrada válidos. NULL significa que todos los caracteres son válidos. El valor predeterminado de este parámetro es NULL.

### <a name="remarks"></a>Observaciones

Utilice este método para definir una lista de caracteres válidos. Si un carácter de entrada no está en esta lista, el control de edición enmascarado no lo aceptará.

En el ejemplo de código siguiente solo se aceptan números hexadecimales.

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText

Muestra una solicitud en el control de edición enmascarado.

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*lpszString*<br/>
[en] Apunta a una cadena terminada en null que se usará como solicitud.

### <a name="remarks"></a>Observaciones

Este método establece el texto del control.

Este método redefine [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
