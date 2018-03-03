---
title: Clase CMFCMaskedEdit | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0ada987b3226d901c3bf01236c2a593c2e36f51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcmaskededit-class"></a>Clase CMFCMaskedEdit
La `CMFCMaskedEdit` clase es compatible con un control de edición con máscara, que valida la entrada de usuario en una máscara y muestra los resultados validados de acuerdo con una plantilla.  
  
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
|[CMFCMaskedEdit::DisableMask](#disablemask)|Deshabilita la validación de entrada de usuario.|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Especifica si el `GetWindowText` método recupera solo caracteres enmascarados.|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|Inicializa la máscara de control de edición.|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Especifica si el control de edición con máscara selecciona grupos concretos de intervención del usuario, o todos los datos de usuario de entrada.|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Especifica si el texto se valida comparándola con solo enmascara caracteres, o con la máscara de toda.|  
|`CMFCMaskedEdit::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Recupera valida texto desde el control de edición con máscara.|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Especifica una cadena de caracteres válidos que el usuario puede escribir.|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Muestra un símbolo del sistema en el control de edición con máscara.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Lo llama el marco para validar el carácter especificado en el carácter correspondiente de la máscara.|  
  
## <a name="remarks"></a>Comentarios  
 Realice los pasos siguientes para usar el `CMFCMaskedEdit` control en la aplicación:  
  
 1. Incrustar un `CMFCMaskedEdit` objeto a la clase de ventana.  
  
 2. Llame a la [CMFCMaskedEdit::EnableMask](#enablemask) método para especificar la máscara.  
  
 3. Llame a la [CMFCMaskedEdit::SetValidChars](#setvalidchars) método para especificar la lista de caracteres válidos.  
  
 4. Llame a la [CMFCMaskedEdit::SetWindowText](#setwindowtext) método para especificar el texto predeterminado para el control de edición de la máscara.  
  
 5. Llame a la [CMFCMaskedEdit::GetWindowText](#getwindowtext) método para recuperar el texto validado.  
  
 Si no se llama a uno o varios métodos para inicializar la máscara, caracteres válidos y texto predeterminado, el control de edición con máscara se comporta tal y como se comporta el control de edición estándar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar una máscara (por ejemplo, un número de teléfono) mediante el uso de la `EnableMask` método para crear la máscara para editar la máscara (control), el `SetValidChars` método para especificar una cadena de caracteres válidos que el usuario puede escribir y `SetWindowText` control de edición de método para mostrar un símbolo del sistema en la máscara. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
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
  
##  <a name="disablemask"></a>CMFCMaskedEdit::DisableMask  
 Deshabilita la validación de entrada de usuario.  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se deshabilita la validación de entrada de usuario, el control de edición con máscara se comporta como el estándar de control de edición.  
  
##  <a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 Especifica si el `GetWindowText` método recupera solo caracteres enmascarados.  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`para especificar que la [CMFCMaskedEdit::GetWindowText](#getwindowtext) método recuperar solo enmascara caracteres; `FALSE` para especificar que el método recuperar todo el texto. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para habilitar la recuperación de caracteres enmascarados. A continuación, cree un control de edición con máscara que corresponde al número de teléfono, como (425) 555-0187. Si se llama a la `GetWindowText` método, devuelve "4255550187". Si deshabilita recuperar caracteres enmascarados, la `GetWindowText` método devuelve el texto que se muestra en el control de edición, por ejemplo "(425) 555-0187".  
  
##  <a name="enablemask"></a>CMFCMaskedEdit::EnableMask  
 Inicializa la máscara de control de edición.  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszMask`  
 Una cadena de máscara que especifica el tipo de caracteres que pueden aparecer en cada posición en la entrada del usuario. La longitud de la `lpszInputTemplate` y `lpszMask` cadenas de parámetros deben ser el mismo. Vea la sección Comentarios para obtener información más detallada sobre los caracteres de máscara.  
  
 [in] `lpszInputTemplate`  
 Una cadena de plantilla de máscara que especifica que el literal de caracteres que puede aparecer en cada posición en la entrada del usuario. Utilice el carácter de subrayado ('_') como un marcador de posición de carácter. La longitud de la `lpszInputTemplate` y `lpszMask` cadenas de parámetros deben ser el mismo.  
  
 [in] `chMaskInputTemplate`  
 Un carácter predeterminado que se sustituye por el marco de trabajo para cada carácter no válido en la entrada del usuario. El valor predeterminado de este parámetro es el carácter de subrayado ('_').  
  
 [in] `lpszValid`  
 Una cadena que contiene un conjunto de caracteres válidos. `NULL`indica que todos los caracteres son válidos. El valor predeterminado de este parámetro es `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para crear la máscara para el control de edición con máscara. Derivar una clase de la `CMFCMaskedEdit` clase e invalidar el [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) método se debe utilizar su propio código para el procesamiento de máscara personalizada.  
  
 En la tabla siguiente muestra los caracteres de máscara de forma predeterminada:  
  
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
  
##  <a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup  
 Especifica si el control de edición con máscara permite al usuario seleccionar grupos determinada entrada, o todas las entradas.  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para seleccionar únicamente grupos; `FALSE` para seleccionar el texto completo. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para especificar si el control de edición con máscara permite al usuario seleccionar por grupo o el texto completo.  
  
 De forma predeterminada, se habilita la selección por grupo. En este caso, el usuario puede seleccionar solo continuados grupos de caracteres válidos.  
  
 Por ejemplo, puede usar el control de edición con máscara siguientes para validar un número de teléfono:  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 Si se habilita la selección por grupo, el usuario puede recuperar solo el "425", "555" o "0187" grupos de cadena. Si se deshabilita la selección de grupos del usuario puede recuperar todo el texto del número de teléfono: "(425) 555-0187".  
  
##  <a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 Especifica si el texto se valida frente a solo los caracteres enmascarados o con respecto a la máscara de toda.  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`para validar al usuario la entrada contra enmascarada solo caracteres; `FALSE` para validar con la máscara de toda. El valor predeterminado es `TRUE`.  
  
##  <a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText  
 Recupera valida texto desde el control de edición con máscara.  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lpszStringBuf`  
 Un puntero a un búfer que recibe el texto desde el control de edición.  
  
 [in] `nMaxCount`  
 El número máximo de caracteres que se va a recibir.  
  
 [out] `rstrString`  
 Una referencia al objeto de cadena que recibe el texto desde el control de edición.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera sobrecarga de método devuelve el número de bytes de la cadena que se copia en el `lpszStringBuf` búfer de parámetro; 0 si el control de edición con máscara no tiene ningún texto.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia el texto del control de edición con máscara a la `lpszStringBuf` búfer o `rstrString` cadena.  
  
 Este método vuelve a definir [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).  
  
##  <a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar  
 Lo llama el marco para validar el carácter especificado en el carácter correspondiente de la máscara.  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `chChar`  
 El carácter que se va a validar.  
  
 [in] `chMaskChar`  
 El carácter correspondiente de la cadena de máscara.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `chChar` parámetro es el tipo de caracteres permitido por el `chMaskChar` parámetro; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para validar los caracteres de entrada por su cuenta. Para obtener más información acerca de los caracteres de máscara, consulte la [CMFCMaskedEdit::EnableMask](#enablemask) método.  
  
##  <a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars  
 Especifica una cadena de caracteres válidos que el usuario puede escribir.  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszValid`  
 Una cadena que contiene el conjunto de caracteres de entrada válidos. `NULL`significa que todos los caracteres son válidos. El valor predeterminado de este parámetro es `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para definir una lista de caracteres válidos. Si un carácter de entrada no está en esta lista, control de edición con máscara no lo aceptará.  
  
 En el ejemplo de código siguiente se acepta solo los números hexadecimales.  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText  
 Muestra un símbolo del sistema en el control de edición con máscara.  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszString`  
 Apunta a una cadena terminada en null que se usará como un símbolo del sistema.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece el texto del control.  
  
 Este método vuelve a definir [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CEdit (clase)](../../mfc/reference/cedit-class.md)
