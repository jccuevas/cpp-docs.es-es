---
title: CFindReplaceDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7948b755e65b3a64c57f2fd99cf4eefa68cb3cb9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432378"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog (clase)

Permite implementar cuadros de diálogo Buscar y reemplazar cadenas estándar en su aplicación.

## <a name="syntax"></a>Sintaxis

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|Llame a esta función para construir un `CFindReplaceDialog` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|Crea y muestra un `CFindReplaceDialog` cuadro de diálogo.|
|[CFindReplaceDialog::FindNext](#findnext)|Llame a esta función para determinar si el usuario desea buscar la siguiente repetición de la cadena de búsqueda.|
|[CFindReplaceDialog::GetFindString](#getfindstring)|Llame a esta función para recuperar la cadena de búsqueda actual.|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|Llame a esta función para recuperar el `FINDREPLACE` estructura en el controlador de mensajes registrados.|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|Llame a esta función para recuperar la cadena de reemplazo actual.|
|[CFindReplaceDialog::IsTerminating](#isterminating)|Llame a esta función para determinar si el cuadro de diálogo está finalizando.|
|[CFindReplaceDialog::MatchCase](#matchcase)|Llame a esta función para determinar si el usuario desea coincidir exactamente con el caso de la cadena de búsqueda.|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|Llame a esta función para determinar si el usuario desea hacer coincidir sólo palabras completas.|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|Llame a esta función para determinar si el usuario desea que todas las apariciones de la cadena que se debe reemplazar.|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|Llame a esta función para determinar si el usuario desea que la palabra actual que se debe reemplazar.|
|[CFindReplaceDialog::SearchDown](#searchdown)|Llame a esta función para determinar si el usuario desea que la búsqueda para continuar en dirección descendente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|Una estructura utilizada para personalizar un `CFindReplaceDialog` objeto.|

## <a name="remarks"></a>Comentarios

A diferencia de los otros Windows cuadros de diálogo comunes, `CFindReplaceDialog` objetos son no modales, lo que permite a los usuarios interactuar con otras ventanas mientras están en la pantalla. Hay dos tipos de `CFindReplaceDialog` objetos: buscar cuadros de diálogo y los cuadros de diálogo Buscar y reemplazar. Aunque los cuadros de diálogo permiten al usuario que la entrada de búsqueda y buscar y reemplazar cadenas, no realizan alguna de la búsqueda o reemplazo de funciones. Debe agregarlas a la aplicación.

Para construir un `CFindReplaceDialog` de objeto, utilice el constructor proporcionado (que no tiene ningún argumento). Puesto que se trata de un cuadro de diálogo no modal, asignar el objeto en el montón mediante el **nuevo** operador, en lugar de en la pila.

Una vez un `CFindReplaceDialog` se ha construido el objeto, debe llamar a la [crear](#create) función miembro para crear y mostrar el cuadro de diálogo.

Use la [m_fr](#m_fr) estructura para inicializar el cuadro de diálogo antes de llamar a `Create`. El `m_fr` estructura es de tipo [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea). Para obtener más información sobre esta estructura, consulte el SDK de Windows.

En el orden de la ventana primaria recibir una notificación de solicitudes de búsqueda y reemplazo, debe usar el Windows [RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947) funcionar y utilizar el [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message) macros de mapa de mensajes en el marco ventana que controla este mensaje registrado.

Puede determinar si el usuario ha decidido terminar el cuadro de diálogo con el `IsTerminating` función miembro.

`CFindReplaceDialog` se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase de `CFindReplaceDialog`, proporcione una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base.

Personalización de la función de enlace no es necesario.

Para obtener más información sobre el uso de `CFindReplaceDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog

Construye un objeto `CFindReplaceDialog`.

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Comentarios

Dado que el `CFindReplaceDialog` objeto es un cuadro de diálogo no modal, debe crear en el montón mediante el uso de la **nuevo** operador.

Durante la destrucción, el marco de trabajo intenta realizar una **eliminar este** en el puntero en el cuadro de diálogo. Si ha creado el cuadro de diálogo en la pila, el **esto** puntero no existe y puede provocar un comportamiento indefinido.

Para obtener más información sobre la construcción de `CFindReplaceDialog` objetos, vea el [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md) información general. Use la [CFindReplaceDialog::Create](#create) función miembro para mostrar el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

Crea y muestra una búsqueda o buscar y reemplazar diálogo cuadro objeto, dependiendo del valor de `bFindDialogOnly`.

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
Establezca este parámetro en TRUE para mostrar un **buscar** cuadro de diálogo. Establézcalo en FALSE para mostrar un **buscar y reemplazar** cuadro de diálogo.

*lpszFindWhat*<br/>
Puntero a la cadena de búsqueda de forma predeterminada, cuando aparezca el cuadro de diálogo. Si es NULL, el cuadro de diálogo no contiene una cadena de búsqueda predeterminado.

*lpszReplaceWith*<br/>
Puntero a la cadena de reemplazo predeterminado cuando aparece el cuadro de diálogo. Si es NULL, el cuadro de diálogo no contiene una cadena de reemplazo predeterminado.

*dwFlags*<br/>
Uno o más marcadores que puede usar para personalizar la configuración del cuadro de diálogo combinada mediante el operador OR bit a bit. El valor predeterminado es FR_DOWN, que especifica que la búsqueda debe continuar en dirección descendente. Consulte la [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea) estructura en el SDK de Windows para obtener más información sobre estas marcas.

*pParentWnd*<br/>
Un puntero a la ventana de principal o propietaria del cuadro de diálogo. Esta es la ventana que va a recibir el mensaje especial que indica que se solicita una acción de buscar y reemplazar. Si es NULL, se usa la ventana principal de la aplicación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de cuadro de diálogo se creó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

En el orden de la ventana primaria recibir una notificación de solicitudes de búsqueda y reemplazo, debe usar el Windows [RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947) función cuyo valor devuelto es un número de mensaje único para la instancia de la aplicación. La ventana de marco debe tener una entrada de asignación de mensaje que declara la función de devolución de llamada ( `OnFindReplace` en el ejemplo siguiente) que controla este mensaje registrado. El fragmento de código siguiente es un ejemplo de cómo hacer esto para una clase de ventana de marco denominada `CMyRichEditView`:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

Dentro de su `OnFindReplace` función, interpretar las intenciones del usuario mediante el uso de la [CFindReplaceDialog::FindNext](#findnext) y [CFindReplaceDialog::IsTerminating](#isterminating) métodos y crear el código para las operaciones de buscar y reemplazar.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

##  <a name="findnext"></a>  CFindReplaceDialog::FindNext

Llame a esta función desde la función de devolución de llamada para determinar si el usuario desea buscar la siguiente repetición de la cadena de búsqueda.

```
BOOL FindNext() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea buscar la siguiente repetición de la cadena de búsqueda; en caso contrario, es 0.

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

Llame a esta función desde la función de devolución de llamada para recuperar la cadena predeterminada para buscar.

```
CString GetFindString() const;
```

### <a name="return-value"></a>Valor devuelto

La cadena predeterminada para buscar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier

Llame a esta función para recuperar un puntero al cuadro de diálogo Buscar y reemplazar actual.

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*lParam*<br/>
El *lparam* valor pasado a la ventana de marco `OnFindReplace` función miembro.

### <a name="return-value"></a>Valor devuelto

Un puntero en el cuadro de diálogo actual.

### <a name="remarks"></a>Comentarios

Debe usarse dentro de la función de devolución de llamada para obtener acceso al cuadro de diálogo actual, llame a su miembro, funciones y acceso el `m_fr` estructura.

### <a name="example"></a>Ejemplo

Consulte [CFindReplaceDialog::Create](#create) para obtener un ejemplo de cómo registrar el controlador OnFindReplace para recibir notificaciones desde el cuadro de diálogo Buscar y reemplazar.

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

Llame a esta función para recuperar la cadena de reemplazo actual.

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>Valor devuelto

La cadena predeterminada con la que se va a reemplazar las cadenas se encuentra.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::GetFindString](#getfindstring).

##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating

Llame a esta función dentro de la función de devolución de llamada para determinar si el usuario ha decidido terminar el cuadro de diálogo.

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha decidido terminar el cuadro de diálogo; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si esta función devuelve cero, se debe llamar a la `DestroyWindow` función de miembro del cuadro de diálogo actual y establezca cualquier variable de puntero de cuadro de diálogo en NULL. Si lo desea, también puede almacenar el texto de búsqueda y reemplazo que se escribió por última vez y usarlo para inicializar el cuadro de diálogo Buscar y reemplazar siguiente.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::GetFindString](#getfindstring).

##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr

Usar para personalizar un `CFindReplaceDialog` objeto.

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Comentarios

`m_fr` es una estructura de tipo [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea). Sus miembros almacenan las características del objeto de cuadro de diálogo. Después de crear un `CFindReplaceDialog` objeto, puede usar `m_fr` para modificar los valores distintos en el cuadro de diálogo.

Para obtener más información sobre esta estructura, vea el `FINDREPLACE` estructura en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog).

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

Llame a esta función para determinar si el usuario desea coincidir exactamente con el caso de la cadena de búsqueda.

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea buscar apariciones de la cadena de búsqueda que coincidan exactamente con el caso de la cadena de búsqueda; en caso contrario, es 0.

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

Llame a esta función para determinar si el usuario desea hacer coincidir sólo palabras completas.

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea hacer coincidir solo las palabras completas de la cadena de búsqueda; en caso contrario, es 0.

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

Llame a esta función para determinar si el usuario desea que todas las apariciones de la cadena que se debe reemplazar.

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha solicitado que se reemplazan todas las cadenas que coinciden con la cadena de reemplazo; en caso contrario, es 0.

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

Llame a esta función para determinar si el usuario desea que la palabra actual que se debe reemplazar.

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha solicitado que se reemplaza la cadena seleccionada actualmente con la cadena de reemplazo; en caso contrario, es 0.

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

Llame a esta función para determinar si el usuario desea que la búsqueda para continuar en dirección descendente.

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario desea que la búsqueda para continuar en dirección descendente; 0 si el usuario desea que la búsqueda continúe hacia arriba.

## <a name="see-also"></a>Vea también

[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
