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
ms.openlocfilehash: 7a12d0520d070d74afd9fa91e828970d14c82700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373850"
---
# <a name="cfindreplacedialog-class"></a>Clase CFindReplaceDialog

Le permite implementar cuadros de diálogo de cadena estándar Buscar/Reemplazar en la aplicación.

## <a name="syntax"></a>Sintaxis

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Llame a esta `CFindReplaceDialog` función para construir un objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|Crea y `CFindReplaceDialog` muestra un cuadro de diálogo.|
|[CFindReplaceDialog::FindNext](#findnext)|Llame a esta función para determinar si el usuario desea encontrar la siguiente aparición de la cadena find.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Llame a esta función para recuperar la cadena de búsqueda actual.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Llame a esta `FINDREPLACE` función para recuperar la estructura en el controlador de mensajes registrado.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Llame a esta función para recuperar la cadena de reemplazo actual.|
|[CFindReplaceDialog::Isterminating](#isterminating)|Llame a esta función para determinar si el cuadro de diálogo está terminando.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Llame a esta función para determinar si el usuario desea hacer coincidir el caso de la cadena find exactamente.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Llame a esta función para determinar si el usuario desea hacer coincidir solo palabras completas.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Llame a esta función para determinar si el usuario desea que se reemplacen todas las apariciones de la cadena.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Llame a esta función para determinar si el usuario desea que se reemplace la palabra actual.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Llame a esta función para determinar si el usuario desea que la búsqueda continúe en una dirección descendente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Estructura utilizada para `CFindReplaceDialog` personalizar un objeto.|

## <a name="remarks"></a>Observaciones

A diferencia de los `CFindReplaceDialog` otros cuadros de diálogo comunes de Windows, los objetos son no codificador, lo que permite a los usuarios interactuar con otras ventanas mientras están en pantalla. Hay dos tipos `CFindReplaceDialog` de objetos: Buscar cuadros de diálogo y Buscar/Reemplazar cuadros de diálogo. Aunque los cuadros de diálogo permiten al usuario introducir cadenas de búsqueda y búsqueda/reemplazo, no realizan ninguna de las funciones de búsqueda o sustitución. Debe agregarlos a la aplicación.

Para construir `CFindReplaceDialog` un objeto, utilice el constructor proporcionado (que no tiene argumentos). Puesto que se trata de un cuadro de diálogo no basado en la directiva, asigne el objeto en el montón mediante el operador **new,** en lugar de en la pila.

Una `CFindReplaceDialog` vez que se ha construido un objeto, debe llamar a la [crear](#create) función miembro para crear y mostrar el cuadro de diálogo.

Utilice la estructura [m_fr](#m_fr) para inicializar `Create`el cuadro de diálogo antes de llamar a . La `m_fr` estructura es de tipo [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Para obtener más información sobre esta estructura, consulte el Windows SDK.

Para que la ventana primaria reciba una notificación de las solicitudes find/replace, debe usar la función [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) de Windows y usar la macro de mapa de mensajes [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) en la ventana de marco que controla este mensaje registrado.

Puede determinar si el usuario ha decidido terminar `IsTerminating` el cuadro de diálogo con la función miembro.

`CFindReplaceDialog`depende del COMMDLG. DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de `CFindReplaceDialog`diálogo, derive una clase de , proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes sin procesar deben pasarse a la clase base.

No es necesario personalizar la función de gancho.

Para obtener más `CFindReplaceDialog`información sobre el uso de , vea [Clases](../../mfc/common-dialog-classes.md)de cuadro de diálogo comunes .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="cfindreplacedialogcfindreplacedialog"></a><a name="cfindreplacedialog"></a>CFindReplaceDialog::CFindReplaceDialog

Construye un objeto `CFindReplaceDialog`.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Observaciones

Dado `CFindReplaceDialog` que el objeto es un cuadro de diálogo no basado en la no diferencia, debe construirlo en el montón mediante el operador **new.**

Durante la destrucción, el marco de trabajo intenta realizar una **eliminación en** el puntero al cuadro de diálogo. Si ha creado el cuadro de diálogo en la pila, el puntero **this** no existe y puede producirse un comportamiento indefinido.

Para obtener más información `CFindReplaceDialog` sobre la construcción de objetos, vea el [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) información general. Utilice la [CFindReplaceDialog::Create](#create) función miembro para mostrar el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

## <a name="cfindreplacedialogcreate"></a><a name="create"></a>CFindReplaceDialog::Create

Crea y muestra un objeto de cuadro de diálogo Buscar `bFindDialogOnly`o Buscar/Reemplazar, en función del valor de .

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
Establezca este parámetro en TRUE para mostrar un cuadro de diálogo **Buscar.** Establézcalo en FALSE para mostrar un cuadro de diálogo **Buscar/Reemplazar.**

*lpszFindWhat*<br/>
Puntero a la cadena de búsqueda predeterminada cuando aparece el cuadro de diálogo. Si NULL, el cuadro de diálogo no contiene una cadena de búsqueda predeterminada.

*lpszReplaceWith*<br/>
Puntero a la cadena de reemplazo predeterminada cuando aparece el cuadro de diálogo. Si NULL, el cuadro de diálogo no contiene una cadena de reemplazo predeterminada.

*dwFlags*<br/>
Una o más marcas se pueden utilizar para personalizar la configuración del cuadro de diálogo, combinado mediante el operador OR bit a bit. El valor predeterminado es FR_DOWN, que especifica que la búsqueda debe continuar en una dirección descendente. Consulte la estructura [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew) en el Windows SDK para obtener más información sobre estas marcas.

*pParentWnd*<br/>
Puntero a la ventana principal o propietaria del cuadro de diálogo. Esta es la ventana que recibirá el mensaje especial que indica que se solicita una acción de búsqueda/reemplazo. Si NULL, se utiliza la ventana principal de la aplicación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de cuadro de diálogo se creó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para que la ventana primaria reciba una notificación de las solicitudes find/replace, debe usar la función [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) de Windows cuyo valor devuelto sea un número de mensaje único para la instancia de la aplicación. La ventana de marco debe tener una entrada `OnFindReplace` de mapa de mensajes que declare la función de devolución de llamada (en el ejemplo siguiente) que controla este mensaje registrado. El siguiente fragmento de código es un ejemplo de `CMyRichEditView`cómo hacerlo para una clase de ventana de marco denominada:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

Dentro `OnFindReplace` de la función, interprete las intenciones del usuario mediante el [CFindReplaceDialog::FindNext](#findnext) y [CFindReplaceDialog::IsTerminating](#isterminating) métodos y cree el código para las operaciones de búsqueda/reemplazo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogfindnext"></a><a name="findnext"></a>CFindReplaceDialog::FindNext

Llame a esta función desde la función de devolución de llamada para determinar si el usuario desea encontrar la siguiente aparición de la cadena de búsqueda.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea encontrar la siguiente aparición de la cadena de búsqueda; de lo contrario 0.

## <a name="cfindreplacedialoggetfindstring"></a><a name="getfindstring"></a>CFindReplaceDialog::GetFindString

Llame a esta función desde la función de devolución de llamada para recuperar la cadena predeterminada que se va a buscar.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Valor devuelto

La cadena predeterminada que se va a buscar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetnotifier"></a><a name="getnotifier"></a>CFindReplaceDialog::GetNotifier

Llame a esta función para recuperar un puntero al cuadro de diálogo Buscar reemplazar actual.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*lParam*<br/>
El valor *lparam* pasado a `OnFindReplace` la función miembro de la ventana de marco.

### <a name="return-value"></a>Valor devuelto

Un puntero al cuadro de diálogo actual.

### <a name="remarks"></a>Observaciones

Debe usarse dentro de la función de devolución de llamada para `m_fr` tener acceso al cuadro de diálogo actual, llamar a sus funciones miembro y tener acceso a la estructura.

### <a name="example"></a>Ejemplo

Vea [CFindReplaceDialog::Create](#create) para obtener un ejemplo de cómo registrar el OnFindReplace controlador para recibir notificaciones desde el Buscar reemplazar cuadro de diálogo.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

## <a name="cfindreplacedialoggetreplacestring"></a><a name="getreplacestring"></a>CFindReplaceDialog::GetReplaceString

Llame a esta función para recuperar la cadena de reemplazo actual.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Valor devuelto

Cadena predeterminada con la que reemplazar las cadenas encontradas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogisterminating"></a><a name="isterminating"></a>CFindReplaceDialog::Isterminating

Llame a esta función dentro de la función de devolución de llamada para determinar si el usuario ha decidido terminar el cuadro de diálogo.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha decidido terminar el cuadro de diálogo; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si esta función devuelve distinto `DestroyWindow` de cero, debe llamar a la función miembro del cuadro de diálogo actual y establecer cualquier variable de puntero de cuadro de diálogo en NULL. Opcionalmente, también puede almacenar el texto de búsqueda/sustitución introducido por última vez y utilizarlo para inicializar el siguiente cuadro de diálogo de búsqueda/reemplazar.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::GetFindString](#getfindstring).

## <a name="cfindreplacedialogm_fr"></a><a name="m_fr"></a>CFindReplaceDialog::m_fr

Se utiliza `CFindReplaceDialog` para personalizar un objeto.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Observaciones

`m_fr`es una estructura de tipo [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew). Sus miembros almacenan las características del objeto de cuadro de diálogo. Después de `CFindReplaceDialog` construir un `m_fr` objeto, puede utilizar para modificar varios valores en el cuadro de diálogo.

Para obtener más información sobre `FINDREPLACE` esta estructura, vea la estructura en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

## <a name="cfindreplacedialogmatchcase"></a><a name="matchcase"></a>CFindReplaceDialog::MatchCase

Llame a esta función para determinar si el usuario desea hacer coincidir el caso de la cadena find exactamente.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea encontrar las apariciones de la cadena de búsqueda que coinciden exactamente con el caso de la cadena de búsqueda; de lo contrario 0.

## <a name="cfindreplacedialogmatchwholeword"></a><a name="matchwholeword"></a>CFindReplaceDialog::MatchWholeWord

Llame a esta función para determinar si el usuario desea hacer coincidir solo palabras completas.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea hacer coincidir solo las palabras completas de la cadena de búsqueda; de lo contrario 0.

## <a name="cfindreplacedialogreplaceall"></a><a name="replaceall"></a>CFindReplaceDialog::ReplaceAll

Llame a esta función para determinar si el usuario desea que se reemplacen todas las apariciones de la cadena.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha solicitado que se reemplacen todas las cadenas que coinciden con la cadena replace; de lo contrario 0.

## <a name="cfindreplacedialogreplacecurrent"></a><a name="replacecurrent"></a>CFindReplaceDialog::ReplaceCurrent

Llame a esta función para determinar si el usuario desea que se reemplace la palabra actual.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha solicitado que la cadena seleccionada actualmente se reemplace por la cadena replace; de lo contrario 0.

## <a name="cfindreplacedialogsearchdown"></a><a name="searchdown"></a>CFindReplaceDialog::SearchDown

Llame a esta función para determinar si el usuario desea que la búsqueda continúe en una dirección descendente.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea que la búsqueda continúe en una dirección descendente; 0 si el usuario desea que la búsqueda continúe en dirección ascendente.

## <a name="see-also"></a>Consulte también

[Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
