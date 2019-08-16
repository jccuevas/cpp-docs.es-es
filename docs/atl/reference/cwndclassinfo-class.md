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
ms.openlocfilehash: c416155ed103f1345c42e6680c2329ab98d35926
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496125"
---
# <a name="cwndclassinfo-class"></a>Clase CWndClassInfo

Esta clase proporciona métodos para registrar información para una clase de ventana.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CWndClassInfo
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|[Registro](#register)|Registra la clase de ventana.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_atom](#m_atom)|Identifica de forma única la clase de ventana registrada.|
|[m_bSystemCursor](#m_bsystemcursor)|Especifica si el recurso de cursor hace referencia a un cursor del sistema o a un cursor contenido en un recurso de módulo.|
|[m_lpszCursorID](#m_lpszcursorid)|Especifica el nombre del recurso de cursor.|
|[m_lpszOrigName](#m_lpszorigname)|Contiene el nombre de una clase de ventana existente.|
|[m_szAutoName](#m_szautoname)|Contiene un nombre generado por ATL de la clase de ventana.|
|[m_wc](#m_wc)|Mantiene la información de la clase `WNDCLASSEX` de ventana en una estructura.|
|[pWndProc](#pwndproc)|Apunta al procedimiento de ventana de una clase de ventana existente.|

## <a name="remarks"></a>Comentarios

`CWndClassInfo`administra la información de una clase de ventana. Normalmente se usa `CWndClassInfo` a través de una de tres macros, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX o DECLARE_WND_SUPERCLASS, como se describe en la tabla siguiente:

|Macro|DESCRIPCIÓN|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`registra información para una nueva clase de ventana.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`registra información para una nueva clase de ventana, incluidos los parámetros de clase.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`registra información de una clase de ventana que se basa en una clase existente, pero utiliza un procedimiento de ventana diferente. Esta técnica se denomina superclase.|

De forma predeterminada, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) incluye `DECLARE_WND_CLASS` la macro para crear una ventana basada en una nueva clase de ventana. DECLARE_WND_CLASS proporciona los estilos predeterminados y el color de fondo para el control. Si desea especificar el estilo y el color de fondo, derive la clase de `CWindowImpl` e incluya la macro DECLARE_WND_CLASS_EX en la definición de clase.

Si desea crear una ventana basada en una clase de ventana existente, derive la clase de `CWindowImpl` e incluya la macro DECLARE_WND_SUPERCLASS en la definición de clase. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Para obtener más información sobre las clases de ventana, vea [clases de ventana](/windows/win32/winmsg/window-classes) en el Windows SDK.

Para obtener más información sobre el uso de Windows en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="m_atom"></a>  CWndClassInfo::m_atom

Contiene el identificador único de la clase de ventana registrada.

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor

Si es TRUE, el recurso de cursor del sistema se cargará cuando se registre la clase de ventana.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Comentarios

De lo contrario, se cargará el recurso de cursor incluido en el módulo.

`CWndClassInfo`solo `m_bSystemCursor` se usa cuando se especifica [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) . En este caso, `m_bSystemCursor` se inicializa en true. Para obtener más información, consulte la información general de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID

Especifica el nombre del recurso de cursor o el identificador de recurso en la palabra de orden inferior y cero en la palabra de orden superior.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Comentarios

Cuando se registra la clase de ventana, [m_wc](#m_wc)recupera y almacena el identificador `m_lpszCursorID` del cursor identificado por.

`CWndClassInfo`solo `m_lpszCursorID` se usa cuando se especifica [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) . En este caso, `m_lpszCursorID` se inicializa en IDC_ARROW. Para obtener más información, consulte la información general de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName

Contiene el nombre de una clase de ventana existente.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Comentarios

`CWndClassInfo`solo `m_lpszOrigName` se usa cuando se incluye la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) en la definición de clase. En este caso, `CWndClassInfo` registra una clase de ventana basada en la clase denominada por `m_lpszOrigName`. Para obtener más información, consulte la información general de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName

Contiene el nombre de la clase de ventana.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Comentarios

`CWndClassInfo`usa `m_szAutoName` solo si se pasa null para el `WndClassName` parámetro a [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) o [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL construirá un nombre cuando se registra la clase de ventana.

##  <a name="m_wc"></a>  CWndClassInfo::m_wc

Mantiene la información de la clase de ventana en una estructura [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw) .

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Comentarios

Si ha especificado [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `m_wc` contiene información sobre una nueva clase de ventana.

Si ha especificado la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , contiene `m_wc` información sobre una superclase, una clase de ventana que se basa en una clase existente, pero utiliza un procedimiento de ventana diferente. [m_lpszOrigName](#m_lpszorigname) y [pWndProc](#pwndproc) guardan el nombre y el procedimiento de ventana de la clase de ventana existente, respectivamente.

##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc

Apunta al procedimiento de ventana de una clase de ventana existente.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Comentarios

`CWndClassInfo`solo `pWndProc` se usa cuando se incluye la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) en la definición de clase. En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente, pero utiliza un procedimiento de ventana diferente. El procedimiento de ventana de la clase de ventana existente `pWndProc`se guarda en. Para obtener más información, consulte la información general de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

##  <a name="register"></a>  CWndClassInfo::Register

Lo llama [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create) para registrar la clase de ventana si aún no se ha registrado.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parámetros

*pProc*<br/>
enuncia Especifica el procedimiento de ventana original de una clase de ventana existente.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un átomo que identifica de forma única la clase de ventana que se va a registrar. De lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si ha especificado [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `Register` registra una nueva clase de ventana. En este caso, no se usa el parámetro *pProc* .

Si ha especificado la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , registra `Register` una superclase, una clase de ventana que se basa en una clase existente, pero utiliza un procedimiento de ventana diferente. El procedimiento de ventana de la clase de ventana existente se devuelve en *pProc*.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
