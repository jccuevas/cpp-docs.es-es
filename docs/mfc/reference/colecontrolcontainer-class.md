---
title: COleControlContainer Clase
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
ms.openlocfilehash: b1737b2ac114181a4245fff027b756ca30b64129
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366180"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer Clase

Actúa como contenedor de control para controles ActiveX.

## <a name="syntax"></a>Sintaxis

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Construye un objeto `COleControlContainer`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Crea un sitio de control, hospedado por el contenedor.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informa a todos los controles hospedados de que una propiedad ambiental ha cambiado.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modifica el control de botón especificado.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Selecciona el botón de opción especificado de un grupo.|
|[COleControlContainer::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|
|[COleControlContainer::CreateOleFont](#createolefont)|Crea una fuente OLE.|
|[COleControlContainer::FindItem](#finditem)|Devuelve el sitio personalizado del control especificado.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Determina si el sitio de control acepta eventos.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Recupera la propiedad ambiente especificada.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Recupera el control de cuadro de diálogo especificado.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Recupera el valor del control de cuadro de diálogo especificado.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Recupera el título del control de cuadro de diálogo especificado.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Determina si el contenedor controla WM_SETFOCUS mensajes.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Controla los mensajes enviados a un control sin ventanas.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Determina el estado del botón especificado.|
|[COleControlContainer::OnPaint](#onpaint)|Se llama para volver a pintar una parte del contenedor.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Se llama cuando un control está a punto de activarse in situ.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Se llama cuando un control está a punto de desactivarse.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Llamado por el marco de trabajo cuando se reciben mensajes de desplazamiento desde una ventana secundaria.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Envía un mensaje al control especificado.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Establece el valor del control especificado.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Establece el texto del control especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|El color de fondo del contenedor.|
|[COleControlContainer::m_crFore](#m_crfore)|El color de primer plano del contenedor.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Una lista de los sitios de control admitidos.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|El número de controles hospedados sin ventanas.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Un puntero a la fuente OLE del sitio de control personalizado.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Puntero al sitio de control de captura.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Puntero al control que actualmente tiene el foco de entrada.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Puntero al control que está activado actualmente en contexto.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Puntero a la ventana que implementa el contenedor de control.|
|[COleControlContainer::m_siteMap](#m_sitemap)|El mapa del sitio.|

## <a name="remarks"></a>Observaciones

Esto se hace proporcionando compatibilidad con uno o más `COleControlSite`sitios de control ActiveX (implementados por ). `COleControlContainer`implementa completamente el [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) y [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) interfaces, lo que permite que los controles ActiveX contenidos para cumplir sus calificaciones como elementos en el lugar.

Normalmente, esta clase se `COccManager` usa `COleControlSite` junto con e implementar un contenedor de controles ActiveX personalizado, con sitios personalizados para uno o varios controles ActiveX.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxocc.h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

Llamado por el marco de trabajo para crear y adjuntar un sitio de control.

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
El identificador del control que se va a adjuntar.

### <a name="remarks"></a>Observaciones

Invalide esta función si desea personalizar este proceso.

> [!NOTE]
> Utilice la primera forma de esta función si está vinculando estáticamente a la biblioteca MFC. Use el segundo formulario si está vinculando dinámicamente a la biblioteca MFC.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

Informa a todos los controles hospedados de que una propiedad ambiental ha cambiado.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
El identificador de envío de la propiedad ambiental que se va a cambiar.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función cuando una propiedad ambiente ha cambiado el valor. Invalide esta función para personalizar este comportamiento.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Modifica el estado actual del botón.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parámetros

*nIDButton*<br/>
El identificador del botón que se va a modificar.

*nCheck*<br/>
Especifica el estado del botón. Puede ser uno de los siguientes:

- BST_CHECKED Establece el estado del botón en marcado.

- BST_INDETERMINATE Establece el estado del botón en atenuado, lo que indica un estado indeterminado. Utilice este valor solo si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE.

- BST_UNCHECKED Establece el estado del botón en borrar.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

Selecciona un botón de opción especificado en un grupo y borra los botones restantes del grupo.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parámetros

*nIDFirstButton*<br/>
Especifica el identificador del primer botón de opción del grupo.

*nIDLastButton*<br/>
Especifica el identificador del último botón de opción del grupo.

*nIDCheckButton*<br/>
Especifica el identificador del botón de opción que se va a comprobar.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

Construye un objeto `COleControlContainer`.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Un puntero a la ventana primaria del contenedor de control.

### <a name="remarks"></a>Observaciones

Una vez que el objeto se haya creado correctamente, `AttachControlSite`agregue un sitio de control personalizado con una llamada a .

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer::CreateControl

Crea un control ActiveX, hospedado `COleControlSite` por el objeto especificado.

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
Puntero al objeto de ventana que representa el control.

*clsid*<br/>
El identificador de clase único del control.

*lpszWindowName*<br/>
Puntero al texto que se mostrará en el control. Establece el valor de la propiedad Caption o Text del control (si existe). Si NULL, no se cambia la propiedad Caption o Text del control.

*dwStyle*<br/>
Estilos de Windows. Los estilos disponibles se enumeran en la sección **Comentarios.**

*Rect*<br/>
Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto `RECT` o una estructura.

*nID*<br/>
Especifica el identificador de ventana secundaria del control.

*pPersist*<br/>
Puntero a `CFile` un que contiene el estado persistente para el control. El valor predeterminado es NULL, lo que indica que el control se inicializa sin restaurar su estado desde cualquier almacenamiento persistente. Si no es NULL, debe `CFile`ser un puntero a un objeto derivado que contiene los datos persistentes del control, en forma de una secuencia o un almacenamiento. Estos datos podrían haberse guardado en una activación anterior del cliente. Puede `CFile` contener otros datos, pero debe tener su puntero de lectura y escritura establecido `CreateControl`en el primer byte de datos persistentes en el momento de la llamada a .

*bAlmacenamiento*<br/>
Indica si los datos de *pPersist* `IStorage` deben `IStream` interpretarse como datos o datos. Si los datos de *pPersist* es un almacenamiento, *bStorage* debe ser TRUE. Si los datos de *pPersist* es una secuencia, *bStorage* debe ser FALSE. El valor predeterminado es FALSE.

*bstrLicKey*<br/>
Datos de clave de licencia opcionales. Estos datos solo son necesarios para crear controles que requieren una clave de licencia en tiempo de ejecución. Si el control admite licencias, debe proporcionar una clave de licencia para que la creación del control se realice correctamente. El valor predeterminado es NULL.

*ppNewSite*<br/>
Puntero al sitio de control existente que hospedará el control que se está creando. El valor predeterminado es NULL, lo que indica que se creará automáticamente un nuevo sitio de control y se adjuntará al nuevo control.

*Ppt*<br/>
Puntero a `POINT` una estructura que contiene la esquina superior izquierda del control. El tamaño del control viene determinado por el valor de *psize*. Los valores *ppt* y *psize* son un método opcional para especificar el tamaño y la posición del control.

*psize*<br/>
Puntero a `SIZE` una estructura que contiene el tamaño del control. La esquina superior izquierda viene determinada por el valor de *ppt*. Los valores *ppt* y *psize* son un método opcional para especificar el tamaño y la posición del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Solo un subconjunto de las marcas `CreateControl` *dwStyle* de Windows son compatibles con:

- WS_VISIBLE Crea una ventana que está visible inicialmente. Necesario si desea que el control sea visible inmediatamente, como ventanas normales.

- WS_DISABLED Crea una ventana que está deshabilitada inicialmente. Una ventana deshabilitada no puede recibir la entrada del usuario. Se puede establecer si el control tiene un Enabled propiedad.

- WS_BORDER Crea una ventana con un borde de línea delgada. Se puede establecer si el control tiene un BorderStyle propiedad.

- WS_GROUP Especifica el primer control de un grupo de controles. El usuario puede cambiar el foco del teclado de un control del grupo al siguiente mediante las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo e inicia el siguiente grupo.

- WS_TABSTOP Especifica un control que puede recibir el foco del teclado cuando el usuario presiona la tecla TAB. Al pulsar la tecla TAB, el foco del teclado se muestra al siguiente control del estilo WS_TABSTOP.

Utilice la segunda sobrecarga para crear controles de tamaño predeterminado.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer::CreateOleFont

Crea una fuente OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
Un puntero a la fuente que usará el contenedor de controles.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer::FindItem

Busca el sitio personalizado que hospeda el elemento especificado.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del elemento que se va a encontrar.

### <a name="return-value"></a>Valor devuelto

Un puntero al sitio personalizado del elemento especificado.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

Determina si el contenedor omitirá los eventos de los sitios de control adjuntos o los aceptará.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parámetros

*bFreeze*<br/>
Distinto de cero si se procesarán los eventos; de lo contrario 0.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> El control no es necesario para detener los eventos de desencadenamiento si lo solicita el contenedor de control. Puede continuar la activación, pero el contenedor de control omitirá todos los eventos subsiguientes.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer::GetAmbientProp

Recupera el valor de una propiedad ambiente especificada.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Puntero a un sitio de control desde el que se recuperará la propiedad ambiente.

*dispid*<br/>
El ID de envío de la propiedad ambiental deseada.

*pVarResult*<br/>
Un puntero al valor de la propiedad ambiente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer::GetDlgItem

Recupera un puntero al control especificado o a la ventana secundaria en un cuadro de diálogo u otra ventana.

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

Un puntero a la ventana del elemento de cuadro de diálogo.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

Recupera el valor del texto traducido del control especificado.

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
Puntero a una variable booleana que recibe un valor de error o éxito de la función (TRUE indica que se ha realizado correctamente, FALSE indica un error).

*bFirmado*<br/>
Especifica si la función debe examinar el texto de un signo menos al principio y devolver un valor entero con signo si encuentra uno. Si el *bSigned* parámetro es TRUE, especificando que el valor que se va a recuperar es un valor entero con signo, convertir el valor devuelto a un tipo **int.** Para obtener información de error extendida, llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, la variable a la que apunta *lpTrans* se establece en TRUE y el valor devuelto es el valor traducido del texto del control.

Si se produce un error en la función, la variable a la que apunta *lpTrans* se establece en FALSE y el valor devuelto es cero. Tenga en cuenta que, dado que cero es un posible valor traducido, un valor devuelto de cero no indica por sí mismo un error.

Si *lpTrans* es NULL, la función no devuelve información sobre el éxito o el error.

### <a name="remarks"></a>Observaciones

La función traduce el texto recuperado eliminando cualquier espacio adicional al principio del texto y, a continuación, convirtiendo los dígitos decimales. La función deja de traducir cuando llega al final del texto o encuentra un carácter no numérico.

Esta función devuelve cero si el valor traducido es mayor que INT_MAX (para números con signo) o UINT_MAX (para números sin signo).

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

Recupera el texto del control especificado.

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
Especifica la longitud máxima, en caracteres, de la cadena que se va a copiar en el búfer al que apunta *lpStr*. Si la longitud de la cadena supera el límite, la cadena se trunca.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto especifica el número de caracteres copiados en el búfer, sin incluir el carácter nulo de terminación.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

Determina si el contenedor controla WM_SETFOCUS mensajes.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el contenedor controla WM_SETFOCUS mensajes; de lo contrario cero.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

Procesa los mensajes de ventana para los controles sin ventanas.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parámetros

*Mensaje*<br/>
Identificador del mensaje de ventana, proporcionado por Windows.

*wParam*<br/>
Parámetro del mensaje; proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor del parámetro *message.*

*lParam*<br/>
Parámetro del mensaje; proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor del parámetro *message.*

*plResult*<br/>
Código de resultado de Windows. Especifica el resultado del procesamiento de mensajes y depende del mensaje enviado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Invalide esta función para personalizar el control de los mensajes de control sin ventanas.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked

Determina el estado del botón especificado.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parámetros

*nIDButton*<br/>
Identificador del control de botón.

### <a name="return-value"></a>Valor devuelto

El valor devuelto, a partir de un botón creado con el estilo BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON o BS_3STATE. Puede ser uno de los siguientes:

- BST_CHECKED está marcada.

- BST_INDETERMINATE Button está atenuado, lo que indica un estado indeterminado (solo se aplica si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE).

- BST_UNCHECKED Button está desactivado.

### <a name="remarks"></a>Observaciones

Si el botón es un control de tres estados, la función miembro determina si está atenuado, comprobado o ninguno.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COleControlContainer::m_crBack

El color de fondo del contenedor.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COleControlContainer::m_crFore

El color de primer plano del contenedor.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

Una lista de los sitios de control hospedados por el contenedor.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

El número de controles sin ventanas hospedados por el contenedor de controles.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COleControlContainer::m_pOleFont

Un puntero a la fuente OLE del sitio de control personalizado.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture

Puntero al sitio de control de captura.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus

Puntero al sitio de control que actualmente tiene el foco de entrada.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive

Puntero al sitio de control que está activado in situ.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COleControlContainer::m_pWnd

Puntero al objeto de ventana asociado al contenedor.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COleControlContainer::m_siteMap

El mapa del sitio.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer::OnPaint

Llamado por el marco de trabajo para controlar WM_PAINT solicitudes.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto del dispositivo utilizado por el contenedor.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controló el mensaje; de lo contrario cero.

### <a name="remarks"></a>Observaciones

Reemplace esta función para personalizar el proceso de pintura.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer::OnUIActivate

Llamado por el marco de trabajo cuando el sitio de control, señalado por *pSite*, está a punto de activarse in situ.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Un puntero al sitio de control a punto de activarse en contexto.

### <a name="remarks"></a>Observaciones

La activación in situ significa que el menú principal del contenedor se sustituye por un menú compuesto in situ.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

Llamado por el marco de trabajo cuando el sitio de control, señalado por *pSite*, está a punto de desactivarse.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Un puntero al sitio de control a punto de desactivarse.

### <a name="remarks"></a>Observaciones

Cuando se recibe esta notificación, el contenedor debe reinstalar su interfaz de usuario y ponerse el foco.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer::ScrollChildren

Llamado por el marco de trabajo cuando se reciben mensajes de desplazamiento desde una ventana secundaria.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parámetros

*Dx*<br/>
La cantidad, en píxeles, de desplazarse a lo largo del eje X.

*Dy*<br/>
La cantidad, en píxeles, de desplazarse a lo largo del eje Y.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

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

*Mensaje*<br/>
Especifica el mensaje que se va a enviar.

*wParam*<br/>
Especifica información adicional específica del mensaje.

*lParam*<br/>
Especifica información adicional específica del mensaje.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

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

*nValor*<br/>
El valor entero que se va a mostrar.

*bFirmado*<br/>
Especifica si el *nValue* parámetro está firmado o sin signo. Si este parámetro es TRUE, *nValue* está firmado. Si este parámetro es TRUE y *nValue* es menor que cero, se coloca un signo menos antes del primer dígito de la cadena. Si este parámetro es FALSE, *nValue* no está firmado.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText

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

## <a name="see-also"></a>Consulte también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleControlSite](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager (clase)](../../mfc/reference/coccmanager-class.md)
