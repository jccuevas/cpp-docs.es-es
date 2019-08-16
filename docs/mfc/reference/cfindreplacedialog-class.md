---
title: Clase CFindReplaceDialog
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 71234adec214bcbf5d42090edb582a7e5dd552b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506525"
---
# <a name="cfindreplacedialog-class"></a>Clase CFindReplaceDialog

Permite implementar los cuadros de diálogo Buscar/reemplazar de cadena estándar en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Llame a esta función para construir `CFindReplaceDialog` un objeto.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|Crea y muestra un `CFindReplaceDialog` cuadro de diálogo.|
|[CFindReplaceDialog::FindNext](#findnext)|Llame a esta función para determinar si el usuario desea buscar la siguiente aparición de la cadena de búsqueda.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Llame a esta función para recuperar la cadena de búsqueda actual.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Llame a esta función para recuperar `FINDREPLACE` la estructura en el controlador de mensajes registrado.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Llame a esta función para recuperar la cadena de reemplazo actual.|
|[CFindReplaceDialog::IsTerminating](#isterminating)|Llame a esta función para determinar si el cuadro de diálogo está finalizando.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Llame a esta función para determinar si el usuario desea coincidir exactamente con las mayúsculas y minúsculas de la cadena de búsqueda.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Llame a esta función para determinar si el usuario desea coincidir solo con palabras completas.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Llame a esta función para determinar si el usuario desea reemplazar todas las apariciones de la cadena.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Llame a esta función para determinar si el usuario desea reemplazar la palabra actual.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Llame a esta función para determinar si el usuario desea que la búsqueda continúe en sentido descendente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Estructura utilizada para personalizar un `CFindReplaceDialog` objeto.|

## <a name="remarks"></a>Comentarios

A diferencia de los demás cuadros de diálogo comunes `CFindReplaceDialog` de Windows, los objetos no son modales, lo que permite a los usuarios interactuar con otras ventanas mientras están en la pantalla. Hay dos tipos de `CFindReplaceDialog` objetos: Buscar cuadros de diálogo y buscar/reemplazar cuadros de diálogo. Aunque los cuadros de diálogo permiten al usuario escribir las cadenas de búsqueda y de búsqueda y reemplazo, no realizan ninguna de las funciones de búsqueda o reemplazo. Debe agregarlos a la aplicación.

Para construir un `CFindReplaceDialog` objeto, use el constructor proporcionado (que no tiene ningún argumento). Puesto que se trata de un cuadro de diálogo no modal, asigne el objeto en el montón mediante el operador **New** , en lugar de en la pila.

Una vez `CFindReplaceDialog` construido un objeto, debe llamar a la función miembro [Create](#create) para crear y mostrar el cuadro de diálogo.

Use la estructura [m_fr](#m_fr) para inicializar el cuadro de diálogo `Create`antes de llamar a. La `m_fr` estructura es de tipo [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Para obtener más información sobre esta estructura, vea el Windows SDK.

Para que se notifique a la ventana primaria de las solicitudes de búsqueda y reemplazo, debe usar la función [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) de Windows y usar la macro de mapa de mensajes [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) en la ventana de marco que controla este mensaje registrado.

Puede determinar si el usuario ha decidido terminar el cuadro de diálogo con la `IsTerminating` función miembro.

`CFindReplaceDialog`se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3,1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase `CFindReplaceDialog`de, proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base.

No es necesaria la personalización de la función de enlace.

Para obtener más información sobre `CFindReplaceDialog`el uso de, vea [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs. h

##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog

Construye un objeto `CFindReplaceDialog`.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Comentarios

Dado que `CFindReplaceDialog` el objeto es un cuadro de diálogo no modal, debe construirlo en el montón mediante el operador **New** .

Durante la destrucción, el marco de trabajo intenta realizar una **eliminación** en el puntero al cuadro de diálogo. Si ha creado el cuadro de diálogo en la pila, el puntero This no existe y **se** puede producir un comportamiento indefinido.

Para obtener más información sobre la construcción `CFindReplaceDialog` de objetos, vea la introducción a [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) . Utilice la función miembro [CFindReplaceDialog:: Create](#create) para mostrar el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

Crea y muestra un objeto de cuadro de diálogo Buscar o buscar/reemplazar, dependiendo del valor de `bFindDialogOnly`.

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*bFindDialogOnly*<br/>
Establezca este parámetro en TRUE para mostrar un cuadro de diálogo de **búsqueda** . Establézcalo en FALSE para mostrar un cuadro de diálogo **Buscar y reemplazar** .

*lpszFindWhat*<br/>
Puntero a la cadena de búsqueda predeterminada cuando aparece el cuadro de diálogo. Si es NULL, el cuadro de diálogo no contiene una cadena de búsqueda predeterminada.

*lpszReplaceWith*<br/>
Puntero a la cadena de reemplazo predeterminada cuando aparece el cuadro de diálogo. Si es NULL, el cuadro de diálogo no contiene una cadena de reemplazo predeterminada.

*dwFlags*<br/>
Una o varias marcas que puede usar para personalizar la configuración del cuadro de diálogo, combinada mediante el operador bit a bit or. El valor predeterminado es FR_DOWN, que especifica que la búsqueda debe continuar en sentido descendente. Vea la estructura [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) en el Windows SDK para obtener más información acerca de estas marcas.

*pParentWnd*<br/>
Puntero a la ventana primaria o propietaria del cuadro de diálogo. Esta es la ventana que recibirá el mensaje especial que indica que se ha solicitado una acción de búsqueda y reemplazo. Si es NULL, se utiliza la ventana principal de la aplicación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de cuadro de diálogo se ha creado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Para que se notifique a la ventana primaria de las solicitudes de búsqueda y reemplazo, debe usar la función [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) de Windows cuyo valor devuelto sea un número de mensaje único para la instancia de la aplicación. La ventana de marco debe tener una entrada de mapa de mensajes que declare la `OnFindReplace` función de devolución de llamada (en el ejemplo siguiente) que controla este mensaje registrado. El siguiente fragmento de código es un ejemplo de cómo hacer esto para una clase de ventana de `CMyRichEditView`marco denominada:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

Dentro de `OnFindReplace` la función, se interpretan las intenciones del usuario mediante los métodos [CFindReplaceDialog:: FindNext](#findnext) y [CFindReplaceDialog:: IsTerminating](#isterminating) y se crea el código para las operaciones de búsqueda y reemplazo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog).

##  <a name="findnext"></a>  CFindReplaceDialog::FindNext

Llame a esta función desde la función de devolución de llamada para determinar si el usuario desea buscar la siguiente aparición de la cadena de búsqueda.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea buscar la siguiente aparición de la cadena de búsqueda; de lo contrario, es 0.

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

Llame a esta función desde la función de devolución de llamada para recuperar la cadena predeterminada que se va a buscar.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena predeterminada que se va a buscar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier

Llame a esta función para recuperar un puntero al cuadro de diálogo Buscar reemplazar actual.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*lParam*<br/>
Valor *lParam* que se pasa a la función miembro `OnFindReplace` de la ventana de marco.

### <a name="return-value"></a>Valor devuelto

Puntero al cuadro de diálogo actual.

### <a name="remarks"></a>Comentarios

Debe usarse dentro de la función de devolución de llamada para tener acceso al cuadro de diálogo actual, llamar a sus `m_fr` funciones miembro y obtener acceso a la estructura.

### <a name="example"></a>Ejemplo

Vea [CFindReplaceDialog:: Create](#create) para obtener un ejemplo de cómo registrar el controlador OnFindReplace para recibir notificaciones desde el cuadro de diálogo Buscar reemplazar.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

Llame a esta función para recuperar la cadena de reemplazo actual.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena predeterminada con la que se van a reemplazar las cadenas encontradas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog:: GetFindString](#getfindstring).

##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating

Llame a esta función dentro de la función de devolución de llamada para determinar si el usuario ha decidido finalizar el cuadro de diálogo.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha decidido finalizar el cuadro de diálogo; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si esta función devuelve un valor distinto de cero, debe `DestroyWindow` llamar a la función miembro del cuadro de diálogo actual y establecer en NULL cualquier variable de puntero de cuadro de diálogo. Opcionalmente, también puede almacenar el texto de buscar y reemplazar que se escribió por última vez y usarlo para inicializar el siguiente cuadro de diálogo Buscar y reemplazar.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog:: GetFindString](#getfindstring).

##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr

Se usa para personalizar `CFindReplaceDialog` un objeto.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Comentarios

`m_fr`es una estructura de tipo [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Sus miembros almacenan las características del objeto de cuadro de diálogo. Después de construir un `CFindReplaceDialog` objeto, puede utilizar `m_fr` para modificar diversos valores en el cuadro de diálogo.

Para obtener más información sobre esta estructura, vea `FINDREPLACE` la estructura en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog).

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

Llame a esta función para determinar si el usuario desea coincidir exactamente con las mayúsculas y minúsculas de la cadena de búsqueda.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea buscar apariciones de la cadena de búsqueda que coincidan exactamente con las mayúsculas y minúsculas de la cadena de búsqueda; de lo contrario, es 0.

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

Llame a esta función para determinar si el usuario desea coincidir solo con palabras completas.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea hacer coincidir solo las palabras completas de la cadena de búsqueda; de lo contrario, es 0.

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

Llame a esta función para determinar si el usuario desea reemplazar todas las apariciones de la cadena.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha solicitado que se reemplacen todas las cadenas que coincidan con la cadena de reemplazo; de lo contrario, es 0.

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

Llame a esta función para determinar si el usuario desea reemplazar la palabra actual.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha solicitado que la cadena seleccionada se reemplace con la cadena de reemplazo; de lo contrario, es 0.

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

Llame a esta función para determinar si el usuario desea que la búsqueda continúe en sentido descendente.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea que la búsqueda continúe en sentido descendente; 0 si el usuario desea que la búsqueda continúe en una dirección ascendente.

## <a name="see-also"></a>Vea también

[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
