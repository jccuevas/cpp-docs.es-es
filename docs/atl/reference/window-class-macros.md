---
title: Macros de clase de ventana | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
dev_langs:
- C++
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0490eedb412e43f2ae99c4034648880be5f32a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364237"
---
# <a name="window-class-macros"></a>Macros de clase de ventana
Estas macros definen utilidades de la clase de ventana.  
  
|||  
|-|-|  
|[DECLARE_WND_CLASS](#declare_wnd_class)|Permite especificar el nombre de una nueva clase de ventana.| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(2017 de visual Studio) Permite especificar el nombre de una nueva clase de ventana y la clase envolvente cuyo procedimiento de ventana que se va a usar la nueva clase.| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Permite especificar el nombre de una clase de ventana existente en el que se basará una nueva clase de ventana.|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Permite especificar los parámetros de una clase.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
   
##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS  
 Permite especificar el nombre de una nueva clase de ventana. Coloque esta macro en la clase de control de un control ActiveX ATL.  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>Parámetros  
 `WndClassName`  
 [in] El nombre de la nueva clase de ventana. Si **NULL**, ATL generará un nombre de clase de ventana.  
  
### <a name="remarks"></a>Comentarios  
 Si está utilizando la opción /permissive-compiler, DECLARE_WND_CLASS provocará un error del compilador; Utilice DECLARE_WND_CLASS2 en su lugar.
 
 DECLARE_WND_CLASS le permite especificar el nombre de una nueva clase de ventana cuya información se administrarán con [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS` define la nueva clase de ventana mediante la implementación de la función estática siguiente:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 `DECLARE_WND_CLASS` Especifica los estilos siguientes de la nueva ventana:  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 `DECLARE_WND_CLASS` También especifica el color de fondo de la ventana de forma predeterminada. Use la [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) macro para proporcionar sus propios estilos y el color de fondo.  
  
 [CWindowImpl](cwindowimpl-class.md) usa el `DECLARE_WND_CLASS` macro para crear una ventana basada en una clase de ventana nueva. Para invalidar este comportamiento, use la [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) (macro), o proporcionar su propia implementación de la [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) función.  

  
 Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana de ATL](../../atl/atl-window-classes.md).  

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2  
 (2017 de visual Studio) Similar a DECLARE_WND_CLASS, pero con un parámetro adicional que evita un error de nombre dependiente cuando se compila con la /permissive-option.
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>Parámetros  
 `WndClassName`  
 [in] El nombre de la nueva clase de ventana. Si **NULL**, ATL generará un nombre de clase de ventana. 

 `EnclosingClass`  
 [in] El nombre de la clase de ventana que contiene la nueva clase de ventana. No puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios 
Si usas el /permissive-option, DECLARE_WND_CLASS provocará un error de compilación porque contiene un nombre dependiente. DECLARE_WND_CLASS2 requiere un nombre explícito a la clase que esta macro se usa en y no provoca el error en la /permissive-flag.
En caso contrario, esta macro equivale a [DECLARE_WND_CLASS](#declare_wnd_class).
   
##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS  
 Permite especificar los parámetros de una clase. Coloque esta macro en la clase de control de un control ActiveX ATL.  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>Parámetros  
 `WndClassName`  
 [in] El nombre de la ventana de clase que superclase will `OrigWndClassName`. Si **NULL**, ATL generará un nombre de clase de ventana.  
  
 `OrigWndClassName`  
 [in] El nombre de una clase de ventana existente.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro permite especificar el nombre de una clase de ventana que le superclase de una clase de ventana existente. [CWndClassInfo](cwndclassinfo-class.md) administra la información de la superclase.  
  
 `DECLARE_WND_SUPERCLASS` implementa la función estática siguiente:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 De forma predeterminada, [CWindowImpl](cwindowimpl-class.md) utiliza la [DECLARE_WND_CLASS](#declare_wnd_class) macro para crear una ventana basada en una clase de ventana nueva. Mediante la especificación de la `DECLARE_WND_SUPERCLASS` macro en un `CWindowImpl`-clase derivada, la clase de ventana se basará en una clase existente pero va a utilizar el procedimiento de ventana. Esta técnica se conoce como creación de superclases.  
  
 Además de utilizar el `DECLARE_WND_CLASS` y `DECLARE_WND_SUPERCLASS` macros, puede invalidar la [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) función con su propia implementación.  

  
 Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana de ATL](../../atl/atl-window-classes.md).  
  
##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX  
 Permite especificar el nombre de una clase de ventana existente en el que se basará una nueva clase de ventana. Coloque esta macro en la clase de control de un control ActiveX ATL.  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>Parámetros  
 `WndClassName`  
 [in] El nombre de la nueva clase de ventana. Si **NULL**, ATL generará un nombre de clase de ventana.  
  
 `style`  
 [in] El estilo de la ventana.  
  
 *fondo*  
 [in] El color de fondo de la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro permite especificar los parámetros de la clase de una nueva clase de ventana, cuya información se administrarán con [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS_EX` define la nueva clase de ventana mediante la implementación de la función estática siguiente:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 Si desea usar los estilos predeterminados y el color de fondo, utilice la [DECLARE_WND_CLASS](#declare_wnd_class) macro. Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana de ATL](../../atl/atl-window-classes.md).  
  
## <a name="see-also"></a>Vea también  
 [Macros](atl-macros.md)









