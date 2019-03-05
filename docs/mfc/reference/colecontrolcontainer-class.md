---
title: COleControlContainer (clase)
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
ms.openlocfilehash: 6e97f7ceafb92098d701cba64b4ec01d26d3991a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274991"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer (clase)

Actúa como contenedor de control para controles ActiveX.

## <a name="syntax"></a>Sintaxis

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Construye un objeto `COleControlContainer`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Crea un sitio del control hospedado por el contenedor.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informa a hospedado todos los controles que ha cambiado una propiedad de ambiente.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Modifica el control de botón especificado.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Selecciona el botón de radio especificado de un grupo.|
|[COleControlContainer::CreateControl](#createcontrol)|Crea un control ActiveX hospedado.|
|[COleControlContainer::CreateOleFont](#createolefont)|Crea una fuente OLE.|
|[COleControlContainer::FindItem](#finditem)|Devuelve el sitio personalizado del control especificado.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Determina si el sitio del control está aceptando los eventos.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Recupera la propiedad de ambiente especificada.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Recupera el control de cuadro de diálogo especificado.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Recupera el valor del control de cuadro de diálogo especificado.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Recupera el título del control de cuadro de diálogo especificado.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Determina si el contenedor controla los mensajes WM_SETFOCUS.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Controla los mensajes enviados a un control sin ventanas.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Determina el estado del botón especificado.|
|[COleControlContainer::OnPaint](#onpaint)|Se llama para volver a dibujar una parte del contenedor.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Se llama cuando un control se va a activar en contexto.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Se llama cuando un control está a punto de desactivarse.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Lo llama el marco de trabajo cuando se reciben mensajes de desplazamiento de una ventana secundaria.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Envía un mensaje al control especificado.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Establece el valor del control especificado.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Establece el texto del control especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|El color de fondo del contenedor.|
|[COleControlContainer::m_crFore](#m_crfore)|El color de primer plano del contenedor.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Una lista de los sitios de control admitidos.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|El número de controles sin ventana hospedados.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Un puntero a la fuente OLE de sitio del control personalizado.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Puntero al sitio del control de captura.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Puntero al control que actualmente tiene el foco de entrada.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Puntero al control que está actualmente activado en el contexto.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Puntero a la ventana implementar el contenedor del control.|
|[COleControlContainer::m_siteMap](#m_sitemap)|El mapa del sitio.|

## <a name="remarks"></a>Comentarios

Esto se hace proporcionando compatibilidad para uno o varios sitios de control ActiveX (implementado por `COleControlSite`). `COleControlContainer` implementa por completo el [IOleInPlaceFrame](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceframe) y [IOleContainer](/windows/desktop/api/oleidl/nn-oleidl-iolecontainer) interfaces, lo que permite a los controles ActiveX contenidos cumplir sus cualificaciones como elementos en contexto.

Normalmente, esta clase se utiliza junto con `COccManager` y `COleControlSite` para implementar un contenedor de controles ActiveX personalizado, con sitios personalizados para uno o varios controles ActiveX.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxocc.h

##  <a name="attachcontrolsite"></a>  COleControlContainer::AttachControlSite

Lo llama el marco para crear y asociar un sitio del control.

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
El identificador del control que se adjuntará.

### <a name="remarks"></a>Comentarios

Reemplace esta función si desea personalizar este proceso.

> [!NOTE]
>  Use la primera forma de esta función si se vincula estáticamente a la biblioteca MFC. Use el segundo formulario si se vincula dinámicamente a la biblioteca MFC.

##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange

Informa a hospedado todos los controles que ha cambiado una propiedad de ambiente.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parámetros

*dispid*<br/>
Identificador de envío de la propiedad de ambiente que se está cambiando.

### <a name="remarks"></a>Comentarios

Esta función se llama el marco de trabajo cuando una propiedad de ambiente ha cambiado el valor. Reemplace esta función para personalizar este comportamiento.

##  <a name="checkdlgbutton"></a>  COleControlContainer::CheckDlgButton

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

- BST_CHECKED conjuntos que comprueban el estado del botón.

- BST_INDETERMINATE establece el estado del botón a deshabilitado, que indica un estado indeterminado. Use este valor solo si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE.

- Conjuntos BST_UNCHECKED el estado del botón para borra.

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
Un puntero a la ventana primaria del contenedor del control.

### <a name="remarks"></a>Comentarios

Una vez que el objeto se ha creado correctamente, agregue un sitio de control personalizado con una llamada a `AttachControlSite`.

##  <a name="createcontrol"></a>  COleControlContainer::CreateControl

Crea un control ActiveX, hospedado por especificado `COleControlSite` objeto.

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
Un puntero al objeto window que representa el control.

*clsid*<br/>
El identificador de clase única del control.

*lpszWindowName*<br/>
Un puntero al texto que se mostrará en el control. Establece el valor de propiedad de leyenda o el texto del control (si existe). Si es NULL, no se cambia la propiedad de leyenda o el texto del control.

*dwStyle*<br/>
Estilos de Windows. Los estilos disponibles aparecen en la **comentarios** sección.

*rect*<br/>
Especifica el tamaño y la posición del control. Puede ser un `CRect` objeto o un `RECT` estructura.

*nID*<br/>
Especifica el identificador de ventana secundaria del control

*pPersist*<br/>
Un puntero a un `CFile` que contiene el estado persistente para el control. El valor predeterminado es NULL, que indica que el control se inicializa sin restaurar su estado de cualquier almacenamiento persistente. Si no es NULL, debe ser un puntero a un `CFile`: objeto que contiene los datos persistentes del control, en forma de una secuencia o un almacenamiento derivado. Estos datos se ha guardado en una activación anterior del cliente. El `CFile` puede contener otros datos, pero debe tener su puntero de lectura y escritura establecido en el primer byte de datos persistentes en el momento de la llamada a `CreateControl`.

*bStorage*<br/>
Indica si los datos de *pPersist* debe interpretarse como `IStorage` o `IStream` datos. Si los datos de *pPersist* es un almacenamiento, *bStorage* debe ser verdadero. Si los datos de *pPersist* es una secuencia, *bStorage* debe ser FALSE. El valor predeterminado es FALSE.

*bstrLicKey*<br/>
Datos de clave de licencia opcional. Estos datos solo se necesitan para crear los controles que requieren una clave de licencia de tiempo de ejecución. Si el control es compatible con las licencias, debe proporcionar una clave de licencia para la creación del control se realice correctamente. El valor predeterminado es NULL.

*ppNewSite*<br/>
Un puntero al sitio del control existente que se va a hospedar el control que se está creando. El valor predeterminado es NULL, que indica que un nuevo sitio de control se se crea automáticamente y se adjunta al nuevo control.

*ppt*<br/>
Un puntero a un `POINT` estructura que contiene la esquina superior izquierda del control. El tamaño del control viene determinada por el valor de *psize*. El *ppt* y *psize* los valores son un método opcional para especificar el tamaño y posición del control.

*psize*<br/>
Un puntero a un `SIZE` estructura que contiene el tamaño del control. La esquina superior izquierda viene determinada por el valor de *ppt*. El *ppt* y *psize* los valores son un método opcional para especificar el tamaño y posición del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Solo un subconjunto de la Windows *dwStyle* marcas son compatibles con `CreateControl`:

- WS_VISIBLE crea una ventana que está visible inicialmente. Necesario si desea que el control sea visible inmediatamente, como las ventanas normales.

- WS_DISABLED crea una ventana que está deshabilitada inicialmente. Una ventana deshabilitada no puede recibir entradas del usuario. Se puede establecer si el control tiene una propiedad Enabled.

- WS_BORDER crea una ventana con un borde de línea fino. Se puede establecer si el control tiene una propiedad de estilo de borde.

- WS_GROUP especifica el primer control de un grupo de controles. El usuario puede cambiar el foco de teclado de un control en el grupo a otro utilizando las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El control siguiente con el estilo WS_GROUP finaliza el grupo e inicia el grupo siguiente.

- WS_TABSTOP especifica un control que puede recibir el foco de teclado cuando el usuario presiona la tecla TAB. Al presionar la tecla TAB, cambia el foco del teclado al siguiente control del estilo WS_TABSTOP.

Usar la segunda sobrecarga para crear controles de tamaño predeterminado.

##  <a name="createolefont"></a>  COleControlContainer::CreateOleFont

Crea una fuente OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
Un puntero a la fuente que va a usar el contenedor del control.

##  <a name="finditem"></a>  COleControlContainer::FindItem

Busca el sitio personalizado que hospeda el elemento especificado.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
El identificador del elemento que se encuentra.

### <a name="return-value"></a>Valor devuelto

Un puntero al sitio personalizado del elemento especificado.

##  <a name="freezeallevents"></a>  COleControlContainer::FreezeAllEvents

Determina si el contenedor se omita algunos eventos desde los sitios de control adjunto o aceptarlos.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parámetros

*bFreeze*<br/>
Distinto de cero si se procesarán los eventos; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  El control no es necesario detener la activación de eventos si lo solicita el contenedor del control. Puede continuar la activación, pero se omitirá todos los eventos subsiguientes en el contenedor del control.

##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp

Recupera el valor de propiedad de ambiente especificada.

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
Identificador de envío de la propiedad de ambiente deseada.

*pVarResult*<br/>
Un puntero al valor de la propiedad de ambiente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="getdlgitem"></a>  COleControlContainer::GetDlgItem

Recupera un puntero a la ventana de control o elemento secundario especificada en un cuadro de diálogo u otra ventana.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador del elemento de cuadro de diálogo para recuperar.

*phWnd*<br/>
Un puntero al identificador de objeto de ventana del elemento de cuadro de diálogo especificado.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana del elemento de cuadro de diálogo.

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
El identificador del control.

*lpTrans*<br/>
Puntero a una variable booleana que recibe un valor de correcto o con errores de función (TRUE indica éxito, FALSE indica un error).

*bSigned*<br/>
Especifica si la función debe examinar el texto de un signo menos al principio y devolver un valor entero con signo si encuentra uno. Si el *bSigned* parámetro es TRUE, especifica que el valor que se va a recuperar un valor entero con signo, convierta el valor devuelto para un **int** tipo. Para obtener información de error extendida, llame a [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="return-value"></a>Valor devuelto

Si es correcto, la variable apunta a *lpTrans* está establecida en TRUE, y el valor devuelto es el valor traducido del texto del control.

Si se produce un error en la función, la variable apunta a *lpTrans* está establecida en FALSE, y el valor devuelto es cero. Tenga en cuenta que, desde cero es un posible valor traducido, un valor devuelto de cero no por sí mismo indica error.

Si *lpTrans* es NULL, la función no devuelve ninguna información sobre el éxito o error.

### <a name="remarks"></a>Comentarios

La función convierte el texto recuperado por la eliminación de todos los espacios adicionales al principio del texto y, a continuación, convertir los dígitos decimales. La función deja de traducir cuando llega al final del texto o se encuentra un carácter numérico.

Esta función devuelve cero si el valor convertido es mayor que INT_MAX (para números con signo) o UINT_MAX (para números sin signo).

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
El identificador del control.

*lpStr*<br/>
Puntero al texto del control.

*nMaxCount*<br/>
Especifica la longitud máxima, en caracteres, de la cadena que se copiarán en el búfer señalado por *lpStr*. Si la longitud de la cadena supera el límite, se trunca la cadena.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto especifica el número de caracteres copiados en el búfer, sin incluir el carácter nulo de terminación.

Si la función no se realiza correctamente, el valor devuelto es cero. Para obtener información de error extendida, llame a [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

##  <a name="handlesetfocus"></a>  COleControlContainer::HandleSetFocus

Determina si el contenedor controla los mensajes WM_SETFOCUS.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el contenedor controla los mensajes WM_SETFOCUS; en caso contrario, es cero.

##  <a name="handlewindowlessmessage"></a>  COleControlContainer::HandleWindowlessMessage

Procesa los mensajes de ventana para controles sin ventana.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parámetros

*message*<br/>
El identificador del mensaje de ventana, proporcionado por Windows.

*wParam*<br/>
Parámetro del mensaje. proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor de la *mensaje* parámetro.

*lParam*<br/>
Parámetro del mensaje. proporcionado por Windows. Especifica información adicional específica del mensaje. El contenido de este parámetro depende del valor de la *mensaje* parámetro.

*plResult*<br/>
Código de resultado de Windows. Especifica el resultado del procesamiento del mensaje y depende del mensaje enviado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Reemplace esta función para personalizar el tratamiento de mensajes de control sin ventanas.

##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked

Determina el estado del botón especificado.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parámetros

*nIDButton*<br/>
El identificador del control de botón.

### <a name="return-value"></a>Valor devuelto

El valor devuelto de un botón creado con el estilo BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON o BS_3STATE. Puede ser uno de los siguientes:

- Botón BST_CHECKED está activada.

- Botón BST_INDETERMINATE está atenuada, que indica un estado indeterminado (se aplica sólo si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE).

- Botón BST_UNCHECKED está desactivada.

### <a name="remarks"></a>Comentarios

Si el botón es un control de tres estados, la función miembro determina si se está atenuado, está activada, o ninguno.

##  <a name="m_crback"></a>  COleControlContainer::m_crBack

El color de fondo del contenedor.

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>  COleControlContainer::m_crFore

El color de primer plano del contenedor.

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds

Una lista de los sitios del control hospedado por el contenedor.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>  COleControlContainer::m_nWindowlessControls

El número de controles sin ventana hospedado por el contenedor del control.

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont

Un puntero a la fuente OLE de sitio del control personalizado.

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

Puntero al sitio del control de captura.

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

Un puntero al sitio del control que actualmente tiene el foco de entrada.

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

Un puntero al sitio del control que está activado en el contexto.

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>  COleControlContainer::m_pWnd

Un puntero al objeto de ventana asociado al contenedor.

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

El mapa del sitio.

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
Un puntero al contexto de dispositivo utilizado por el contenedor.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha controlado el mensaje; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Reemplace esta función para personalizar el proceso de dibujo.

##  <a name="onuiactivate"></a>  COleControlContainer::OnUIActivate

Lo llama el marco cuando el sitio del control, que señala *pSite*, está a punto de activar en contexto.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Un puntero al sitio del control va a activar en contexto.

### <a name="remarks"></a>Comentarios

Activación en contexto significa que el menú principal del contenedor se reemplaza con un menú compuesto en contexto.

##  <a name="onuideactivate"></a>  COleControlContainer::OnUIDeactivate

Lo llama el marco cuando el sitio del control, que señala *pSite*, está a punto de desactivarse.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parámetros

*pSite*<br/>
Un puntero al sitio del control va a desactivar.

### <a name="remarks"></a>Comentarios

Cuando se recibe esta notificación, el contenedor debe volver a instalar su interfaz de usuario y tomar el foco.

##  <a name="scrollchildren"></a>  COleControlContainer::ScrollChildren

Lo llama el marco de trabajo cuando se reciben mensajes de desplazamiento de una ventana secundaria.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parámetros

*dx*<br/>
La cantidad, en píxeles, de desplazamiento a lo largo del eje x.

*dy*<br/>
La cantidad, en píxeles, de desplazamiento a lo largo del eje y.

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
Especifica que se envíe el mensaje.

*wParam*<br/>
Especifica información adicional específica del mensaje.

*lParam*<br/>
Especifica información adicional específica del mensaje.

##  <a name="setdlgitemint"></a>  COleControlContainer::SetDlgItemInt

Establece el texto de un control en un cuadro de diálogo para la representación de cadena de un valor entero especificado.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
El identificador del control.

*nValue*<br/>
El valor entero que se mostrará.

*bSigned*<br/>
Especifica si el *nvalor* parámetro es con o sin signo. Si este parámetro es TRUE, *nvalor* está firmado. Si este parámetro es TRUE y *nvalor* es menor que cero, un inicio de sesión se coloca delante del primer dígito en la cadena de menos. Si este parámetro es FALSE, *nvalor* es sin signo.

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

Establece el texto del control especificado, utilizando el texto contenido en *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
El identificador del control.

*lpszString*<br/>
Puntero al texto del control.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite (clase)](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager (clase)](../../mfc/reference/coccmanager-class.md)
