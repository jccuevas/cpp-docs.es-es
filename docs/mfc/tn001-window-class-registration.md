---
title: 'TN001: Registro de clase de ventana'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 95e35ddd6f55c955bc2adb7b4db2460ae84a6dc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513550"
---
# <a name="tn001-window-class-registration"></a>TN001: Registro de clase de ventana

En esta nota se describen las rutinas de MFC que registran la [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)especial que necesita Microsoft Windows. Se `WNDCLASS` describen los atributos específicos utilizados por MFC y Windows.

## <a name="the-problem"></a>El problema

Los atributos de un objeto [CWnd](../mfc/reference/cwnd-class.md) , como un `HWND` identificador de Windows, se almacenan en dos lugares: el objeto Window y `WNDCLASS`el. `WNDCLASS` El nombre de se pasa a las funciones de creación de ventanas generales como [CWnd:: Create](../mfc/reference/cwnd-class.md#create) y [CFrameWnd:: Create](../mfc/reference/cframewnd-class.md#create) en el parámetro *lpszClassName* .

`WNDCLASS` Debe registrarse a través de uno de los cuatro medios siguientes:

- Implícitamente mediante el uso de un `WNDCLASS`MFC proporcionado.

- Implícitamente mediante la subclase de un control de Windows (o algún otro control).

- Explícitamente mediante una llamada a [AfxRegisterWndClass (](../mfc/reference/application-information-and-management.md#afxregisterwndclass) o [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)de MFC.

- Explícitamente mediante una llamada a la rutina [RegisterClass](/windows/win32/api/winuser/nf-winuser-registerclassw)de Windows.

## <a name="wndclass-fields"></a>Campos de WNDCLASS

La `WNDCLASS` estructura consta de varios campos que describen una clase de ventana. En la tabla siguiente se muestran los campos y se especifica cómo se usan en una aplicación MFC:

|Campo|DESCRIPCIÓN|
|-----------|-----------------|
|*lpfnWndProc*|el procedimiento de ventana debe ser un`AfxWndProc`|
|*cbClsExtra*|no se usa (debe ser cero)|
|*cbWndExtra*|no se usa (debe ser cero)|
|*hInstance*|se rellena automáticamente con [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|icono para las ventanas de marco, vea a continuación|
|*hCursor*|cursor cuando el mouse está encima de la ventana, vea a continuación|
|*hbrBackground*|color de fondo, vea a continuación|
|*lpszMenuName*|no se usa (debe ser NULL)|
|*lpszClassName*|nombre de clase, vea a continuación|

## <a name="provided-wndclasses"></a>WNDCLASSes proporcionado

Las versiones anteriores de MFC (antes de MFC 4,0) ofrecían varias clases de ventana predefinidas. Estas clases de ventana ya no se proporcionan de forma predeterminada. Las aplicaciones deben `AfxRegisterWndClass` usar con los parámetros adecuados.

Si la aplicación proporciona un recurso con el identificador de recurso especificado (por ejemplo, AFX_IDI_STD_FRAME), MFC usará ese recurso. De lo contrario, utilizará el recurso predeterminado. En el icono, se usa el icono de la aplicación estándar y, para el cursor, se usa el cursor de flecha estándar.

Dos iconos admiten aplicaciones MDI con tipos de documento único: un icono para la aplicación principal, el otro icono para ventanas de documento o MDIChild de iconos. En el caso de varios tipos de documentos con iconos diferentes, `WNDCLASS`debe registrar es o usar la función [CFrameWnd:: LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) .

`CFrameWnd::LoadFrame`registrará un `WNDCLASS` con el identificador de icono que especifique como primer parámetro y los siguientes atributos estándar:

- estilo de clase: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- icono AFX_IDI_STD_FRAME

- cursor de flecha

- Color de fondo de COLOR_WINDOW

Los valores de color de fondo y cursor para [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) no se usan, ya que el área cliente `CMDIFrameWnd` de está totalmente incluida en la ventana **MdiClient** . Microsoft no fomenta la subclase de la ventana **MdiClient** , así que use los colores estándar y los tipos de cursor cuando sea posible.

## <a name="subclassing-and-superclassing-controls"></a>Subclases y controles de superclase

Si la subclase o la superclase es un control de Windows (por ejemplo, [CButton](../mfc/reference/cbutton-class.md)), la clase `WNDCLASS` obtiene automáticamente los atributos proporcionados en la implementación de Windows de ese control.

## <a name="the-afxregisterwndclass-function"></a>La función AfxRegisterWndClass (

MFC proporciona una función auxiliar para registrar una clase de ventana. Dado un conjunto de atributos (estilo de clase de ventana, cursor, pincel de fondo e icono), se genera un nombre sintético y se registra la clase de ventana resultante. Por ejemplo,

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Esta función devuelve una cadena temporal del nombre de clase de ventana registrada generado. Para obtener más información sobre esta función, vea [AfxRegisterWndClass (](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

La cadena devuelta es un puntero temporal a un búfer de cadena estático. Es válido hasta la siguiente llamada a `AfxRegisterWndClass`. Si desea conservar esta cadena, almacénela en una variable [CString](../atl-mfc-shared/using-cstring.md) , como en este ejemplo:

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass`producirá una [CResourceException](../mfc/reference/cresourceexception-class.md) si la clase de ventana no se pudo registrar (ya sea debido a parámetros incorrectos o fuera de la memoria de Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>Las funciones RegisterClass y AfxRegisterClass

Si desea hacer algo más sofisticado que lo que `AfxRegisterWndClass` proporciona, puede llamar a la API `RegisterClass` de Windows o a la `AfxRegisterClass`función de MFC. Las `CWnd`funciones, [CFrameWnd](../mfc/reference/cframewnd-class.md) y [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` toman un nombre de cadena *lpszClassName* para la clase Window como primer parámetro. Puede usar cualquier nombre de clase de ventana registrada, independientemente del método utilizado para registrarlo.

Es importante usar `AfxRegisterClass` (o `AfxRegisterWndClass`) en un archivo dll en Win32. Win32 no anula automáticamente el registro de las clases registradas por un archivo DLL, por lo que debe anular el registro de las clases explícitamente cuando se termina el archivo DLL. El uso `AfxRegisterClass` de en lugar `RegisterClass` de esto se controla automáticamente. `AfxRegisterClass`mantiene una lista de clases únicas registradas por el archivo DLL y anulará su registro automáticamente cuando finalice el archivo DLL. Cuando se usa `RegisterClass` en un archivo dll, debe asegurarse de que se anule el registro de todas las clases cuando se termine el archivo DLL (en la función [DllMain](/windows/win32/Dlls/dllmain) ). Si no lo hace, es `RegisterClass` posible que se produzca un error inesperado cuando otra aplicación cliente intente usar el archivo dll.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
