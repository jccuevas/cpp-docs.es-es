---
title: Clase CWndClassInfo
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 01706bf61c3b977c28998325ece68724cfbc7452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330338"
---
# <a name="cwndclassinfo-class"></a>Clase CWndClassInfo

Esta clase proporciona métodos para registrar información para una clase de ventana.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CWndClassInfo
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|[Registrar](#register)|Registra la clase de ventana.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_atom](#m_atom)|Identifica de forma única la clase de ventana registrada.|
|[m_bSystemCursor](#m_bsystemcursor)|Especifica si el recurso de cursor hace referencia a un cursor del sistema o a un cursor contenido en un recurso de módulo.|
|[m_lpszCursorID](#m_lpszcursorid)|Especifica el nombre del recurso de cursor.|
|[m_lpszOrigName](#m_lpszorigname)|Contiene el nombre de una clase de ventana existente.|
|[m_szAutoName](#m_szautoname)|Contiene un nombre generado por ATL de la clase de ventana.|
|[m_wc](#m_wc)|Mantiene la información de `WNDCLASSEX` clase de ventana en una estructura.|
|[pWndProc](#pwndproc)|Señala el procedimiento de ventana de una clase de ventana existente.|

## <a name="remarks"></a>Observaciones

`CWndClassInfo`administra la información de una clase de ventana. Normalmente se `CWndClassInfo` utiliza a través de una de las tres macros, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX o DECLARE_WND_SUPERCLASS, como se describe en la tabla siguiente:

|Macro|Descripción|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`registra información para una nueva clase de ventana.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`registra información para una nueva clase de ventana, incluidos los parámetros de clase.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`registra información para una clase de ventana que se basa en una clase existente pero utiliza un procedimiento de ventana diferente. Esta técnica se denomina superclase.|

De forma predeterminada, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) incluye la `DECLARE_WND_CLASS` macro para crear una ventana basada en una nueva clase de ventana. DECLARE_WND_CLASS proporciona estilos predeterminados y color de fondo para el control. Si desea especificar el estilo y el color `CWindowImpl` de fondo usted mismo, derive la clase e incluya la macro DECLARE_WND_CLASS_EX en la definición de clase.

Si desea crear una ventana basada en una clase `CWindowImpl` de ventana existente, derive la clase e incluya la macro DECLARE_WND_SUPERCLASS en la definición de clase. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Para obtener más información acerca de las clases de ventana, vea [Clases](/windows/win32/winmsg/window-classes) de ventana en el Windows SDK.

Para obtener más información sobre el uso de ventanas en ATL, vea el artículo Clases de [ventana ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a>CWndClassInfo::m_atom

Contiene el identificador único para la clase de ventana registrada.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor

Si es TRUE, el recurso de cursor del sistema se cargará cuando se registre la clase de ventana.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Observaciones

De lo contrario, se cargará el recurso de cursor contenido en el módulo.

`CWndClassInfo`solo `m_bSystemCursor` se utiliza cuando se especifica el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX.](window-class-macros.md#declare_wnd_class_ex) En este `m_bSystemCursor` caso, se inicializa en TRUE. Para obtener más información, vea el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID

Especifica el nombre del recurso de cursor o el identificador de recurso en la palabra de orden bajo y cero en la palabra de orden superior.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Observaciones

Cuando se registra la clase de ventana, `m_lpszCursorID` el identificador del cursor identificado por se recupera y almacena mediante [m_wc](#m_wc).

`CWndClassInfo`solo `m_lpszCursorID` se utiliza cuando se especifica el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX.](window-class-macros.md#declare_wnd_class_ex) En este `m_lpszCursorID` caso, se inicializa en IDC_ARROW. Para obtener más información, vea el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName

Contiene el nombre de una clase de ventana existente.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Observaciones

`CWndClassInfo`solo `m_lpszOrigName` se utiliza cuando se incluye la [macro DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) en la definición de clase. En este `CWndClassInfo` caso, registra una clase de `m_lpszOrigName`ventana basada en la clase nombrada por . Para obtener más información, vea el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a>CWndClassInfo::m_szAutoName

Contiene el nombre de la clase de ventana.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Observaciones

`CWndClassInfo`utiliza `m_szAutoName` sólo si se `WndClassName` pasa NULL para que el parámetro [se DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), el [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) o [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL construirá un nombre cuando se registre la clase de ventana.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a>CWndClassInfo::m_wc

Mantiene la información de clase de ventana en una estructura [WNDCLASSEX.](/windows/win32/api/winuser/ns-winuser-wndclassexw)

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Observaciones

Si ha especificado el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX,](window-class-macros.md#declare_wnd_class_ex) `m_wc` contiene información sobre una nueva clase de ventana.

Si ha especificado la macro `m_wc` [DECLARE_WND_SUPERCLASS,](window-class-macros.md#declare_wnd_superclass) contiene información sobre una superclase, una clase de ventana que se basa en una clase existente pero utiliza un procedimiento de ventana diferente. [m_lpszOrigName](#m_lpszorigname) y [pWndProc](#pwndproc) guardan el nombre y el procedimiento de ventana de la clase de ventana existente, respectivamente.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc

Señala el procedimiento de ventana de una clase de ventana existente.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Observaciones

`CWndClassInfo`solo `pWndProc` se utiliza cuando se incluye la [macro DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) en la definición de clase. En este `CWndClassInfo` caso, registra una clase de ventana que se basa en una clase existente pero utiliza un procedimiento de ventana diferente. El procedimiento de ventana de la `pWndProc`clase de ventana existente se guarda en . Para obtener más información, vea el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

## <a name="cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::Register

Llamado por [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) para registrar la clase de ventana si aún no se ha registrado.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parámetros

*pProc*<br/>
[fuera] Especifica el procedimiento de ventana original de una clase de ventana existente.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un átomo que identifica de forma única la clase de ventana que se está registrando. De lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si ha especificado el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX,](window-class-macros.md#declare_wnd_class_ex) `Register` registra una nueva clase de ventana. En este caso, no se utiliza el parámetro *pProc.*

Si ha especificado la macro `Register` [DECLARE_WND_SUPERCLASS,](window-class-macros.md#declare_wnd_superclass) registra una superclase, una clase de ventana que se basa en una clase existente pero utiliza un procedimiento de ventana diferente. El procedimiento de ventana de la clase de ventana existente se devuelve en *pProc*.

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
