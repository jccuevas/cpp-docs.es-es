---
title: Clase CDialog
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
ms.openlocfilehash: 36913cfdd8beda31136176c966890a90077c1b30
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753367"
---
# <a name="cdialog-class"></a>Clase CDialog

La clase base utilizada para mostrar cuadros de diálogo en la pantalla.

## <a name="syntax"></a>Sintaxis

```
class CDialog : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|Construye un objeto `CDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDialog::Crear](#create)|Inicializa el objeto `CDialog`. Crea un cuadro de diálogo no selector `CDialog` y lo asocia al objeto.|
|[CDialog::CreateIndirect](#createindirect)|Crea un cuadro de diálogo no liberador a partir de una plantilla de cuadro de diálogo en la memoria (no basada en recursos).|
|[CDialog::DoModal](#domodal)|Llama a un cuadro de diálogo modal y devuelve cuando se hace.|
|[CDialog::EndDialog](#enddialog)|Cierra un cuadro de diálogo modal.|
|[CDialog::GetDefID](#getdefid)|Obtiene el identificador del control de pulsador predeterminado para un cuadro de diálogo.|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Mueve el foco a un control de cuadro de diálogo especificado en el cuadro de diálogo.|
|[CDialog::InitModalIndirect](#initmodalindirect)|Crea un cuadro de diálogo modal a partir de una plantilla de cuadro de diálogo en la memoria (no basada en recursos). Los parámetros se `DoModal` almacenan hasta que se llama a la función.|
|[CDialog::MapDialogRect](#mapdialogrect)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Mueve el foco al siguiente control de cuadro de diálogo en el cuadro de diálogo.|
|[CDialog::OnInitDialog](#oninitdialog)|Reemplazar para aumentar la inicialización del cuadro de diálogo.|
|[CDialog::OnSetFont](#onsetfont)|Reemplazar para especificar la fuente que un control de cuadro de diálogo debe utilizar cuando dibuja texto.|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Mueve el foco al control de cuadro de diálogo anterior en el cuadro de diálogo.|
|[CDialog::SetDefID](#setdefid)|Cambia el control de pulsador predeterminado de un cuadro de diálogo a un pulsador especificado.|
|[CDialog::SetHelpID](#sethelpid)|Establece un identificador de ayuda contextual para el cuadro de diálogo.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|Reemplazar para realizar el botón Cancelar o la acción de clave ESC. El valor predeterminado cierra `DoModal` el cuadro de diálogo y devuelve IDCANCEL.|
|[CDialog::OnOK](#onok)|Reemplazar para realizar la acción del botón Aceptar en un cuadro de diálogo modal. El valor predeterminado cierra `DoModal` el cuadro de diálogo y devuelve IDOK.|

## <a name="remarks"></a>Observaciones

Los cuadros de diálogo son de dos tipos: modal y no modal. El usuario debe cerrar un cuadro de diálogo modal antes de que la aplicación continúe. Un cuadro de diálogo no iniciado permite al usuario mostrar el cuadro de diálogo y volver a otra tarea sin cancelar o quitar el cuadro de diálogo.

Un `CDialog` objeto es una combinación `CDialog`de una plantilla de cuadro de diálogo y una clase derivada. Utilice el editor de cuadros de diálogo para crear la plantilla de cuadro de `CDialog`diálogo y almacenarla en un recurso y, a continuación, utilice el asistente Agregar clase para crear una clase derivada de .

Un cuadro de diálogo, como cualquier otra ventana, recibe mensajes de Windows. En un cuadro de diálogo, está particularmente interesado en controlar los mensajes de notificación de los controles del cuadro de diálogo, ya que es así como el usuario interactúa con el cuadro de diálogo. Utilice el [Asistente para clases](mfc-class-wizard.md) para seleccionar los mensajes que desea controlar y agregará las entradas de mapa de mensajes adecuadas y las funciones miembro del controlador de mensajes a la clase. Solo necesita escribir código específico de la aplicación en las funciones miembro del controlador.

Si lo prefiere, siempre puede escribir entradas de mapa de mensajes y funciones miembro manualmente.

En todos los cuadros de diálogo, excepto el más trivial, se agregan variables miembro a la clase de cuadro de diálogo derivada para almacenar los datos introducidos en los controles del cuadro de diálogo por el usuario o para mostrar datos para el usuario. Puede usar el asistente Agregar variable para crear variables miembro y asociarlas a controles. Al mismo tiempo, elige un tipo de variable y un rango de valores permisible para cada variable. El asistente de código agrega las variables miembro a la clase de cuadro de diálogo derivada.

Se genera un mapa de datos para controlar automáticamente el intercambio de datos entre las variables miembro y los controles del cuadro de diálogo. El mapa de datos proporciona funciones que inicializan los controles en el cuadro de diálogo con los valores adecuados, recuperan los datos y validan los datos.

Para crear un cuadro de diálogo modal, construya un objeto en la `DoModal` pila utilizando el constructor de la clase de cuadro de diálogo derivada y, a continuación, llame para crear la ventana de diálogo y sus controles. Si desea crear un cuadro de `Create` diálogo no deseado, llame al constructor de la clase de cuadro de diálogo.

También puede crear una plantilla en memoria mediante una estructura de datos [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) como se describe en el Windows SDK. Después de `CDialog` construir un objeto, llame a [CreateIndirect](#createindirect) para crear un cuadro de diálogo no modal o llame a [InitModalIndirect](#initmodalindirect) y [DoModal](#domodal) para crear un cuadro de diálogo modal.

El mapa de datos de intercambio `CWnd::DoDataExchange` y validación se escribe en una invalidación de que se agrega a la nueva clase de cuadro de diálogo. Consulte el [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) `CWnd` función miembro para obtener más información sobre la funcionalidad de intercambio y validación.

Tanto el programador como `DoDataExchange` el marco de trabajo llaman indirectamente a través de una llamada a [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).

El marco `UpdateData` de trabajo llama cuando el usuario hace clic en el Aceptar botón para cerrar un cuadro de diálogo modal. (Los datos no se recuperan si se hace clic en el botón Cancelar.) La implementación predeterminada de [OnInitDialog](#oninitdialog) también llama `UpdateData` para establecer los valores iniciales de los controles. Normalmente se `OnInitDialog` reemplaza para inicializar más controles. `OnInitDialog`se llama después de crear todos los controles de cuadro de diálogo y justo antes de que se muestre el cuadro de diálogo.

Puede llamar `CWnd::UpdateData` en cualquier momento durante la ejecución de un cuadro de diálogo modal o no modal.

Si desarrolla un cuadro de diálogo a mano, agregue las variables miembro necesarias a la clase de cuadro de diálogo derivada usted mismo y agregue funciones miembro para establecer u obtener estos valores.

Un cuadro de diálogo modal se cierra automáticamente cuando el usuario presiona `EndDialog` los botones Aceptar o Cancelar o cuando el código llama a la función miembro.

Al implementar un cuadro de diálogo no `OnCancel` aplicado, `DestroyWindow` invalide siempre la función miembro y llame desde dentro de ella. No llame a la `CDialog::OnCancel`clase base `EndDialog`, porque llama a , lo que hará que el cuadro de diálogo invisible, pero no lo destruirá. También debe `PostNcDestroy` anular los cuadros de diálogo no iniciados para eliminar **esto,** ya que los cuadros de diálogo no iniciados se suelen asignar con **nuevos**. Los cuadros de diálogo modales suelen construirse en el marco y no necesitan `PostNcDestroy` limpieza.

Para obtener `CDialog`más información sobre , vea [Cuadros de diálogo](../../mfc/dialog-boxes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cdialogcdialog"></a><a name="cdialog"></a>CDialog::CDialog

Para construir un cuadro de diálogo modal basado en recursos, llame a cualquier forma pública del constructor.

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
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

### <a name="remarks"></a>Observaciones

Una forma del constructor proporciona acceso al recurso de cuadro de diálogo por nombre de plantilla. El otro constructor proporciona acceso por número de identificador de plantilla, normalmente con un prefijo **IDD_** (por ejemplo, IDD_DIALOG1).

Para construir un cuadro de diálogo modal a partir de una plantilla `InitModalIndirect`en memoria, primero invoque el constructor protegido sin parámetros y, a continuación, llame a .

Después de construir un cuadro de diálogo `DoModal`modal con uno de los métodos anteriores, llame a .

Para construir un cuadro de diálogo no posicionado, utilice la forma protegida del `CDialog` constructor. El constructor está protegido porque debe derivar su propia clase de cuadro de diálogo para implementar un cuadro de diálogo no basado en la no modelo. La construcción de un cuadro de diálogo no basado en un paso es un proceso de dos pasos. Primero llame al constructor; a continuación, llame a la `Create` función miembro `CreateIndirect` para crear un cuadro de diálogo basado en recursos o llame para crear el cuadro de diálogo a partir de una plantilla en memoria.

## <a name="cdialogcreate"></a><a name="create"></a>CDialog::Crear

Llame `Create` para crear un cuadro de diálogo no liberador mediante una plantilla de cuadro de diálogo de un recurso.

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
Apunta al objeto de ventana principal (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*nIDTemplate*<br/>
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

### <a name="return-value"></a>Valor devuelto

Ambos formularios devuelven distinto de cero si la creación y la inicialización del cuadro de diálogo se tuvieron correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Puede colocar la `Create` llamada dentro del constructor o llamarla después de invocar el constructor.

Se proporcionan `Create` dos formas de la función miembro para el acceso al recurso de plantilla de cuadro de diálogo por nombre de plantilla o número de identificador de plantilla (por ejemplo, IDD_DIALOG1).

Para cualquier formulario, pase un puntero al objeto de ventana principal. Si *pParentWnd* es NULL, el cuadro de diálogo se creará con su ventana primaria o propietaria establecida en la ventana principal de la aplicación.

La `Create` función miembro devuelve inmediatamente después de crear el cuadro de diálogo.

Utilice el estilo WS_VISIBLE en la plantilla de cuadro de diálogo si el cuadro de diálogo debe aparecer cuando se crea la ventana primaria. De lo contrario, debe llamar a `ShowWindow`. Para obtener más estilos de cuadro de diálogo y su aplicación, vea la estructura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) en el Windows SDK y [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana en la *referencia de MFC*.

Utilice `CWnd::DestroyWindow` la función para destruir `Create` un cuadro de diálogo creado por la función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

## <a name="cdialogcreateindirect"></a><a name="createindirect"></a>CDialog::CreateIndirect

Llame a esta función miembro para crear un cuadro de diálogo no basado en una plantilla de cuadro de diálogo en la memoria.

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
Apunta a la memoria que contiene una plantilla de cuadro de diálogo utilizada para crear el cuadro de diálogo. Esta plantilla tiene la forma de una estructura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) e información de control, como se describe en el Windows SDK.

*pParentWnd*<br/>
Apunta al objeto de ventana principal del objeto de cuadro de diálogo (de tipo [CWnd](../../mfc/reference/cwnd-class.md)). Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*lpDialogInit*<br/>
Apunta a un recurso DLGINIT.

*hDialogTemplate*<br/>
Contiene un identificador de memoria global que contiene una plantilla de cuadro de diálogo. Esta plantilla tiene la `DLGTEMPLATE` forma de una estructura y datos para cada control en el cuadro de diálogo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cuadro de diálogo se creó e inicializó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La `CreateIndirect` función miembro devuelve inmediatamente después de crear el cuadro de diálogo.

Utilice el estilo WS_VISIBLE en la plantilla de cuadro de diálogo si el cuadro de diálogo debe aparecer cuando se crea la ventana primaria. De lo contrario, debe llamar `ShowWindow` para que aparezca. Para obtener más información sobre cómo puede especificar otros estilos de cuadro de diálogo en la plantilla, vea el [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) estructura en el Windows SDK.

Utilice `CWnd::DestroyWindow` la función para destruir `CreateIndirect` un cuadro de diálogo creado por la función.

Los cuadros de diálogo que contienen controles ActiveX requieren información adicional proporcionada en un recurso DLGINIT.

## <a name="cdialogdomodal"></a><a name="domodal"></a>CDialog::DoModal

Llame a esta función miembro para invocar el cuadro de diálogo modal y devolver el resultado del cuadro de diálogo cuando haya terminado.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Un **int** valor que especifica el valor de la *nResult* parámetro que se pasó a la [CDialog::EndDialog](#enddialog) función miembro, que se utiliza para cerrar el cuadro de diálogo. El valor devuelto es -1 si la función no pudo crear el cuadro de diálogo, o IDABORT si se produjo algún otro error, en cuyo caso la ventana de salida contendrá información de error de [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Observaciones

Esta función miembro controla toda la interacción con el usuario mientras el cuadro de diálogo está activo. Esto es lo que hace que el cuadro de diálogo sea modal; es decir, el usuario no puede interactuar con otras ventanas hasta que se cierra el cuadro de diálogo.

Si el usuario hace clic en uno de los pulsadores del cuadro de diálogo, como Aceptar o Cancelar, se llama a una función miembro del controlador de mensajes, como [OnOK](#onok) o [OnCancel](#oncancel), para intentar cerrar el cuadro de diálogo. La `OnOK` función miembro predeterminada validará y actualizará los datos del cuadro de `OnCancel` diálogo y cerrará el cuadro de diálogo con el resultado IDOK, y la función miembro predeterminada cerrará el cuadro de diálogo con el resultado IDCANCEL sin validar ni actualizar los datos del cuadro de diálogo. Puede invalidar estas funciones de controlador de mensajes para modificar su comportamiento.

> [!NOTE]
> `PreTranslateMessage`ahora se llama para el procesamiento de mensajes de cuadro de diálogo modal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

## <a name="cdialogenddialog"></a><a name="enddialog"></a>CDialog::EndDialog

Llame a esta función miembro para terminar un cuadro de diálogo modal.

```cpp
void EndDialog(int nResult);
```

### <a name="parameters"></a>Parámetros

*nResultado*<br/>
Contiene el valor que se va a `DoModal`devolver desde el cuadro de diálogo al autor de la llamada de .

### <a name="remarks"></a>Observaciones

Esta función miembro devuelve *nResult* como el valor devuelto de `DoModal`. Debe utilizar `EndDialog` la función para completar el procesamiento siempre que se cree un cuadro de diálogo modal.

Puede llamar `EndDialog` en cualquier momento, incluso en [OnInitDialog](#oninitdialog), en cuyo caso debe cerrar el cuadro de diálogo antes de que se muestre o antes de establecer el foco de entrada.

`EndDialog`no cierra el cuadro de diálogo inmediatamente. En su lugar, establece una marca que indica al cuadro de diálogo que se cierre tan pronto como se devuelva el controlador de mensajes actual.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

## <a name="cdialoggetdefid"></a><a name="getdefid"></a>CDialog::GetDefID

Llame `GetDefID` a la función miembro para obtener el identificador del control de pulsador predeterminado para un cuadro de diálogo.

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de 32 bits ( `DWORD`). Si el pulsador predeterminado tiene un valor de ID, la palabra de orden superior contiene DC_HASDEFID y la palabra de orden bajo contiene el valor ID. Si el pulsador predeterminado no tiene un valor id, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

Esto suele ser un botón OK.

## <a name="cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl

Mueve el foco al control especificado en el cuadro de diálogo.

```cpp
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>Parámetros

*pWndCtrl*<br/>
Identifica la ventana (control) que va a recibir el foco.

### <a name="remarks"></a>Observaciones

Para obtener un puntero al control (ventana secundaria) para pasar `CWnd::GetDlgItem` como *pWndCtrl*, llame a la función miembro, que devuelve un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).

## <a name="cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog::InitModalIndirect

Llame a esta función miembro para inicializar un objeto de cuadro de diálogo modal mediante una plantilla de cuadro de diálogo que se construye en memoria.

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
Apunta a la memoria que contiene una plantilla de cuadro de diálogo utilizada para crear el cuadro de diálogo. Esta plantilla tiene la forma de una estructura [DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate) e información de control, como se describe en el Windows SDK.

*hDialogTemplate*<br/>
Contiene un identificador de memoria global que contiene una plantilla de cuadro de diálogo. Esta plantilla tiene la `DLGTEMPLATE` forma de una estructura y datos para cada control en el cuadro de diálogo.

*pParentWnd*<br/>
Apunta al objeto de ventana primario o propietario (de tipo [CWnd](../../mfc/reference/cwnd-class.md)) al que pertenece el objeto de cuadro de diálogo. Si es NULL, la ventana primaria del objeto de cuadro de diálogo se establece en la ventana principal de la aplicación.

*lpDialogInit*<br/>
Apunta a un recurso DLGINIT.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de cuadro de diálogo se creó e inicializó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para crear un cuadro de diálogo modal indirectamente, primero asigne un bloque global de memoria y rellénelo con la plantilla de cuadro de diálogo. A continuación, `CDialog` llame al constructor vacío para construir el objeto de cuadro de diálogo. A continuación, llame `InitModalIndirect` para almacenar el identificador en la plantilla de cuadro de diálogo en memoria. El cuadro de diálogo de Windows se crea y se muestra más adelante, cuando el [DoModal](#domodal) se llama a la función miembro.

Los cuadros de diálogo que contienen controles ActiveX requieren información adicional proporcionada en un recurso DLGINIT.

## <a name="cdialogmapdialogrect"></a><a name="mapdialogrect"></a>CDialog::MapDialogRect

Llame para convertir las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.

```cpp
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene las coordenadas del cuadro de diálogo que se van a convertir.

### <a name="remarks"></a>Observaciones

Las unidades de cuadro de diálogo se indican en términos de la unidad base del cuadro de diálogo actual derivada de la anchura y la altura medias de los caracteres de la fuente utilizada para el texto del cuadro de diálogo. Una unidad horizontal es una cuarta parte de la unidad de ancho base del cuadro de diálogo y una unidad vertical es una octava parte de la unidad de altura base del cuadro de diálogo.

La `GetDialogBaseUnits` función de Windows devuelve información de tamaño para la fuente del sistema, pero puede especificar una fuente diferente para cada cuadro de diálogo si utiliza el estilo de DS_SETFONT en el archivo de definición de recursos. La `MapDialogRect` función Windows utiliza la fuente adecuada para este cuadro de diálogo.

La `MapDialogRect` función miembro reemplaza las unidades de cuadro de diálogo en *lpRect* con unidades de pantalla (píxeles) para que el rectángulo se puede utilizar para crear un cuadro de diálogo o colocar un control dentro de un cuadro.

## <a name="cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog::NextDlgCtrl

Mueve el foco al siguiente control del cuadro de diálogo.

```cpp
void NextDlgCtrl() const;
```

### <a name="remarks"></a>Observaciones

Si el foco está en el último control del cuadro de diálogo, se mueve al primer control.

## <a name="cdialogoncancel"></a><a name="oncancel"></a>CDialog::OnCancel

El marco de trabajo llama a este método cuando el usuario hace clic en **Cancelar** o presiona la tecla ESC en un cuadro de diálogo modal o no modal.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Observaciones

Invalide este método para realizar acciones (como restaurar datos antiguos) cuando un usuario cierra el cuadro de diálogo haciendo clic en **Cancelar** o pulsando la tecla ESC. El valor predeterminado cierra un cuadro de diálogo modal llamando a [EndDialog](#enddialog) y haciendo que [DoModal](#domodal) devuelva IDCANCEL.

Si implementa el botón **Cancelar** en un cuadro de `OnCancel` diálogo no aplicado, debe invalidar el método y llamar a [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) dentro de él. No llame al método de clase `EndDialog`base, porque llama a , lo que hará que el cuadro de diálogo sea invisible, pero no lo destruirá.

> [!NOTE]
> No se puede invalidar este `CFileDialog` método cuando se utiliza un objeto en un programa compilado en Windows XP. Para obtener `CFileDialog`más información sobre , vea [CFileDialog (Clase)](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

## <a name="cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog::OnInitDialog

Se llama a este `WM_INITDIALOG` método en respuesta al mensaje.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

Especifica si la aplicación ha establecido el foco de entrada en uno de los controles del cuadro de diálogo. Si `OnInitDialog` devuelve distinto de cero, Windows establece el foco de entrada en la ubicación predeterminada, el primer control del cuadro de diálogo. La aplicación solo puede devolver 0 si ha establecido explícitamente el foco de entrada en uno de los controles del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Windows envía `WM_INITDIALOG` el mensaje al cuadro de diálogo durante las llamadas [Create](#create), [CreateIndirect](#createindirect)o [DoModal,](#domodal) que se producen inmediatamente antes de que se muestre el cuadro de diálogo.

Invalide este método si desea realizar un procesamiento especial cuando se inicializa el cuadro de diálogo. En la versión reemplazada, primero `OnInitDialog` llame a la clase base, pero ignore su valor devuelto. Normalmente volverá `TRUE` desde el método invalidado.

Windows llama `OnInitDialog` a la función mediante el procedimiento de cuadro de diálogo global estándar común a todos los cuadros de diálogo Biblioteca de clases de Microsoft Foundation. No llama a esta función a través del mapa de mensajes y, por lo tanto, no necesita una entrada de mapa de mensajes para este método.

> [!NOTE]
> No se puede invalidar este `CFileDialog` método cuando se utiliza un objeto en un programa que se compila en Windows Vista o sistemas operativos posteriores. Para obtener más `CFileDialog` información acerca de los cambios en Windows Vista y versiones posteriores, vea [CFileDialog (Clase)](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

## <a name="cdialogonok"></a><a name="onok"></a>CDialog::OnOK

Se llama cuando el usuario hace clic en el botón **Aceptar** (el botón con un identificador de IDOK).

```
virtual void OnOK();
```

### <a name="remarks"></a>Observaciones

Invalide este método para realizar acciones cuando se activa el botón **Aceptar.** Si el cuadro de diálogo incluye la validación automática de datos y el intercambio, la implementación predeterminada de este método valida los datos del cuadro de diálogo y actualiza las variables adecuadas en la aplicación.

Si implementa el **botón Aceptar** en un cuadro de `OnOK` diálogo no correcto, debe invalidar el método y llamar a [DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) dentro de él. No llame al método de clase base, porque llama a [EndDialog](#enddialog) que hace que el cuadro de diálogo invisible pero no lo destruye.

> [!NOTE]
> No se puede invalidar este `CFileDialog` método cuando se utiliza un objeto en un programa compilado en Windows XP. Para obtener `CFileDialog`más información sobre , vea [CFileDialog (Clase)](../../mfc/reference/cfiledialog-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

## <a name="cdialogonsetfont"></a><a name="onsetfont"></a>CDialog::OnSetFont

Especifica la fuente que utilizará un control de cuadro de diálogo al dibujar texto.

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
[en] Especifica un puntero a la fuente que se usará como fuente predeterminada para todos los controles de este cuadro de diálogo.

### <a name="remarks"></a>Observaciones

El cuadro de diálogo utilizará la fuente especificada como valor predeterminado para todos sus controles.

Normalmente, el editor de cuadros de diálogo establece la fuente del cuadro de diálogo como parte del recurso de plantilla de cuadro de diálogo.

> [!NOTE]
> No se puede invalidar este `CFileDialog` método cuando se utiliza un objeto en un programa que se compila en Windows Vista o sistemas operativos posteriores. Para obtener más `CFileDialog` información acerca de los cambios en Windows Vista y versiones posteriores, vea [CFileDialog (Clase)](../../mfc/reference/cfiledialog-class.md).

## <a name="cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl

Establece el foco en el control anterior en el cuadro de diálogo.

```cpp
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>Observaciones

Si el foco está en el primer control del cuadro de diálogo, se mueve al último control del cuadro.

## <a name="cdialogsetdefid"></a><a name="setdefid"></a>CDialog::SetDefID

Cambia el control de pulsador predeterminado para un cuadro de diálogo.

```cpp
void SetDefID(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Especifica el identificador del control pulsador que se convertirá en el valor predeterminado.

## <a name="cdialogsethelpid"></a><a name="sethelpid"></a>CDialog::SetHelpID

Establece un identificador de ayuda contextual para el cuadro de diálogo.

```cpp
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>Parámetros

*nIDR*<br/>
Especifica el identificador de ayuda contextual.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
