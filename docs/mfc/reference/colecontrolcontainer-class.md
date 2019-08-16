---
title: Clase COleControlContainer
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 3aa2515b1731eafcb5e3bcfa22a56ebbc1cdfdfb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504323"
---
# <a name="colecontrolcontainer-class"></a>Clase COleControlContainer

Actúa como contenedor de control para controles ActiveX.

## <a name="syntax"></a>Sintaxis

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Construye un objeto `COleControlContainer`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Crea un sitio de control, hospedado por el contenedor.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informa a todos los controles hospedados que una propiedad de ambiente ha cambiado.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modifica el control de botón especificado.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Selecciona el botón de radio especificado de un grupo.|
|[COleControlContainer::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|
|[COleControlContainer::CreateOleFont](#createolefont)|Crea una fuente OLE.|
|[COleControlContainer::FindItem](#finditem)|Devuelve el sitio personalizado del control especificado.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Determina si el sitio de control está aceptando eventos.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Recupera la propiedad de ambiente especificada.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Recupera el control de cuadro de diálogo especificado.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Recupera el valor del control de cuadro de diálogo especificado.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Recupera el título del control de cuadro de diálogo especificado.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Determina si el contenedor controla los mensajes WM_SETFOCUS.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Controla los mensajes enviados a un control sin ventana.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Determina el estado del botón especificado.|
|[COleControlContainer::OnPaint](#onpaint)|Se llama para volver a dibujar una parte del contenedor.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Se llama cuando un control está a punto de activarse en contexto.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Se le llama cuando un control está a punto de desactivarse.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Lo llama el marco de trabajo cuando se reciben mensajes de desplazamiento desde una ventana secundaria.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Envía un mensaje al control especificado.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Establece el valor del control especificado.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Establece el texto del control especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Color de fondo del contenedor.|
|[COleControlContainer::m_crFore](#m_crfore)|Color de primer plano del contenedor.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Una lista de los sitios de control admitidos.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|El número de controles sin ventanas hospedados.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Puntero a la fuente OLE del sitio del control personalizado.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Puntero al sitio del control de captura.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Puntero al control que tiene actualmente el foco de entrada.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Puntero al control que está activado actualmente en contexto.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Puntero a la ventana que implementa el contenedor de control.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapa del sitio.|

## <a name="remarks"></a>Comentarios

Esto se hace proporcionando compatibilidad con uno o varios sitios de control ActiveX (implementados `COleControlSite`por). `COleControlContainer`implementa completamente las interfaces [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) y [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) , lo que permite que los controles ActiveX contenidos cumplan sus calificaciones como elementos en contexto.

Normalmente, esta clase se utiliza junto con `COccManager` y `COleControlSite` para implementar un contenedor de controles ActiveX personalizado, con sitios personalizados para uno o más controles ActiveX.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxocc. h

##  <a name="attachcontrolsite"></a>  COleControlContainer::AttachControlSite

Lo llama el marco de trabajo para crear y adjuntar un sitio de control.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a un objeto `CWnd` .

*nIDC*<br/>
IDENTIFICADOR del control que se va a adjuntar.

### <a name="remarks"></a>Comentarios

Invalide esta función si desea personalizar este proceso.

> [!NOTE]
>  Use el primer formulario de esta función si está vinculando estáticamente a la biblioteca MFC. Utilice la segunda forma si va a vincular dinámicamente a la biblioteca MFC.

##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange

Informa a todos los controles hospedados que una propiedad de ambiente ha cambiado.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
IDENTIFICADOR de envío de la propiedad de ambiente que se va a cambiar.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función cuando una propiedad de ambiente ha cambiado de valor. Invalide esta función para personalizar este comportamiento.

##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Modifica el estado actual del botón.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parámetros

*nIDButton*<br/>
IDENTIFICADOR del botón que se va a modificar.

*nCheck*<br/>
Especifica el estado del botón. Puede ser uno de los siguientes:

- BST_CHECKED establece el estado del botón en activado.

- BST_INDETERMINATE establece el estado del botón en atenuado, lo que indica un estado indeterminado. Use este valor solo si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE.

- BST_UNCHECKED establece el estado del botón en desactivado.

##  <a name="checkradiobutton"></a>  COleControlContainer::CheckRadioButton

Selecciona un botón de radio especificado en un grupo y borra los botones restantes en el grupo.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parámetros

*nIDFirstButton*<br/>
Especifica el identificador del primer botón de radio del grupo.

*nIDLastButton*<br/>
Especifica el identificador del último botón de radio del grupo.

*nIDCheckButton*<br/>
Especifica el identificador del botón de radio que se va a comprobar.

##  <a name="colecontrolcontainer"></a>  COleControlContainer::COleControlContainer

Construye un objeto `COleControlContainer`.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana primaria del contenedor del control.

### <a name="remarks"></a>Comentarios

Una vez que el objeto se haya creado correctamente, agregue un sitio de control personalizado con `AttachControlSite`una llamada a.

##  <a name="createcontrol"></a>  COleControlContainer::CreateControl

Crea un control ActiveX, hospedado por el `COleControlSite` objeto especificado.

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>Parámetros

*pWndCtrl*<br/>
Puntero al objeto Window que representa el control.

*clsid*<br/>
IDENTIFICADOR de clase único del control.

*lpszWindowName*<br/>
Puntero al texto que se va a mostrar en el control. Establece el valor de la propiedad de texto o título del control (si existe). Si es NULL, no se cambia la propiedad de texto o la leyenda del control.

*dwStyle*<br/>
Estilos de Windows. Los estilos disponibles se enumeran en la sección **comentarios** .

*rect*<br/>
Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto o una `RECT` estructura.

*nID*<br/>
Especifica el identificador de la ventana secundaria del control.

*pPersist*<br/>
Un puntero a un `CFile` que contiene el estado persistente del control. El valor predeterminado es NULL, lo que indica que el control se inicializa sin restaurar su estado desde un almacenamiento persistente. Si no es null, debe ser un puntero a un `CFile`objeto derivado de que contenga los datos persistentes del control, en forma de una secuencia o un almacenamiento. Estos datos se podrían haber guardado en una activación anterior del cliente. Puede contener otros datos, pero debe tener su puntero de lectura y escritura establecido en el primer byte de datos persistentes en el momento de la llamada `CreateControl`a. `CFile`

*bStorage*<br/>
Indica si los datos de *pPersist* deben interpretarse como `IStorage` datos `IStream` de o. Si los datos de *pPersist* son un almacenamiento, *BSTORAGE* debe ser true. Si los datos de *pPersist* son una secuencia, *BSTORAGE* debe ser false. El valor predeterminado es FALSE.

*bstrLicKey*<br/>
Datos de clave de licencia opcionales. Estos datos solo son necesarios para crear controles que requieran una clave de licencia en tiempo de ejecución. Si el control admite las licencias, debe proporcionar una clave de licencia para que la creación del control se realice correctamente. El valor predeterminado es NULL.

*ppNewSite*<br/>
Puntero al sitio de control existente que hospedará el control que se va a crear. El valor predeterminado es NULL, lo que indica que se creará automáticamente un nuevo sitio de control y se adjuntará al nuevo control.

*ppt*<br/>
Puntero a una `POINT` estructura que contiene la esquina superior izquierda del control. El tamaño del control viene determinado por el valor de *psize*. Los valores *PPT* y *psize* son un método opcional para especificar el tamaño y la posición del control.

*psize*<br/>
Puntero a una `SIZE` estructura que contiene el tamaño del control. La esquina superior izquierda viene determinada por el valor de *PPT*. Los valores *PPT* y *psize* son un método opcional para especificar el tamaño y la posición del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Solo se admite `CreateControl`un subconjunto de las marcas *dwStyle* de Windows:

- WS_VISIBLE crea una ventana que está inicialmente visible. Necesario si desea que el control esté visible inmediatamente, como las ventanas normales.

- WS_DISABLED crea una ventana que está deshabilitada inicialmente. Una ventana deshabilitada no puede recibir entradas del usuario. Se puede establecer si el control tiene una propiedad habilitada.

- WS_BORDER crea una ventana con un borde de línea fina. Se puede establecer si el control tiene una propiedad BorderStyle.

- WS_GROUP especifica el primer control de un grupo de controles. El usuario puede cambiar el foco del teclado de un control del grupo al siguiente mediante las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo e inicia el grupo siguiente.

- WS_TABSTOP especifica un control que puede recibir el foco del teclado cuando el usuario presiona la tecla TAB. Al presionar la tecla TAB, el foco de teclado cambia al siguiente control del estilo WS_TABSTOP.

Use la segunda sobrecarga para crear controles de tamaño predeterminado.

##  <a name="createolefont"></a>  COleControlContainer::CreateOleFont

Crea una fuente OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
Puntero a la fuente que va a utilizar el contenedor de controles.

##  <a name="finditem"></a>  COleControlContainer::FindItem

Busca el sitio personalizado que hospeda el elemento especificado.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del elemento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Puntero al sitio personalizado del elemento especificado.

##  <a name="freezeallevents"></a>  COleControlContainer::FreezeAllEvents

Determina si el contenedor omitirá los eventos de los sitios de control asociados o los aceptará.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parámetros

*bFreeze*<br/>
Distinto de cero si se van a procesar los eventos; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  No es necesario que el control detenga los eventos de activación si lo solicita el contenedor de control. Puede continuar la activación, pero el contenedor de controles omitirá todos los eventos subsiguientes.

##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp

Recupera el valor de una propiedad de ambiente especificada.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Un puntero a un sitio de control desde el que se recuperará la propiedad de ambiente.

*dispid*<br/>
El identificador de envío de la propiedad de ambiente deseada.

*pVarResult*<br/>
Puntero al valor de la propiedad de ambiente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="getdlgitem"></a>  COleControlContainer::GetDlgItem

Recupera un puntero al control o la ventana secundaria especificados en un cuadro de diálogo o en otra ventana.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del elemento de cuadro de diálogo que se va a recuperar.

*phWnd*<br/>
Puntero al identificador del objeto de ventana del elemento de cuadro de diálogo especificado.

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana del elemento de cuadro de diálogo.

##  <a name="getdlgitemint"></a>  COleControlContainer::GetDlgItemInt

Recupera el valor del texto traducido del control dado.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del control.

*lpTrans*<br/>
Puntero a una variable booleana que recibe un valor de function Success/Failure (TRUE indica que es correcto, FALSE indica un error).

*bSigned*<br/>
Especifica si la función debe examinar el texto de un signo menos al principio y devolver un valor entero con signo si encuentra uno. Si el parámetro *bSigned* es true, especificando que el valor que se va a recuperar es un valor entero con signo, convierta el valor devuelto a un tipo **int** . Para obtener información de error extendida, llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Valor devuelto

Si es correcto, la variable a la que apunta *lpTrans* se establece en true y el valor devuelto es el valor traducido del texto del control.

Si se produce un error en la función, la variable a la que apunta *lpTrans* se establece en false y el valor devuelto es cero. Tenga en cuenta que, puesto que cero es un valor traducido posible, un valor devuelto de cero no indica por sí mismo el error.

Si *lpTrans* es null, la función no devuelve información sobre el éxito o el error.

### <a name="remarks"></a>Comentarios

La función traduce el texto recuperado quitando los espacios adicionales al principio del texto y, a continuación, convierte los dígitos decimales. La función deja de traducir cuando llega al final del texto o encuentra un carácter no numérico.

Esta función devuelve cero si el valor traducido es mayor que INT_MAX (para números con signo) o UINT_MAX (para números sin signo).

##  <a name="getdlgitemtext"></a>  COleControlContainer::GetDlgItemText

Recupera el texto del control dado.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del control.

*lpStr*<br/>
Puntero al texto del control.

*nMaxCount*<br/>
Especifica la longitud máxima, en caracteres, de la cadena que se va a copiar en el búfer señalado por *lpStr*. Si la longitud de la cadena supera el límite, la cadena se trunca.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto especifica el número de caracteres copiados en el búfer, sin incluir el carácter nulo de terminación.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

##  <a name="handlesetfocus"></a>  COleControlContainer::HandleSetFocus

Determina si el contenedor controla los mensajes WM_SETFOCUS.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el contenedor administra mensajes WM_SETFOCUS; de lo contrario, es cero.

##  <a name="handlewindowlessmessage"></a>  COleControlContainer::HandleWindowlessMessage

Procesa los mensajes de ventana para los controles sin ventanas.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parámetros

*message*<br/>
Identificador del mensaje de ventana, proporcionado por Windows.

*wParam*<br/>
Parámetro del mensaje; proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor del parámetro de *mensaje* .

*lParam*<br/>
Parámetro del mensaje; proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor del parámetro de *mensaje* .

*plResult*<br/>
Código de resultado de Windows. Especifica el resultado del procesamiento del mensaje y depende del mensaje enviado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Invalide esta función para personalizar el control de los mensajes de control sin ventanas.

##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked

Determina el estado del botón especificado.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parámetros

*nIDButton*<br/>
Identificador del control de botón.

### <a name="return-value"></a>Valor devuelto

El valor devuelto de un botón creado con el estilo BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON o BS_3STATE. Puede ser uno de los siguientes:

- El botón BST_CHECKED está activado.

- El botón BST_INDETERMINATE está atenuado, lo que indica un estado indeterminado (solo se aplica si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE).

- El botón BST_UNCHECKED está desactivado.

### <a name="remarks"></a>Comentarios

Si el botón es un control de tres Estados, la función miembro determina si está atenuada, activada o no.

##  <a name="m_crback"></a>  COleControlContainer::m_crBack

Color de fondo del contenedor.

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>  COleControlContainer::m_crFore

Color de primer plano del contenedor.

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds

Una lista de los sitios de control hospedados por el contenedor.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>  COleControlContainer::m_nWindowlessControls

El número de controles sin ventanas hospedados por el contenedor de control.

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont

Puntero a la fuente OLE del sitio del control personalizado.

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

Puntero al sitio del control de captura.

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

Puntero al sitio de control que actualmente tiene el foco de entrada.

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

Puntero al sitio de control que está activado en contexto.

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>  COleControlContainer::m_pWnd

Puntero al objeto de ventana asociado al contenedor.

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

Mapa del sitio.

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>  COleControlContainer::OnPaint

Lo llama el marco de trabajo para controlar las solicitudes WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Un puntero al contexto de dispositivo usado por el contenedor.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha controlado el mensaje; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Invalide esta función para personalizar el proceso de dibujo.

##  <a name="onuiactivate"></a>  COleControlContainer::OnUIActivate

Lo llama el marco de trabajo cuando el sitio del control, al que apunta *pSite*, está a punto de activarse en contexto.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Un puntero al sitio de control que está a punto de activarse en contexto.

### <a name="remarks"></a>Comentarios

La activación en contexto significa que el menú principal del contenedor se reemplaza por un menú compuesto en contexto.

##  <a name="onuideactivate"></a>  COleControlContainer::OnUIDeactivate

Lo llama el marco de trabajo cuando el sitio del control, al que apunta *pSite*, está a punto de desactivarse.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Un puntero al sitio de control que se va a desactivar.

### <a name="remarks"></a>Comentarios

Cuando se recibe esta notificación, el contenedor debe volver a instalar su interfaz de usuario y tomar el foco.

##  <a name="scrollchildren"></a>  COleControlContainer::ScrollChildren

Lo llama el marco de trabajo cuando se reciben mensajes de desplazamiento desde una ventana secundaria.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parámetros

*dx*<br/>
Cantidad, en píxeles, del desplazamiento a lo largo del eje x.

*dy*<br/>
Cantidad, en píxeles, del desplazamiento a lo largo del eje y.

##  <a name="senddlgitemmessage"></a>  COleControlContainer::SendDlgItemMessage

Envía un mensaje al control especificado.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Especifica el identificador del control que recibe el mensaje.

*message*<br/>
Especifica el mensaje que se va a enviar.

*wParam*<br/>
Especifica información adicional específica del mensaje.

*lParam*<br/>
Especifica información adicional específica del mensaje.

##  <a name="setdlgitemint"></a>  COleControlContainer::SetDlgItemInt

Establece el texto de un control en un cuadro de diálogo en la representación de cadena de un valor entero especificado.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del control.

*nValue*<br/>
Valor entero que se va a mostrar.

*bSigned*<br/>
Especifica si el parámetro *Nvalor* está firmado o sin signo. Si este parámetro es TRUE, *Nvalor* está firmado. Si este parámetro es TRUE y *Nvalor* es menor que cero, se coloca un signo menos delante del primer dígito de la cadena. Si este parámetro es FALSE, *Nvalor* es sin signo.

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

Establece el texto del control especificado, utilizando el texto contenido en *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del control.

*lpszString*<br/>
Puntero al texto del control.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite (clase)](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager (clase)](../../mfc/reference/coccmanager-class.md)
