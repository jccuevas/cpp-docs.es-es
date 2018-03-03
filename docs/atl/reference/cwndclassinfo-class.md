---
title: Clase CWndClassInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b07f6b12914e18f3f83abedf59742a8b7c7867b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cwndclassinfo-class"></a>Clase CWndClassInfo
Esta clase proporciona métodos para registrar información de una clase de ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
|[m_atom](#m_atom)|Identifica la clase de ventana registrados.|  
|[m_bSystemCursor](#m_bsystemcursor)|Especifica si el recurso de cursor hace referencia a un cursor de sistema o a un cursor dentro de un recurso de un módulo.|  
|[m_lpszCursorID](#m_lpszcursorid)|Especifica el nombre del recurso de cursor.|  
|[m_lpszOrigName](#m_lpszorigname)|Contiene el nombre de una clase de ventana existente.|  
|[m_szAutoName](#m_szautoname)|Contiene un nombre de la clase de ventana generado con ATL.|  
|[m_wc](#m_wc)|Mantiene la información de clase de ventana en un **WNDCLASSEX** estructura.|  
|[pWndProc](#pwndproc)|Señala al procedimiento de ventana de una clase de ventana existente.|  
  
## <a name="remarks"></a>Comentarios  
 `CWndClassInfo`administra la información de una clase de ventana. Se suele usar `CWndClassInfo` a través de uno de tres macros, `DECLARE_WND_CLASS`, `DECLARE_WND_CLASS_EX`, o `DECLARE_WND_SUPERCLASS`, como se describe en la tabla siguiente:  
  
|Macro|Descripción|  
|-----------|-----------------|  
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`registra la información para una nueva clase de ventana.|  
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`registra la información para una nueva clase de ventana, incluidos los parámetros de la clase.|  
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`registra la información para una clase de ventana que se basa en una clase existente pero que utiliza un procedimiento de ventana diferente. Esta técnica se conoce como creación de superclases.|  
  
 De forma predeterminada, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) incluye la `DECLARE_WND_CLASS` macro para crear una ventana basada en una clase de ventana nueva. DECLARE_WND_CLASS proporciona estilos predeterminados y el color de fondo para el control. Si desea especificar el estilo y color de fondo por sí mismo, derive su clase de `CWindowImpl` e incluya el `DECLARE_WND_CLASS_EX` macro en la definición de clase.  
  
 Si desea crear una ventana basada en una clase de ventana existente, derive su clase de `CWindowImpl` e incluya el `DECLARE_WND_SUPERCLASS` macro en la definición de clase. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 Para obtener más información acerca de las clases de ventana, consulte [clases de ventana](http://msdn.microsoft.com/library/windows/desktop/ms632596) del SDK de Windows.  
  
 Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana de ATL](../../atl/atl-window-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="m_atom"></a>CWndClassInfo::m_atom  
 Contiene el identificador único para la clase de ventana registrados.  
  
```
ATOM m_atom;
```  
  
##  <a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor  
 Si **TRUE**, el recurso de cursor de sistema se cargará cuando se registra la clase de ventana.  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>Comentarios  
 En caso contrario, se cargará el recurso de cursor contenido en el módulo.  
  
 `CWndClassInfo`usa `m_bSystemCursor` solo cuando la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) se especifica la macro. En este caso, `m_bSystemCursor` se inicializa en **TRUE**. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.  
  
##  <a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID  
 Especifica el nombre del recurso de cursor o el identificador de recurso en la palabra de orden inferior y cero en la palabra de orden superior.  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se registra la clase de ventana, el identificador del cursor identificado por `m_lpszCursorID` se recuperan y almacenan por [m_wc](#m_wc).  
  
 `CWndClassInfo`usa `m_lpszCursorID` solo cuando la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) se especifica la macro. En este caso, `m_lpszCursorID` se inicializa en **IDC_ARROW**. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.  
  
##  <a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName  
 Contiene el nombre de una clase de ventana existente.  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>Comentarios  
 `CWndClassInfo`usa `m_lpszOrigName` sólo cuando se incluyen la [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro en la definición de clase. En este caso, `CWndClassInfo` registros en función de una clase de ventana en la clase denominada por `m_lpszOrigName`. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.  
  
##  <a name="m_szautoname"></a>CWndClassInfo::m_szAutoName  
 Contiene el nombre de la clase de ventana.  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>Comentarios  
 `CWndClassInfo`usa `m_szAutoName` solo si **NULL** se pasa para el `WndClassName` parámetro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) o [ DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL construirá un nombre cuando se registra la clase de ventana.  
  
##  <a name="m_wc"></a>CWndClassInfo::m_wc  
 Mantiene la información de clase de ventana en un [WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577) estructura.  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>Comentarios  
 Si ha especificado el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro, `m_wc` contiene información sobre una nueva clase de ventana.  
  
 Si ha especificado el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro, `m_wc` contiene información sobre una superclase: una clase de ventana que se basa en una clase existente pero que utiliza un procedimiento de ventana diferente. [m_lpszOrigName](#m_lpszorigname) y [pWndProc](#pwndproc) guardar el nombre de la clase de ventana existente y el procedimiento de ventana, respectivamente.  
  
##  <a name="pwndproc"></a>CWndClassInfo::pWndProc  
 Señala al procedimiento de ventana de una clase de ventana existente.  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>Comentarios  
 `CWndClassInfo`usa `pWndProc` sólo cuando se incluyen la [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro en la definición de clase. En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente pero que utiliza un procedimiento de ventana diferente. Procedimiento de ventana de la clase de ventana existente se guarda en `pWndProc`. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.  
  
##  <a name="register"></a>CWndClassInfo::Register  
 Llamado por el método [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create) para registrar la clase de ventana si aún no se ha registrado.  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>Parámetros  
 `pProc`  
 [out] Especifica el procedimiento de ventana original de una clase de ventana existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, una atom que identifica de forma única la clase de ventana que se va a registrar. En caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si ha especificado el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o la [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro, `Register` registra una nueva clase de ventana. En este caso, el `pProc` parámetro no se utiliza.  
  
 Si ha especificado el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro, `Register` registra una superclase: una clase de ventana que se basa en una clase existente pero que utiliza un procedimiento de ventana diferente. Procedimiento de ventana de la clase de ventana existente se devuelve en `pProc`.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)