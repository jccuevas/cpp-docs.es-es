---
title: CKeyboardManager (clase)
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: 85bda6747c4ef6bed87b7a2ef30a3ef06bdfe29e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517863"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager (clase)

Administra las tablas de teclas de método abreviado de la ventana de marco principal y las ventanas de marco secundarias.

## <a name="syntax"></a>Sintaxis

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Construye un objeto `CKeyboardManager`.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|[CKeyboardManager::CleanUp](#cleanup)|Borra las tablas de clave de acceso directo.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Recupera la tecla de método abreviado predeterminado para el comando especificado y la ventana.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Determina si una clave se controla mediante la tabla de aceleradores.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Indica si un carácter imprimible.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Indica si los menús Mostrar todas las teclas de método abreviado de un comando o sólo la tecla de método abreviado de forma predeterminada.|
|[CKeyboardManager::LoadState](#loadstate)|Carga las tablas de clave de acceso directo desde el registro de Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Vuelve a cargar las tablas de clave de acceso directo desde el recurso de aplicación.|
|[CKeyboardManager::SaveState](#savestate)|Guarda el acceso directo de las tablas de clave en el registro de Windows.|
|[Showallaccelerators](#showallaccelerators)|Especifica si el marco de trabajo muestra todas las teclas de método abreviado para todos los comandos o una clave de acceso directo único para cada comando. Este método no afecta a los comandos que tienen solo una tecla de método abreviado.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Convierte un carácter en su registro superior.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Actualiza una tabla de clave de acceso directo con una nueva tabla de clave de acceso directo.|

## <a name="remarks"></a>Comentarios

Los miembros de esta clase le permiten guardar y cargar las tablas de clave de acceso directo en el registro de Windows, use una plantilla para actualizar las tablas de clave de acceso directo y encontrar la tecla de método abreviado predeterminado para un comando en una ventana de marco. Además, el `CKeyboardManager` objeto le permite controlar cómo se muestran las teclas de método abreviado para el usuario.

No debería crear un `CKeyboardManager` objeto manualmente. Se creará automáticamente el marco de trabajo de la aplicación. Sin embargo, debe llamar a [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) durante el proceso de inicialización de la aplicación. Para obtener un puntero al administrador de teclado para la aplicación, llame a [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo recuperar un puntero a un `CKeyboardManager` objeto desde un `CWinAppEx` clase y cómo mostrar todas las teclas de método abreviado asociadas con los comandos de menú. Este fragmento de código forma parte de la [ejemplo Custom Pages](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxkeyboardmanager.h

##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager

Construye un objeto `CKeyboardManager`.

```
CKeyboardManager();
```

### <a name="remarks"></a>Comentarios

En la mayoría de los casos, no es necesario crear un `CKeyboardManager` directamente. De forma predeterminada, el marco de trabajo crea uno automáticamente. Para obtener un puntero a la `CKeyboardManager`, llame a [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Si crea uno manualmente, debe inicializar con el método [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

##  <a name="cleanup"></a>  CKeyboardManager::CleanUp

Libera el `CKeyboardManager` recursos y borra todas las asignaciones de clave de acceso directo.

```
static void CleanUp();
```

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de teclas de método abreviado, vea [personalización del teclado y Mouse](../../mfc/keyboard-and-mouse-customization.md).

No es necesario llamar a esta función cuando se cierra la aplicación porque el marco de trabajo lo llama automáticamente durante la salida de la aplicación.

##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator

Recupera la tecla de método abreviado predeterminado para el comando especificado y la ventana.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] El identificador de comando.

*str*<br/>
[out] Una referencia a un `CString` objeto.

*pWndFrame*<br/>
[in] Un puntero a una ventana de marco.

*bIsDefaultFrame*<br/>
[in] Especifica si la ventana de marco es la ventana de marco de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el método abreviado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método busca el comando especificado por *uiCmd* y recupera la tecla de método abreviado de forma predeterminada. A continuación, el método toma la cadena asociada a esta tecla de método abreviado y escribe el valor para el *str* parámetro.

##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled

Determina si la clave especificada está controlada por la [CKeyboardManager (clase)](../../mfc/reference/ckeyboardmanager-class.md).

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*nKey*|[in] Para comprobar la clave.|
|*fVirt*|[in] Especifica el comportamiento de la tecla de método abreviado. Para obtener una lista de valores posibles, vea [aceleración estructura](/windows/desktop/api/winuser/ns-winuser-tagaccel).|
|*pWndFrame*|[in] Una ventana de marco. Este método determina si una tecla de método abreviado se trata en este marco.|
|*bIsDefaultFrame*|[in] Un parámetro booleano que indica si *pWndFrame* es la ventana de marco de forma predeterminada.|

### <a name="return-value"></a>Valor devuelto

TRUE si se controla la tecla de método abreviado. FALSE si no se controla la clave o si *pWndFrame* es NULL.

### <a name="remarks"></a>Comentarios

Los parámetros de entrada deben coincidir con la entrada en la tabla de aceleradores tanto para *nKey* y *fVirt* para determinar si una tecla de método abreviado se controla en *pWndFrame*.

##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable

Indica si un carácter imprimible.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*NChar*|[in] El carácter que este método comprueba.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el carácter es imprimible, cero si no lo está.

### <a name="remarks"></a>Comentarios

Este método produce un error si una llamada a [GetKeyboardState](https://msdn.microsoft.com/library/windows/desktop/ms646299) se produce un error.

##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators

Indica si los menús Mostrar todas las teclas de método abreviado asociadas con los comandos de menú o sólo las teclas de método abreviado de forma predeterminada.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la aplicación enumera todas las teclas de método abreviado para comandos de menú; Si la aplicación muestra solo teclas de método abreviado predeterminado es 0.

### <a name="remarks"></a>Comentarios

La aplicación enumera los métodos abreviados para comandos de menú en la barra de menús. Use la función [Showallaccelerators](#showallaccelerators) para controlar si la aplicación enumera todas las teclas de método abreviado o solo las teclas de método abreviado de forma predeterminada.

##  <a name="loadstate"></a>  CKeyboardManager::LoadState

Carga las tablas de clave de acceso directo desde el registro de Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[in] La ruta de acceso del registro donde `CKeyboardManager` se guardan los datos.

*pDefaultFrame*<br/>
[in] Un puntero a una ventana de marco que se usará como la ventana de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el estado se carga correctamente o 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Si el *lpszProfileName* parámetro es NULL, este método comprueba la ubicación del registro de forma predeterminada para `CKeyboardManager` datos. La ubicación del registro predeterminado especificada por el [CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md). Los datos deben escribirse previamente con el método [CKeyboardManager::SaveState](#savestate).

Si no especifica una ventana de forma predeterminada, se usará la ventana de marco principal de la aplicación.

##  <a name="resetall"></a>  CKeyboardManager::ResetAll

Vuelve a cargar las tablas de clave de acceso directo desde el recurso de aplicación.

```
void ResetAll();
```

### <a name="remarks"></a>Comentarios

Esta función borra los métodos abreviados que se almacenan en el `CKeyboardManager` instancia. A continuación, volverá a cargar el estado del Administrador de teclado desde el recurso de aplicación.

##  <a name="savestate"></a>  CKeyboardManager::SaveState

Guarda el acceso directo de las tablas de clave en el registro de Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[in] La ruta de acceso del registro para guardar la `CKeyboardManager` estado.

*pDefaultFrame*<br/>
[in] Un puntero a una ventana de marco que se convierte en la ventana de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el estado del Administrador de teclado se ha guardado correctamente, o 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Si el *lpszProfileName* parámetro es NULL, este método se escribirá el `CKeyboardManager` estado en la ubicación predeterminada especificada por el [CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md). Si especifica una ubicación, puede cargar los datos más adelante mediante el método [CKeyboardManager::LoadState](#loadstate).

Si no especifica una ventana de forma predeterminada, se usará la ventana de marco principal como la ventana de forma predeterminada.

##  <a name="showallaccelerators"></a>  Showallaccelerators

Muestra todas las teclas de método abreviado asociadas con los comandos de menú.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parámetros

*bShowAll*<br/>
[in] Si es TRUE, se mostrará todas las teclas de método abreviado. Si es FALSE, se mostrará la primera tecla de método abreviado.

*lpszDelimiter*<br/>
[in] Una cadena que se va a insertar entre las teclas de método abreviado. Este delimitador no tiene ningún efecto si solo se muestra una tecla de método abreviado.

### <a name="remarks"></a>Comentarios

De forma predeterminada, si un comando tiene más de una tecla de método abreviado asociada con él, se mostrará la primera tecla de método abreviado. Esta función permite obtener una lista de todas las teclas de método abreviado asociadas con todos los comandos.

Las teclas de método abreviado, se mostrará junto al comando en la barra de menús. Si se muestran todas las claves de acceso directo, la cadena proporcionada por *lpszDelimiter* teclas de método abreviado individuales para separar.

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

Convierte un carácter en su registro superior.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parámetros

*NChar*<br/>
[in] El carácter que se va a convertir.

### <a name="return-value"></a>Valor devuelto

El carácter que es la parte superior del registro del parámetro de entrada.

##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable

Actualiza una tabla de clave de acceso directo con una nueva tabla de clave de acceso directo.

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parámetros

*pTemplate*<br/>
[in] Un puntero a una plantilla de documento.

*lpAccel*<br/>
[in] Un puntero a la nueva clave de acceso directo.

*nSize*<br/>
[in] El tamaño de la nueva tabla de acceso directo.

*pDefaultFrame*<br/>
[in] Un puntero a la ventana de marco de forma predeterminada.

*hAccelNew*<br/>
[in] Identificador de la nueva tabla de acceso directo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Utilice esta función para reemplazar la tabla de acceso directo existente con nuevas teclas de método abreviado para varios objetos de ventana de marco. La función recibe una plantilla de documento como un parámetro para obtener acceso a todos los objetos de ventana de marco conectado a la plantilla de documento determinada.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Personalización del teclado y del mouse](../../mfc/keyboard-and-mouse-customization.md)

