---
title: CDialog (clase)
ms.date: 09/07/2019
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
ms.openlocfilehash: b07190c70fb11950b25aff45fb10e850c0e81b24
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907606"
---
# <a name="cdialog-class"></a>CDialog (clase)

La clase base utilizada para mostrar cuadros de diálogo en la pantalla.

## <a name="syntax"></a>Sintaxis

```
class CDialog : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Construye un objeto `CDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDialog::Create](#create)|Inicializa el objeto `CDialog`. Crea un cuadro de diálogo no modal y lo adjunta al `CDialog` objeto.|
|[CDialog::CreateIndirect](#createindirect)|Crea un cuadro de diálogo no modal a partir de una plantilla de cuadro de diálogo en memoria (no basada en recursos).|
|[CDialog::DoModal](#domodal)|Llama a un cuadro de diálogo modal y vuelve cuando se termina.|
|[CDialog::EndDialog](#enddialog)|Cierra un cuadro de diálogo modal.|
|[CDialog::GetDefID](#getdefid)|Obtiene el identificador del control de pulsador predeterminado de un cuadro de diálogo.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Mueve el foco a un control de cuadro de diálogo especificado en el cuadro de diálogo.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Crea un cuadro de diálogo modal a partir de una plantilla de cuadro de diálogo en memoria (no basada en recursos). Los parámetros se almacenan hasta que `DoModal` se llama a la función.|
|[CDialog::MapDialogRect](#mapdialogrect)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Mueve el foco al siguiente control de cuadro de diálogo del cuadro de diálogo.|
|[CDialog::OnInitDialog](#oninitdialog)|Invalide para aumentar la inicialización del cuadro de diálogo.|
|[CDialog::OnSetFont](#onsetfont)|Invalide para especificar la fuente que va a utilizar un control de cuadro de diálogo cuando dibuja texto.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Mueve el foco al control de cuadro de diálogo anterior en el cuadro de diálogo.|
|[CDialog::SetDefID](#setdefid)|Cambia el control de pulsador predeterminado de un cuadro de diálogo a un pulsador especificado.|
|[CDialog::SetHelpID](#sethelpid)|Establece un identificador de ayuda contextual para el cuadro de diálogo.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Invalide para realizar la acción de presionar el botón Cancelar o la tecla ESC. El valor predeterminado cierra el cuadro de diálogo `DoModal` y devuelve IDCANCEL.|
|[CDialog::OnOK](#onok)|Invalide para realizar la acción de botón Aceptar en un cuadro de diálogo modal. El valor predeterminado cierra el cuadro de diálogo `DoModal` y devuelve IDOK.|

## <a name="remarks"></a>Comentarios

Los cuadros de diálogo son de dos tipos: modal y no modal. El usuario debe cerrar un cuadro de diálogo modal antes de que continúe la aplicación. Un cuadro de diálogo no modal permite al usuario mostrar el cuadro de diálogo y volver a otra tarea sin cancelar ni quitar el cuadro de diálogo.

Un `CDialog` objeto es una combinación de una plantilla de cuadro de `CDialog`diálogo y una clase derivada de. Utilice el editor de cuadros de diálogo para crear la plantilla de cuadro de diálogo y almacenarla en un recurso y, a continuación, use el `CDialog`Asistente para agregar clases para crear una clase derivada de.

Un cuadro de diálogo, como cualquier otra ventana, recibe mensajes de Windows. En un cuadro de diálogo, está especialmente interesado en controlar los mensajes de notificación desde los controles del cuadro de diálogo, ya que así es cómo interactúa el usuario con el cuadro de diálogo. Use el [Asistente para clases](mfc-class-wizard.md) para seleccionar qué mensajes desea controlar y agregar las entradas adecuadas del mapa de mensajes y las funciones miembro del controlador de mensajes a la clase. Solo necesita escribir código específico de la aplicación en las funciones miembro de controlador.

Si lo prefiere, siempre puede escribir manualmente las entradas de mapa de mensajes y las funciones miembro.

En todo menos el cuadro de diálogo más trivial, se agregan variables de miembro a la clase de cuadro de diálogo derivada para almacenar los datos especificados por el usuario en los controles del cuadro de diálogo o para mostrar los datos del usuario. Puede usar el Asistente para agregar variables para crear variables de miembro y asociarlas a controles. Al mismo tiempo, se elige un tipo de variable y un intervalo permitido de valores para cada variable. El Asistente para código agrega las variables miembro a la clase de cuadro de diálogo derivada.

Se genera un mapa de datos para controlar automáticamente el intercambio de datos entre las variables miembro y los controles del cuadro de diálogo. El mapa de datos proporciona funciones que inicializan los controles en el cuadro de diálogo con los valores correctos, recuperan los datos y validan los datos.

Para crear un cuadro de diálogo modal, construya un objeto en la pila utilizando el constructor para la clase de cuadro de diálogo `DoModal` derivada y, a continuación, llame a para crear la ventana de cuadro de diálogo y sus controles. Si desea crear un cuadro de diálogo no modal, llame `Create` a en el constructor de la clase de cuadro de diálogo.

También puede crear una plantilla en memoria mediante una estructura de datos [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) , como se describe en el Windows SDK. Después de construir un `CDialog` objeto, llame a [CreateIndirect](#createindirect) para crear un cuadro de diálogo no modal, o llame a [InitModalIndirect](#initmodalindirect) y [DoModal](#domodal) para crear un cuadro de diálogo modal.

La asignación de datos de Exchange y de validación se escribe en `CWnd::DoDataExchange` una invalidación de que se agrega a la nueva clase de cuadro de diálogo. Vea la función miembro [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) en `CWnd` para obtener más información sobre la funcionalidad de Exchange y de validación.

Tanto el programador como el marco llaman `DoDataExchange` indirectamente a través de una llamada a [CWnd:: UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

El marco de `UpdateData` trabajo llama a cuando el usuario hace clic en el botón Aceptar para cerrar un cuadro de diálogo modal. (Los datos no se recuperan si se hace clic en el botón Cancelar). La implementación predeterminada de [OnInitDialog](#oninitdialog) también llama `UpdateData` a para establecer los valores iniciales de los controles. Normalmente se invalida `OnInitDialog` para inicializar más controles. `OnInitDialog`se llama después de que se creen todos los controles de cuadro de diálogo y justo antes de que se muestre el cuadro de diálogo.

Puede llamar `CWnd::UpdateData` a en cualquier momento durante la ejecución de un cuadro de diálogo modal o no modal.

Si desarrolla un cuadro de diálogo manualmente, agregue las variables miembro necesarias a la clase de cuadro de diálogo derivada y agregue funciones miembro para establecer u obtener estos valores.

Un cuadro de diálogo modal se cierra automáticamente cuando el usuario presiona los botones aceptar o cancelar o cuando el código llama `EndDialog` a la función miembro.

Cuando implemente un cuadro de diálogo no modal, invalide siempre la `OnCancel` función miembro y llame a `DestroyWindow` desde dentro de ella. No llame a la clase `CDialog::OnCancel`base, porque llama `EndDialog`a, que hará que el cuadro de diálogo sea invisible pero no lo destruirá. También se debe invalidar `PostNcDestroy` para los cuadros de diálogo no modales con **el**fin de eliminarlo, ya que los cuadros de diálogo no modales normalmente se asignan con un **nuevo**. Los cuadros de diálogo modales se construyen normalmente en el marco `PostNcDestroy` y no necesitan limpieza.

Para obtener más información `CDialog`sobre, vea [cuadros de diálogo](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cdialog"></a>  CDialog::CDialog

Para construir un cuadro de diálogo modal basado en recursos, llame a una forma pública del constructor.

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*nIDTemplate*<br/>
Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (del tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Comentarios

Una forma del constructor proporciona acceso al recurso de cuadro de diálogo por nombre de plantilla. El otro constructor proporciona acceso mediante el número de ID. de plantilla, normalmente con un prefijo **IDD_** (por ejemplo, IDD_DIALOG1).

Para construir un cuadro de diálogo modal a partir de una plantilla en memoria, primero invoque el constructor sin parámetros y `InitModalIndirect`protegido y, a continuación, llame a.

Después de crear un cuadro de diálogo modal con uno de los métodos anteriores, `DoModal`llame a.

Para construir un cuadro de diálogo no modal, utilice el formulario protegido del `CDialog` constructor. El constructor está protegido porque debe derivar su propia clase de cuadro de diálogo para implementar un cuadro de diálogo no modal. La construcción de un cuadro de diálogo no modal es un proceso de dos pasos. Llame primero al constructor; a continuación, `Create` llame a la función miembro para crear un cuadro de diálogo basado en `CreateIndirect` recursos o llame a para crear el cuadro de diálogo a partir de una plantilla en memoria.

##  <a name="create"></a>  CDialog::Create

Llame `Create` a para crear un cuadro de diálogo no modal usando una plantilla de cuadro de diálogo de un recurso.

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana primario (del tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*nIDTemplate*<br/>
Contiene el número de identificación de un recurso de plantilla de cuadro de diálogo.

### <a name="return-value"></a>Valor devuelto

Ambos formularios devuelven un valor distinto de cero si la creación y la inicialización del cuadro de diálogo se realizaron correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Puede colocar la llamada en `Create` dentro del constructor o llamarla después de invocar el constructor.

Se proporcionan dos formas `Create` de la función miembro para el acceso al recurso de plantilla de cuadro de diálogo mediante el nombre de plantilla o el número de ID. de plantilla (por ejemplo, IDD_DIALOG1).

En cualquiera de los dos formularios, pase un puntero al objeto de ventana principal. Si *pParentWnd* es null, el cuadro de diálogo se creará con su ventana primaria o propietaria establecida en la ventana principal de la aplicación.

La `Create` función miembro se devuelve inmediatamente después de crear el cuadro de diálogo.

Use el estilo WS_VISIBLE en la plantilla de cuadro de diálogo si el cuadro de diálogo debe aparecer cuando se crea la ventana primaria. De lo contrario, debe `ShowWindow`llamar a. Para obtener más estilos de cuadro de diálogo y su aplicación, consulte la estructura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) en el Windows SDK y los [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) en la *referencia de MFC*.

Utilice la `CWnd::DestroyWindow` función para destruir un cuadro de diálogo creado por `Create` la función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>  CDialog::CreateIndirect

Llame a esta función miembro para crear un cuadro de diálogo no modal a partir de una plantilla de cuadro de diálogo en memoria.

```
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*lpDialogTemplate*<br/>
Apunta a la memoria que contiene una plantilla de cuadro de diálogo utilizada para crear el cuadro de diálogo. Esta plantilla está en forma de una estructura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) y la información de control, como se describe en el Windows SDK.

*pParentWnd*<br/>
Apunta al objeto de ventana primario del objeto de cuadro de diálogo (de tipo [CWnd](../../mfc/reference/cwnd-class.md)). Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*lpDialogInit*<br/>
Apunta a un recurso DLGINIT.

*hDialogTemplate*<br/>
Contiene un identificador para la memoria global que contiene una plantilla de cuadro de diálogo. Esta plantilla está en forma de una `DLGTEMPLATE` estructura y datos para cada control del cuadro de diálogo.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el cuadro de diálogo se creó y se inicializó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La `CreateIndirect` función miembro se devuelve inmediatamente después de crear el cuadro de diálogo.

Use el estilo WS_VISIBLE en la plantilla de cuadro de diálogo si el cuadro de diálogo debe aparecer cuando se crea la ventana primaria. De lo contrario, debe `ShowWindow` llamar a para que aparezca. Para obtener más información sobre cómo puede especificar otros estilos de cuadro de diálogo en la plantilla, consulte la estructura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) en el Windows SDK.

Utilice la `CWnd::DestroyWindow` función para destruir un cuadro de diálogo creado por `CreateIndirect` la función.

Los cuadros de diálogo que contienen controles ActiveX requieren información adicional que se proporciona en un recurso DLGINIT.

##  <a name="domodal"></a>  CDialog::DoModal

Llame a esta función miembro para invocar el cuadro de diálogo modal y devolver el resultado del cuadro de diálogo cuando haya terminado.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Valor **int** que especifica el valor del parámetro *nresultado* que se pasó a la función miembro [CDialog:: EndDialog](#enddialog) , que se utiliza para cerrar el cuadro de diálogo. El valor devuelto es-1 si la función no pudo crear el cuadro de diálogo o IDABORT si se produjo algún otro error, en cuyo caso la ventana de salida contendrá información de error de [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Comentarios

Esta función miembro controla toda la interacción con el usuario mientras el cuadro de diálogo está activo. Esto es lo que hace que el cuadro de diálogo sea modal; es decir, el usuario no puede interactuar con otras ventanas hasta que se cierre el cuadro de diálogo.

Si el usuario hace clic en uno de los botones de acción del cuadro de diálogo, como aceptar o cancelar, se llama a una función miembro de controlador de mensajes, como [onok](#onok) o [OnCancel](#oncancel), para intentar cerrar el cuadro de diálogo. La función `OnOK` miembro predeterminada validará y actualizará los datos del cuadro de diálogo y cerrará el cuadro de diálogo con el resultado `OnCancel` IDOK, y la función miembro predeterminada cerrará el cuadro de diálogo con el resultado IDCANCEL sin validar ni actualizar el datos del cuadro de diálogo. Puede invalidar estas funciones del controlador de mensajes para modificar su comportamiento.

> [!NOTE]
> `PreTranslateMessage`ahora se llama a para el procesamiento de mensajes de cuadro de diálogo modal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>  CDialog::EndDialog

Llame a esta función miembro para terminar un cuadro de diálogo modal.

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parámetros

*nResult*<br/>
Contiene el valor que se va a devolver desde el cuadro de diálogo al autor `DoModal`de la llamada de.

### <a name="remarks"></a>Comentarios

Esta función miembro devuelve *nresultado* como el valor devuelto `DoModal`de. Debe utilizar la función `EndDialog` para completar el procesamiento cada vez que se cree un cuadro de diálogo modal.

Puede llamar `EndDialog` a en cualquier momento, incluso en [OnInitDialog](#oninitdialog), en cuyo caso debe cerrar el cuadro de diálogo antes de que se muestre o antes de que se establezca el foco de entrada.

`EndDialog`no cierra el cuadro de diálogo inmediatamente. En su lugar, establece una marca que indica al cuadro de diálogo que se cierre en cuanto se devuelva el controlador de mensajes actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>  CDialog::GetDefID

Llame a `GetDefID` la función miembro para obtener el identificador del control de pulsador predeterminado de un cuadro de diálogo.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de 32 bits ( `DWORD`). Si el Pushbutton predeterminado tiene un valor de identificador, la palabra de orden superior contiene DC_HASDEFID y la palabra de orden inferior contiene el valor de identificador. Si el Pushbutton predeterminado no tiene un valor de identificador, el valor devuelto es 0.

### <a name="remarks"></a>Comentarios

Normalmente es un botón Aceptar.

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

Mueve el foco al control especificado en el cuadro de diálogo.

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parámetros

*pWndCtrl*<br/>
Identifica la ventana (control) que va a recibir el foco.

### <a name="remarks"></a>Comentarios

Para obtener un puntero al control (ventana secundaria) que se va a pasar como *pWndCtrl*, `CWnd::GetDlgItem` llame a la función miembro, que devuelve un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

Llame a esta función miembro para inicializar un objeto de cuadro de diálogo modal usando una plantilla de cuadro de diálogo que se crea en la memoria.

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*lpDialogTemplate*<br/>
Apunta a la memoria que contiene una plantilla de cuadro de diálogo utilizada para crear el cuadro de diálogo. Esta plantilla está en forma de una estructura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) y la información de control, como se describe en el Windows SDK.

*hDialogTemplate*<br/>
Contiene un identificador para la memoria global que contiene una plantilla de cuadro de diálogo. Esta plantilla está en forma de una `DLGTEMPLATE` estructura y datos para cada control del cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (del tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*lpDialogInit*<br/>
Apunta a un recurso DLGINIT.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de cuadro de diálogo se creó y se inicializó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Para crear un cuadro de diálogo modal indirectamente, asigne primero un bloque de memoria global y rellénelo con la plantilla de cuadro de diálogo. A continuación, llame `CDialog` al constructor vacío para construir el objeto de cuadro de diálogo. A continuación, `InitModalIndirect` llame a para almacenar su identificador en la plantilla de cuadro de diálogo en memoria. El cuadro de diálogo de Windows se crea y se muestra más adelante, cuando se llama a la función miembro [DoModal](#domodal) .

Los cuadros de diálogo que contienen controles ActiveX requieren información adicional que se proporciona en un recurso DLGINIT.

##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect

Llame a para convertir las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene las coordenadas del cuadro de diálogo que se van a convertir.

### <a name="remarks"></a>Comentarios

Las unidades de cuadro de diálogo se indican en términos de la unidad base de cuadro de diálogo actual derivada del ancho y alto promedio de los caracteres de la fuente utilizada para el texto del cuadro de diálogo. Una unidad horizontal es una cuarta parte de la unidad de ancho base del cuadro de diálogo y una unidad vertical es una octava parte de la unidad de alto base del cuadro de diálogo.

La `GetDialogBaseUnits` función de Windows devuelve información de tamaño para la fuente del sistema, pero puede especificar una fuente diferente para cada cuadro de diálogo si usa el estilo DS_SETFONT en el archivo de definición de recursos. La `MapDialogRect` función de Windows usa la fuente adecuada para este cuadro de diálogo.

La `MapDialogRect` función miembro reemplaza las unidades de cuadro de diálogo de *lpRect* por unidades de pantalla (píxeles) para que el rectángulo pueda usarse para crear un cuadro de diálogo o para colocar un control dentro de un cuadro.

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

Mueve el foco al siguiente control en el cuadro de diálogo.

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Comentarios

Si el foco está en el último control del cuadro de diálogo, se mueve al primer control.

##  <a name="oncancel"></a>  CDialog::OnCancel

El marco de trabajo llama a este método cuando el usuario hace clic en **Cancelar** o presiona la tecla ESC en un cuadro de diálogo modal o no modal.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Comentarios

Invalide este método para realizar acciones (como restaurar los datos antiguos) cuando un usuario cierre el cuadro de diálogo haciendo clic en **Cancelar** o presionando la tecla ESC. De forma predeterminada, se cierra un cuadro de diálogo modal llamando a [EndDialog](#enddialog) y haciendo que [DOMODAL](#domodal) devuelva IDCANCEL.

Si implementa el botón **Cancelar** en un cuadro de diálogo no modal, debe invalidar el `OnCancel` método y llamar a [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) dentro de él. No llame al método de clase base, porque llama a `EndDialog`, que hará que el cuadro de diálogo sea invisible pero no lo destruya.

> [!NOTE]
>  No se puede invalidar este método cuando se `CFileDialog` usa un objeto en un programa compilado en Windows XP. Para obtener más información `CFileDialog`sobre, vea [CFileDialog (clase](../../mfc/reference/cfiledialog-class.md)).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>  CDialog::OnInitDialog

Se llama a este método en respuesta al `WM_INITDIALOG` mensaje.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

Especifica si la aplicación ha establecido el foco de entrada en uno de los controles del cuadro de diálogo. Si `OnInitDialog` devuelve un valor distinto de cero, Windows establece el foco de entrada en la ubicación predeterminada, el primer control en el cuadro de diálogo. La aplicación solo puede devolver 0 si ha establecido explícitamente el foco de entrada en uno de los controles del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Windows envía el `WM_INITDIALOG` mensaje al cuadro de diálogo durante las llamadas a [Create](#create), [CreateIndirect](#createindirect)o [DoModal](#domodal) , que se producen inmediatamente antes de que se muestre el cuadro de diálogo.

Invalide este método si desea realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. En la versión invalidada, llame primero a la `OnInitDialog` clase base pero omita su valor devuelto. Normalmente, se devolverá `TRUE` desde el método invalidado.

Windows llama a `OnInitDialog` la función mediante el procedimiento de cuadro de diálogo global estándar común a todos los cuadros de diálogo de biblioteca MFC. No llama a esta función a través del mapa de mensajes y, por tanto, no necesita una entrada de mapa de mensajes para este método.

> [!NOTE]
> No se puede invalidar este método cuando se `CFileDialog` usa un objeto en un programa compilado en Windows Vista o sistemas operativos posteriores. Para obtener más información acerca de `CFileDialog` los cambios en Windows Vista y versiones posteriores, vea [CFileDialog (clase](../../mfc/reference/cfiledialog-class.md)).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>CDialog:: OnOK

Se llama cuando el usuario hace clic en el botón **Aceptar** (el botón con un identificador de IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Comentarios

Invalide este método para realizar acciones cuando se active el botón **Aceptar** . Si el cuadro de diálogo incluye la validación automática de datos y Exchange, la implementación predeterminada de este método valida los datos del cuadro de diálogo y actualiza las variables adecuadas en la aplicación.

Si implementa el botón **Aceptar** en un cuadro de diálogo no modal, debe invalidar el `OnOK` método y llamar a [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) dentro de él. No llame al método de clase base, porque llama a [EndDialog](#enddialog) , lo que hace que el cuadro de diálogo sea invisible pero no lo destruye.

> [!NOTE]
>  No se puede invalidar este método cuando se `CFileDialog` usa un objeto en un programa compilado en Windows XP. Para obtener más información `CFileDialog`sobre, vea [CFileDialog (clase](../../mfc/reference/cfiledialog-class.md)).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>  CDialog::OnSetFont

Especifica la fuente que va a utilizar un control de cuadro de diálogo al dibujar texto.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
de Especifica un puntero a la fuente que se utilizará como fuente predeterminada para todos los controles de este cuadro de diálogo.

### <a name="remarks"></a>Comentarios

El cuadro de diálogo usará la fuente especificada como valor predeterminado para todos sus controles.

El editor de cuadros de diálogo normalmente establece la fuente del cuadro de diálogo como parte del recurso de plantilla de cuadro de diálogo.

> [!NOTE]
> No se puede invalidar este método cuando se `CFileDialog` usa un objeto en un programa compilado en Windows Vista o sistemas operativos posteriores. Para obtener más información acerca de `CFileDialog` los cambios en Windows Vista y versiones posteriores, vea [CFileDialog (clase](../../mfc/reference/cfiledialog-class.md)).

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

Establece el foco en el control anterior del cuadro de diálogo.

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Comentarios

Si el foco está en el primer control del cuadro de diálogo, se mueve al último control del cuadro.

##  <a name="setdefid"></a>  CDialog::SetDefID

Cambia el control de pulsador predeterminado de un cuadro de diálogo.

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Especifica el identificador del control de pulsador que se convertirá en el valor predeterminado.

##  <a name="sethelpid"></a>  CDialog::SetHelpID

Establece un identificador de ayuda contextual para el cuadro de diálogo.

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parámetros

*nIDR*<br/>
Especifica el identificador de la ayuda contextual.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
