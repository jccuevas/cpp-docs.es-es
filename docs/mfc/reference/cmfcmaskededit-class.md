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
ms.openlocfilehash: c1dcf89811fa5225283cb5bec120d3bd2fdfb003
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410153"
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit (clase)

La `CMFCMaskedEdit` clase es compatible con un control de edición enmascarado, que valida la entrada de usuario en una máscara y muestra los resultados validados de acuerdo con una plantilla.

## <a name="syntax"></a>Sintaxis

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|Constructor predeterminado.|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCMaskedEdit::DisableMask](#disablemask)|Deshabilita la validación de entrada del usuario.|
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Especifica si el `GetWindowText` método recupera solo los caracteres enmascarados.|
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicializa la máscara de control de edición.|
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Especifica si el control de edición con máscara selecciona grupos concretos de entrada del usuario, o todos los usuarios de entrada.|
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Especifica si el texto se valida comparándola con solo enmascarar caracteres, o con la máscara completa.|
|`CMFCMaskedEdit::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Recupera texto desde el control de edición enmascarada puede validar.|
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Especifica una cadena de caracteres válidos que el usuario puede escribir.|
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Muestra un símbolo del sistema en el control de edición con máscara.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Lo llama el marco de trabajo para validar el carácter especificado en el carácter de máscara correspondiente.|

## <a name="remarks"></a>Comentarios

Realice los pasos siguientes para usar el `CMFCMaskedEdit` control en la aplicación:

1. Incrustar un `CMFCMaskedEdit` objeto en la clase de ventana.

2. Llame a la [CMFCMaskedEdit::EnableMask](#enablemask) método para especificar la máscara.

3. Llame a la [CMFCMaskedEdit::SetValidChars](#setvalidchars) método para especificar la lista de caracteres válidos.

4. Llame a la [CMFCMaskedEdit::SetWindowText](#setwindowtext) método para especificar el texto predeterminado para el control de edición de la máscara.

5. Llame a la [CMFCMaskedEdit::GetWindowText](#getwindowtext) método para recuperar el texto validado.

Si no se llame a uno o varios métodos para inicializar la máscara, los caracteres válidos y texto de forma predeterminada, el control de edición con máscara se comporta igual que se comporta el control de edición estándar.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar una máscara (por ejemplo, un número de teléfono) mediante el `EnableMask` método para crear la máscara de control de edición el enmascarado el `SetValidChars` método para especificar una cadena de caracteres válidos que el usuario puede escribir y `SetWindowText` método para mostrar un símbolo del sistema en la máscara de control de edición. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../overview/visual-cpp-samples.md).

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

##  <a name="disablemask"></a>  CMFCMaskedEdit::DisableMask

Deshabilita la validación de entrada del usuario.

```
void DisableMask();
```

### <a name="remarks"></a>Comentarios

Si se deshabilita la validación de entrada de usuario, el control de edición con máscara se comporta como el estándar de control de edición.

##  <a name="enablegetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableGetMaskedCharsOnly

Especifica si el `GetWindowText` método recupera solo los caracteres enmascarados.

```
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
[in] TRUE para especificar que el [CMFCMaskedEdit::GetWindowText](#getwindowtext) método retrieve enmascara solo caracteres; FALSE para especificar que el método recuperar todo el texto. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

Utilice este método para habilitar la recuperación caracteres enmascarados. A continuación, cree un control de edición con máscara que se corresponde con el número de teléfono, como (425) 555-0187. Si se llama a la `GetWindowText` método, devuelve "4255550187". Si deshabilita recuperar caracteres enmascarados, el `GetWindowText` método devuelve el texto que se muestra en el control de edición, por ejemplo, "(425) 555-0187".

##  <a name="enablemask"></a>  CMFCMaskedEdit::EnableMask

Inicializa la máscara de control de edición.

```
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszMask*<br/>
[in] Una cadena de máscara que especifica el tipo de caracteres que pueden aparecer en cada posición en la entrada del usuario. La longitud de la *lpszInputTemplate* y *lpszMask* cadenas del parámetro deben ser el mismo. Vea la sección Comentarios para obtener más detalles sobre los caracteres de máscara.

*lpszInputTemplate*<br/>
[in] Una cadena de plantilla de máscara que especifica que el literal de caracteres que puede aparecer en cada posición en la entrada del usuario. Use el carácter de subrayado ('_') como marcador de posición de carácter. La longitud de la *lpszInputTemplate* y *lpszMask* cadenas del parámetro deben ser el mismo.

*chMaskInputTemplate*<br/>
[in] Un carácter predeterminado que se sustituye por el marco de trabajo para cada carácter no válido en la entrada del usuario. El valor predeterminado de este parámetro es un carácter de subrayado ('_').

*lpszValid*<br/>
[in] Cadena que contiene un conjunto de caracteres válidos. NULL indica que todos los caracteres son válidos. El valor predeterminado de este parámetro es NULL.

### <a name="remarks"></a>Comentarios

Utilice este método para crear la máscara para el control de edición con máscara. Derive una clase de la `CMFCMaskedEdit` clase e invalidar la [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) método debe utilizar su propio código para el procesamiento de máscara personalizado.

La tabla siguiente se enumeran los caracteres de máscara de forma predeterminada:

|Carácter de máscara|Definición|
|--------------------|----------------|
|D|Dígito.|
|d|Dígito o espacio.|
|+|Signo más ('+ '), menos ('-'), o espacio.|
|C|Carácter alfabético.|
|c|Carácter alfabético o un espacio.|
|A|Carácter alfanumérico.|
|a|Carácter alfanumérico o un espacio.|
|*|Un carácter imprimible.|

##  <a name="enableselectbygroup"></a>  CMFCMaskedEdit::EnableSelectByGroup

Especifica si el control de edición con máscara permite al usuario que seleccione grupos concretos entrada o todas las entradas.

```
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
[in] TRUE para seleccionar únicamente grupos; FALSE para seleccionar todo el texto. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

Use esta función para especificar si el control de edición con máscara permite al usuario seleccionar por grupo o todo el texto.

De forma predeterminada, se habilita la selección por grupo. En este caso, el usuario puede seleccionar solo los grupos de caracteres válidos continua.

Por ejemplo, puede usar el control de edición enmascarado siguientes para validar un número de teléfono:

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

Si se habilita la selección por grupo, el usuario puede recuperar solo el "425", "555" o "0187" grupos de cadena. Si se deshabilita la selección de grupos del usuario puede recuperar todo el texto del número de teléfono: "(425) 555-0187".

##  <a name="enablesetmaskedcharsonly"></a>  CMFCMaskedEdit::EnableSetMaskedCharsOnly

Especifica si el texto se valida con solo los caracteres enmascarados o de la máscara completa.

```
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
[in] TRUE para validar la entrada con solo enmascarar caracteres; del usuario FALSE para validar la máscara completa. El valor predeterminado es TRUE.

##  <a name="getwindowtext"></a>  CMFCMaskedEdit::GetWindowText

Recupera texto desde el control de edición enmascarada puede validar.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>Parámetros

*lpszStringBuf*<br/>
[out] Un puntero a un búfer que recibe el texto desde el control de edición.

*nMaxCount*<br/>
[in] El número máximo de caracteres que se va a recibir.

*rstrString*<br/>
[out] Una referencia al objeto de cadena que recibe el texto desde el control de edición.

### <a name="return-value"></a>Valor devuelto

La primera sobrecarga del método devuelve el número de bytes de la cadena que se copia en el *lpszStringBuf* búfer de parámetro; 0 si el control de edición con máscara no tiene ningún texto.

### <a name="remarks"></a>Comentarios

Este método copia el texto del control de edición con máscara para el *lpszStringBuf* búfer o la *rstrString* cadena.

Este método vuelve a definir [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).

##  <a name="ismaskedchar"></a>  CMFCMaskedEdit::IsMaskedChar

Lo llama el marco de trabajo para validar el carácter especificado en el carácter de máscara correspondiente.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>Parámetros

*chChar*<br/>
[in] El carácter que se va a validarse.

*chMaskChar*<br/>
[in] El carácter correspondiente de la cadena de máscara.

### <a name="return-value"></a>Valor devuelto

TRUE si el *chChar* parámetro es el tipo de caracteres permitido por el *chMaskChar* parámetro; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Invalide este método para validar los caracteres de entrada por su cuenta. Para obtener más información sobre los caracteres de máscara, consulte el [CMFCMaskedEdit::EnableMask](#enablemask) método.

##  <a name="setvalidchars"></a>  CMFCMaskedEdit::SetValidChars

Especifica una cadena de caracteres válidos que el usuario puede escribir.

```
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszValid*<br/>
[in] Cadena que contiene el conjunto de caracteres de entrada válidos. NULL significa que todos los caracteres son válidos. El valor predeterminado de este parámetro es NULL.

### <a name="remarks"></a>Comentarios

Utilice este método para definir una lista de caracteres válidos. Si un carácter de entrada no está en esta lista, control de edición enmascarado no lo aceptará.

El siguiente ejemplo de código acepta solo los números hexadecimales.

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

##  <a name="setwindowtext"></a>  CMFCMaskedEdit::SetWindowText

Muestra un símbolo del sistema en el control de edición con máscara.

```
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*lpszString*<br/>
[in] Apunta a una cadena terminada en null que se usará como un símbolo del sistema.

### <a name="remarks"></a>Comentarios

Este método establece el texto del control.

Este método vuelve a definir [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)
