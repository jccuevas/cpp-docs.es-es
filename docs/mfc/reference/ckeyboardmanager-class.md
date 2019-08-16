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
ms.openlocfilehash: e4f8f678e76113b5d012242f474ff0ab8b0628dd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505781"
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
|NOMBRE|DESCRIPCIÓN|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|Construye un objeto `CKeyboardManager`.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|NOMBRE|DESCRIPCIÓN|
|[CKeyboardManager::CleanUp](#cleanup)|Borra las tablas de teclas de método abreviado.|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|Recupera la tecla de método abreviado predeterminada para el comando y la ventana especificados.|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|Determina si la tabla de aceleradores controla una clave.|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|Indica si un carácter se imprime.|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|Indica si los menús muestran todas las teclas de método abreviado para un comando o solo la tecla de método abreviado predeterminada.|
|[CKeyboardManager::LoadState](#loadstate)|Carga las tablas de teclas de método abreviado desde el registro de Windows.|
|[CKeyboardManager::ResetAll](#resetall)|Vuelve a cargar las tablas de teclas de método abreviado desde el recurso de aplicación.|
|[CKeyboardManager::SaveState](#savestate)|Guarda las tablas de teclas de método abreviado en el registro de Windows.|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|Especifica si el marco de trabajo muestra todas las teclas de método abreviado para todos los comandos o una sola tecla de método abreviado para cada comando. Este método no afecta a los comandos que tienen solo una tecla de método abreviado asociada.|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|Convierte un carácter en su registro superior.|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|Actualiza una tabla de teclas de método abreviado con una nueva tabla de teclas de método abreviado.|

## <a name="remarks"></a>Comentarios

Los miembros de esta clase permiten guardar y cargar tablas de teclas de método abreviado en el registro de Windows, usar una plantilla para actualizar las tablas de clave de corte corto y buscar la tecla de método abreviado predeterminada para un comando en una ventana de marco. Además, el `CKeyboardManager` objeto le permite controlar cómo se muestran las teclas de método abreviado al usuario.

No debe crear un `CKeyboardManager` objeto manualmente. El marco de la aplicación lo creará automáticamente. Sin embargo, debe llamar a [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) durante el proceso de inicialización de la aplicación. Para obtener un puntero al administrador de teclado para la aplicación, llame a [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo recuperar un puntero a `CKeyboardManager` un objeto de `CWinAppEx` una clase y cómo mostrar todas las teclas de método abreviado asociadas a comandos de menú. Este fragmento de código forma parte del [ejemplo de páginas personalizadas](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxkeyboardmanager. h

##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager

Construye un objeto `CKeyboardManager`.

```
CKeyboardManager();
```

### <a name="remarks"></a>Comentarios

En la mayoría de los casos, no es necesario crear `CKeyboardManager` un directamente. De forma predeterminada, el marco de trabajo crea uno automáticamente. Para obtener un puntero a `CKeyboardManager`, llame a [CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager). Si crea uno manualmente, debe inicializarlo con el método [CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager).

##  <a name="cleanup"></a>  CKeyboardManager::CleanUp

Libera los recursos y borra todas las asignaciones de teclas de método abreviado. `CKeyboardManager`

```
static void CleanUp();
```

### <a name="remarks"></a>Comentarios

Para obtener más información sobre las teclas de método abreviado, vea [Personalización del teclado y del mouse](../../mfc/keyboard-and-mouse-customization.md).

No es necesario llamar a esta función cuando la aplicación se cierra porque el marco de trabajo la llama automáticamente durante la salida de la aplicación.

##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator

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
de IDENTIFICADOR del comando.

*str*<br/>
enuncia Referencia a un `CString` objeto.

*pWndFrame*<br/>
de Puntero a una ventana de marco.

*bIsDefaultFrame*<br/>
de Especifica si la ventana de marco es la ventana de marco predeterminada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el acceso directo; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método busca el comando especificado por *uiCmd* y recupera la tecla de método abreviado predeterminada. A continuación, el método toma la cadena asociada a esta tecla de método abreviado y escribe el valor en el parámetro *Str* .

##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled

Determina si la [clase CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)controla la clave especificada.

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
|Parámetro|DESCRIPCIÓN|
|*nKey*|de Clave que se va a comprobar.|
|*fVirt*|de Especifica el comportamiento de la tecla de método abreviado. Para obtener una lista de los valores posibles, consulte la [estructura de aceleración](/windows/win32/api/winuser/ns-winuser-accel).|
|*pWndFrame*|de Ventana de marco. Este método determina si una tecla de método abreviado se controla en este marco.|
|*bIsDefaultFrame*|de Un parámetro booleano que indica si *pWndFrame* es la ventana de marco predeterminada.|

### <a name="return-value"></a>Valor devuelto

TRUE si se controla la tecla de método abreviado. FALSE si la clave no está controlada o si *pWndFrame* es NULL.

### <a name="remarks"></a>Comentarios

Los parámetros de entrada deben coincidir con la entrada de la tabla de aceleradores para *nKey* y *fVirt* para determinar si una tecla de método abreviado se controla en *pWndFrame*.

##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable

Indica si un carácter se imprime.

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|DESCRIPCIÓN|
|*nChar*|de Carácter que este método comprueba.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el carácter se imprime, cero si no lo es.

### <a name="remarks"></a>Comentarios

Este método produce un error si se produce un error en una llamada a [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) .

##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators

Indica si los menús muestran todas las teclas de método abreviado asociadas a comandos de menú o solo las teclas de método abreviado predeterminadas.

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la aplicación muestra todas las teclas de método abreviado para los comandos de menú; 0 si la aplicación solo muestra las teclas de método abreviado predeterminadas.

### <a name="remarks"></a>Comentarios

La aplicación muestra las teclas de método abreviado para los comandos de menú en la barra de menús. Use la función [CKeyboardManager:: ShowAllAccelerators](#showallaccelerators) para controlar si la aplicación muestra todas las teclas de método abreviado o solo las teclas de método abreviado predeterminadas.

##  <a name="loadstate"></a>  CKeyboardManager::LoadState

Carga las tablas de teclas de método abreviado desde el registro de Windows.

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de La ruta de acceso `CKeyboardManager` del registro donde se guardan los datos.

*pDefaultFrame*<br/>
de Puntero a una ventana de marco que se va a usar como ventana predeterminada.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el estado se cargó correctamente o 0 de lo contrario.

### <a name="remarks"></a>Comentarios

Si el parámetro *lpszProfileName* es null, este método comprueba la ubicación del registro predeterminada `CKeyboardManager` para los datos. La ubicación del registro predeterminada se especifica mediante la [clase CWinAppEx](../../mfc/reference/cwinappex-class.md). Los datos se deben escribir previamente con el método [CKeyboardManager::](#savestate)SaveState.

Si no especifica una ventana predeterminada, se utilizará la ventana de marco principal de la aplicación.

##  <a name="resetall"></a>  CKeyboardManager::ResetAll

Vuelve a cargar las tablas de teclas de método abreviado desde el recurso de aplicación.

```
void ResetAll();
```

### <a name="remarks"></a>Comentarios

Esta función borra los accesos directos almacenados en la `CKeyboardManager` instancia de. A continuación, volverá a cargar el estado del administrador de teclado desde el recurso de la aplicación.

##  <a name="savestate"></a>  CKeyboardManager::SaveState

Guarda las tablas de teclas de método abreviado en el registro de Windows.

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de La ruta de acceso del registro `CKeyboardManager` para guardar el estado.

*pDefaultFrame*<br/>
de Puntero a una ventana de marco que se convierte en la ventana predeterminada.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el estado del administrador de teclado se guardó correctamente o 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Si el parámetro *lpszProfileName* es null, este método escribirá el `CKeyboardManager` estado en la ubicación predeterminada especificada por la [clase CWinAppEx](../../mfc/reference/cwinappex-class.md). Si especifica una ubicación, puede cargar los datos más adelante con el método [CKeyboardManager:: Loadstate](#loadstate).

Si no especifica una ventana predeterminada, la ventana de marco principal se usará como ventana predeterminada.

##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators

Muestra todas las teclas de método abreviado asociadas a comandos de menú.

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>Parámetros

*bShowAll*<br/>
de Si es TRUE, se mostrarán todas las teclas de método abreviado. Si es FALSE, solo se mostrará la primera tecla de método abreviado.

*lpszDelimiter*<br/>
de Cadena que se va a insertar entre las teclas de método abreviado. Este delimitador no tiene ningún efecto si solo se muestra una tecla de método abreviado.

### <a name="remarks"></a>Comentarios

De forma predeterminada, si un comando tiene más de una tecla de método abreviado asociada, solo se mostrará la primera tecla de método abreviado. Esta función permite enumerar todas las teclas de método abreviado asociadas a todos los comandos.

Las teclas de método abreviado se mostrarán junto al comando en la barra de menús. Si se muestran todas las teclas de método abreviado, la cadena proporcionada por *lpszDelimiter* separará las teclas de método abreviado individuales.

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

Convierte un carácter en su registro superior.

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>Parámetros

*nChar*<br/>
de Carácter que se va a convertir.

### <a name="return-value"></a>Valor devuelto

Carácter que es el registro superior del parámetro de entrada.

##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable

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
de Un puntero a una plantilla de documento.

*lpAccel*<br/>
de Puntero a la nueva tecla de método abreviado.

*nSize*<br/>
de Tamaño de la nueva tabla de acceso directo.

*pDefaultFrame*<br/>
de Puntero a la ventana de marco predeterminada.

*hAccelNew*<br/>
de Identificador de la nueva tabla de acceso directo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Utilice esta función para reemplazar la tabla de acceso directo existente por las nuevas teclas de método abreviado para varios objetos de ventana de marco. La función recibe una plantilla de documento como parámetro para obtener acceso a todos los objetos de la ventana de marco conectados a la plantilla de documento especificada.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx (clase)](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[Personalización del teclado y del mouse](../../mfc/keyboard-and-mouse-customization.md)
