---
title: Clase CKeyboardManager
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
ms.openlocfilehash: a8053ab33a2b49eb2c447cdaa1cb2b9e356bc696
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754929"
---
# <a name="ckeyboardmanager-class"></a>Clase CKeyboardManager

Administra las tablas de teclas de método abreviado de la ventana de marco principal y las ventanas de marco secundarias.

## <a name="syntax"></a>Sintaxis

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Construye un objeto `CKeyboardManager`.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CKeyboardManager::CleanUp](#cleanup)|Borra las tablas de teclas de método abreviado.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Recupera la tecla de método abreviado predeterminada para el comando y la ventana especificados.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Determina si la tabla de aceleradores controla una clave.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Indica si un carácter se puede imprimir.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Indica si los menús muestran todas las teclas de método abreviado de un comando o solo la tecla de método abreviado predeterminada.|
|[CKeyboardManager::LoadState](#loadstate)|Carga las tablas de teclas de método abreviado desde el registro de Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Vuelve a cargar las tablas de teclas de método abreviado desde el recurso de aplicación.|
|[CKeyboardManager::SaveState](#savestate)|Guarda las tablas de teclas de método abreviado en el registro de Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Especifica si el marco de trabajo muestra todas las teclas de método abreviado para todos los comandos o una sola tecla de método abreviado para cada comando. Este método no afecta a los comandos que solo tienen una tecla de método abreviado asociada.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Convierte un carácter en su registro superior.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Actualiza una tabla de teclas de método abreviado con una nueva tabla de teclas de método abreviado.|

## <a name="remarks"></a>Observaciones

Los miembros de esta clase le permiten guardar y cargar tablas de teclas de método abreviado en el registro de Windows, usar una plantilla para actualizar las tablas de teclas de acceso directo y buscar la tecla de método abreviado predeterminada para un comando en una ventana de marco. Además, `CKeyboardManager` el objeto permite controlar cómo se muestran las teclas de método abreviado al usuario.

No debe crear `CKeyboardManager` un objeto manualmente. Se creará automáticamente por el marco de la aplicación. Sin embargo, debe llamar a [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) durante el proceso de inicialización de la aplicación. Para obtener un puntero al administrador de teclado de la aplicación, llame a [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CKeyboardManager` cómo recuperar `CWinAppEx` un puntero a un objeto de una clase y cómo mostrar todas las teclas de método abreviado asociadas con comandos de menú. Este fragmento de código forma parte del [ejemplo Páginas personalizadas.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxkeyboardmanager.h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager

Construye un objeto `CKeyboardManager`.

```
CKeyboardManager();
```

### <a name="remarks"></a>Observaciones

En la mayoría de los casos, no es necesario crear un `CKeyboardManager` directamente. De forma predeterminada, el marco de trabajo crea uno para usted. Para obtener un `CKeyboardManager`puntero a la , llame a [CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Si crea uno manualmente, debe inicializarlo con el método [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a>CKeyboardManager::CleanUp

Libera los `CKeyboardManager` recursos y borra todas las asignaciones de teclas de método abreviado.

```
static void CleanUp();
```

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de las teclas de método abreviado, consulte [Personalización de teclado y ratón](../../mfc/keyboard-and-mouse-customization.md).

No es necesario llamar a esta función cuando se cierra la aplicación porque el marco de trabajo la llama automáticamente durante la salida de la aplicación.

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator

Recupera la tecla de método abreviado predeterminada para el comando y la ventana especificados.

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El id de comando.

*Str*<br/>
[fuera] Una referencia `CString` a un objeto.

*pWndFrame*<br/>
[en] Un puntero a una ventana de marco.

*bIsDefaultFrame*<br/>
[en] Especifica si la ventana de marco es la ventana de marco predeterminada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el acceso directo; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método busca el comando especificado por *uiCmd* y recupera la tecla de método abreviado predeterminada. A continuación, el método toma la cadena asociada a esta tecla de método abreviado y escribe el valor en el *str* parámetro.

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>CKeyboardManager::IsKeyHandled

Determina si la tecla especificada se controla mediante la [clase CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

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
|*nKey*|[en] La llave para comprobar.|
|*fVirt*|[en] Especifica el comportamiento de la tecla de método abreviado. Para obtener una lista de valores posibles, véase [Estructura ACCEL](/windows/win32/api/winuser/ns-winuser-accel).|
|*pWndFrame*|[en] Una ventana de marco. Este método determina si se controla una tecla de método abreviado en este marco.|
|*bIsDefaultFrame*|[en] Un parámetro booleano que indica si *pWndFrame* es la ventana de marco predeterminada.|

### <a name="return-value"></a>Valor devuelto

TRUESi se controla la tecla de método abreviado. FALSE si la clave no se controla o si *pWndFrame* es NULL.

### <a name="remarks"></a>Observaciones

Los parámetros de entrada deben coincidir con la entrada de la tabla de aceleradores tanto para *nKey* como *para fVirt* para determinar si una tecla de método abreviado se controla en *pWndFrame*.

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable

Indica si un carácter se puede imprimir.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*Nchar*|[en] El carácter que comprueba este método.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el carácter es imprimible, cero si no lo es.

### <a name="remarks"></a>Observaciones

Se produce un error en este método si se produce un error en una llamada a [GetKeyboardState.](/windows/win32/api/winuser/nf-winuser-getkeyboardstate)

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>CKeyboardManager::IsShowAllAccelerators

Indica si los menús muestran todas las teclas de método abreviado asociadas con los comandos de menú o solo las teclas de método abreviado predeterminadas.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la aplicación enumera todas las teclas de método abreviado para los comandos de menú; 0 si la aplicación solo muestra las teclas de método abreviado predeterminadas.

### <a name="remarks"></a>Observaciones

La aplicación enumera las teclas de método abreviado para los comandos de menú en la barra de menús. Utilice la función [CKeyboardManager::ShowAllAccelerators](#showallaccelerators) para controlar si la aplicación enumera todas las teclas de método abreviado o solo las teclas de método abreviado predeterminadas.

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a>CKeyboardManager::LoadState

Carga las tablas de teclas de método abreviado desde el registro de Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] La ruta `CKeyboardManager` de acceso del Registro donde se guardan los datos.

*pDefaultFrame*<br/>
[en] Puntero a una ventana de marco para utilizarlo como ventana predeterminada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el estado se cargó correctamente o 0 en caso contrario.

### <a name="remarks"></a>Observaciones

Si el parámetro *lpszProfileName* es NULL, este método `CKeyboardManager` comprueba la ubicación predeterminada del Registro en busca de datos. La ubicación predeterminada del Registro se especifica mediante la [clase CWinAppEx](../../mfc/reference/cwinappex-class.md). Los datos deben escribirse previamente con el método [CKeyboardManager::SaveState](#savestate).

Si no especifica una ventana predeterminada, se utilizará la ventana de marco principal de la aplicación.

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a>CKeyboardManager::ResetAll

Vuelve a cargar las tablas de teclas de método abreviado desde el recurso de aplicación.

```cpp
void ResetAll();
```

### <a name="remarks"></a>Observaciones

Esta función borra los accesos directos almacenados en la `CKeyboardManager` instancia. A continuación, volverá a cargar el estado del administrador de teclado desde el recurso de aplicación.

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a>CKeyboardManager::SaveState

Guarda las tablas de teclas de método abreviado en el registro de Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
[en] La ruta de `CKeyboardManager` acceso del Registro para guardar el estado.

*pDefaultFrame*<br/>
[en] Puntero a una ventana de marco que se convierte en la ventana predeterminada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el estado del administrador de teclado se guardó correctamente, o 0 en caso contrario.

### <a name="remarks"></a>Observaciones

Si el parámetro *lpszProfileName* es NULL, `CKeyboardManager` este método escribirá el estado en la ubicación predeterminada especificada por la [clase CWinAppEx](../../mfc/reference/cwinappex-class.md). Si especifica una ubicación, puede cargar los datos más adelante mediante el método [CKeyboardManager::LoadState](#loadstate).

Si no especifica una ventana predeterminada, la ventana de marco principal se utilizará como la ventana predeterminada.

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>CKeyboardManager::ShowAllAccelerators

Muestra todas las teclas de método abreviado asociadas a los comandos de menú.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parámetros

*bShowAll*<br/>
[en] Si es TRUE, se mostrarán todas las teclas de método abreviado. Si FALSE, solo se mostrará la primera tecla de método abreviado.

*lpszDelimiter*<br/>
[en] Cadena para insertar entre teclas de método abreviado. Este delimitador no tiene ningún efecto si solo se muestra una tecla de método abreviado.

### <a name="remarks"></a>Observaciones

De forma predeterminada, si un comando tiene más de una tecla de método abreviado asociada, solo se mostrará la primera tecla de método abreviado. Esta función le permite enumerar todas las teclas de método abreviado asociadas con todos los comandos.

Las teclas de método abreviado se mostrarán junto al comando en la barra de menús. Si se muestran todas las teclas de método abreviado, la cadena proporcionada por *lpszDelimiter* separará las teclas de método abreviado individuales.

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>CKeyboardManager::TranslateCharToUpper

Convierte un carácter en su registro superior.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parámetros

*Nchar*<br/>
[en] El carácter que se convertirá.

### <a name="return-value"></a>Valor devuelto

Carácter que es el registro superior del parámetro de entrada.

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable

Actualiza una tabla de teclas de método abreviado con una nueva tabla de teclas de método abreviado.

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
[en] Un puntero a una plantilla de documento.

*lpAccel*<br/>
[en] Un puntero a la nueva tecla de método abreviado.

*nTamaño*<br/>
[en] El tamaño de la nueva tabla de accesos directos.

*pDefaultFrame*<br/>
[en] Un puntero a la ventana de marco predeterminada.

*hAccelNew*<br/>
[en] Identificador de la nueva tabla de accesos directos.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Utilice esta función para reemplazar la tabla de métodos abreviados existente con nuevas teclas de método abreviado para varios objetos de ventana de marco. La función recibe una plantilla de documento como parámetro para obtener acceso a todos los objetos de ventana de marco conectados a la plantilla de documento determinada.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Personalización de teclado y ratón](../../mfc/keyboard-and-mouse-customization.md)
