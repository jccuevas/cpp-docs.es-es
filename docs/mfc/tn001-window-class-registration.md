---
title: 'TN001: Registro de la clase de ventana'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: 4ae94d1c9c57f6c315ae482e44576ae25194c00f
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894268"
---
# <a name="tn001-window-class-registration"></a>TN001: Registro de la clase de ventana

Esta nota describe las rutinas MFC que registrar especial [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa)es necesarias para Microsoft Windows. Específica `WNDCLASS` se describen los atributos utilizados por MFC y Windows.

## <a name="the-problem"></a>El problema

Los atributos de un [CWnd](../mfc/reference/cwnd-class.md) objeto, como un `HWND` administrar en Windows, se almacenan en dos lugares: el objeto de ventana y el `WNDCLASS`. El nombre de la `WNDCLASS` se pasa a las funciones de creación de ventana general como [CWnd:: Create](../mfc/reference/cwnd-class.md#create) y [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) en el *lpszClassName* parámetro.

Esto `WNDCLASS` debe estar registrado a través de uno de cuatro formas:

- Implícitamente mediante el uso de un MFC proporcionado `WNDCLASS`.

- Implícitamente mediante la creación de subclases de un control de Windows (o algún otro control).

- Explícitamente mediante una llamada a la MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) o [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass).

- Explícitamente mediante una llamada a la rutina de Windows [RegisterClass](/windows/desktop/api/winuser/nf-winuser-registerclassa).

## <a name="wndclass-fields"></a>Campos WNDCLASS

El `WNDCLASS` estructura consta de varios campos que describen una clase de ventana. En la tabla siguiente se muestra los campos y especifica cómo se usa en una aplicación MFC:

|Campo|Descripción|
|-----------|-----------------|
|*lpfnWndProc*|proc. de ventana, debe ser un `AfxWndProc`|
|*cbClsExtra*|no se usa (debe ser cero)|
|*cbWndExtra*|no se usa (debe ser cero)|
|*hInstance*|rellena automáticamente con [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|
|*hIcon*|icono de ventanas de marco, consulte a continuación|
|*hCursor*|cursor para cuando el mouse está sobre la ventana, consulte a continuación|
|*hbrBackground*|color de fondo, vea a continuación|
|*lpszMenuName*|no se usa (debe ser NULL)|
|*lpszClassName*|nombre de clase, vea a continuación|

## <a name="provided-wndclasses"></a>Proporciona WNDCLASSes

Las versiones anteriores de MFC (antes de MFC 4.0) proporciona varias clases de ventana predefinidas. Estas clases de ventana ya no se proporcionan de forma predeterminada. Las aplicaciones deben usar `AfxRegisterWndClass` con los parámetros adecuados.

Si la aplicación proporciona un recurso con el identificador de recurso especificado (por ejemplo, AFX_IDI_STD_FRAME), MFC usa ese recurso. En caso contrario, usará el recurso predeterminado. Para el icono, se utiliza el icono de aplicación estándar y para el cursor, se usa el cursor de flecha estándar.

Dos iconos de admiten aplicaciones MDI con tipos de documento único: un icono para la aplicación principal, el icono de documento/MDIChild icónico windows. Para varios tipos de documentos con iconos diferentes, debe registrar adicionales `WNDCLASS`í o use el [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) función.

`CFrameWnd::LoadFrame` se registrará un `WNDCLASS` con el Id. de icono que especifique como el primer parámetro y los atributos estándar siguientes:

- estilo de clase: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- icon AFX_IDI_STD_FRAME

- cursor de flecha

- Color de fondo COLOR_WINDOW

Los valores de color de fondo y de cursor para el [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) no se usan desde el área cliente de la `CMDIFrameWnd` está cubierta completamente por el **MDICLIENT** ventana. Microsoft no recomienda la creación de subclases del **MDICLIENT** ventana así que use los colores estándar y los tipos de cursor cuando sea posible.

## <a name="subclassing-and-superclassing-controls"></a>Creación de subclases y crear superclases controles

Si deriva una subclase o superclase un Windows control (por ejemplo, [CButton](../mfc/reference/cbutton-class.md)), a continuación, la clase obtiene automáticamente la `WNDCLASS` atributos que se proporcionan en la implementación de Windows de ese control.

## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass (función)

MFC proporciona una función auxiliar para registrar una clase de ventana. Dado un conjunto de atributos (estilo de clase de ventana, cursor, pincel de fondo e icono), se genera un nombre sintético y la clase de ventana resultante está registrada. Por ejemplo,

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

Esta función devuelve una cadena del nombre de clase de ventana registrada generado temporal. Para obtener más información acerca de esta función, vea [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass).

La cadena devuelta es un puntero a un búfer de cadena estática temporal. Es válido hasta la siguiente llamada a `AfxRegisterWndClass`. Si desea mantener esta cadena alrededor, almacénelo en un [CString](../atl-mfc-shared/using-cstring.md) variable, como en este ejemplo:

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` se producirá un [CResourceException](../mfc/reference/cresourceexception-class.md) si la clase de ventana no se pudo registrar (debido a los parámetros incorrectos, o fuera de memoria de Windows).

## <a name="the-registerclass-and-afxregisterclass-functions"></a>Las funciones de AfxRegisterClass y RegisterClass

Si desea hacer algo más sofisticada de lo que `AfxRegisterWndClass` proporciona, se puede llamar a la API de Windows `RegisterClass` o la función MFC `AfxRegisterClass`. El `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) y [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` funciones toman una *lpszClassName* nombre de la cadena de la clase de ventana como primer parámetro. Puede utilizar cualquier nombre de clase de ventana registrada, independientemente del método usado para registrarla.

Es importante usar `AfxRegisterClass` (o `AfxRegisterWndClass`) en un archivo DLL de Win32. Win32 no automáticamente anular el registro de clases registradas por un archivo DLL, por lo que explícitamente debe anular el registro clases cuando se finaliza el archivo DLL. Mediante el uso de `AfxRegisterClass` en lugar de `RegisterClass` se controla automáticamente para usted. `AfxRegisterClass` mantiene una lista de las clases únicas registrados por el archivo DLL y automáticamente anulará ellos cuando finaliza el archivo DLL. Cuando usas `RegisterClass` en un archivo DLL, debe asegurarse de que todas las clases se eliminan del registradas cuando se finaliza el archivo DLL (en su [DllMain](/windows/desktop/Dlls/dllmain) función). Si no lo hace puede provocar `RegisterClass` fallará inesperadamente cuando otra aplicación cliente intenta usar el archivo DLL.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

