---
title: Macros de clase de ventana | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: f32926b6efd4ffb9c0541c0574a479c13dac01df
ms.lasthandoff: 02/24/2017

---
# <a name="window-class-macros"></a>Macros de clase de ventana
Estas macros definen utilidades de la clase de ventana.  
  
|||  
|-|-|  
|[DECLARE_WND_CLASS](#declare_wnd_class)|Permite especificar el nombre de una nueva clase de ventana.| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(2017 de visual Studio) Permite especificar el nombre de una nueva clase de ventana y la clase envolvente cuyo procedimiento de ventana que se va a utilizar la nueva clase.| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Permite especificar el nombre de una clase de ventana existente en el que se basará la nueva clase de ventana.|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Permite especificar los parámetros de una clase.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
   
##  <a name="a-namedeclarewndclassa--declarewndclass"></a><a name="declare_wnd_class"></a>DECLARE_WND_CLASS  
 Permite especificar el nombre de una nueva clase de ventana. Coloque esta macro en la clase de control de un control ActiveX ATL.  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>Parámetros  
 `WndClassName`  
 [in] El nombre de la nueva clase de ventana. Si **NULL**, ATL generará un nombre de clase de ventana.  
  
### <a name="remarks"></a>Comentarios  
 Si utiliza la opción /permissive-compiler, DECLARE_WND_CLASS provocará un error del compilador; Utilice DECLARE_WND_CLASS2 en su lugar.
 
 DECLARE_WND_CLASS le permite especificar el nombre de una nueva clase de ventana cuya información se administrarán por [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS`define la nueva clase de ventana mediante la implementación de la función estática siguiente:  
  
 [!code-cpp[127 NVC_ATL_Windowing](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 `DECLARE_WND_CLASS`Especifica los estilos de la nueva ventana siguientes:  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 `DECLARE_WND_CLASS`También especifica el color de fondo de la ventana de forma predeterminada. Utilice la [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) macro para proporcionar sus propios estilos y el color de fondo.  
  
 [CWindowImpl](cwindowimpl-class.md) utiliza la `DECLARE_WND_CLASS` (macro) para crear una ventana basada en una clase de ventana nueva. Para invalidar este comportamiento, use la [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) (macro), o proporcionar su propia implementación de la [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) (función).  

  
 Para obtener más información acerca de cómo utilizar ventanas en ATL, vea el artículo [clases de ventana de ATL](../../atl/atl-window-classes.md).  

##  <a name="a-namedeclarewndclass2a--declarewndclass2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2  
 (2017 de visual Studio) Similar a DECLARE_WND_CLASS, pero con un parámetro adicional que evita un error de nombre dependientes cuando se compila con la /permissive-option.
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>Parámetros  
 `WndClassName`  
 [in] El nombre de la nueva clase de ventana. Si **NULL**, ATL generará un nombre de clase de ventana. 

 `EnclosingClass`  
 [in] El nombre de la clase de ventana que incluye la nueva clase de ventana. No puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios 
Si usa el /permissive-option, DECLARE_WND_CLASS provocará un error de compilación porque contiene un nombre dependiente. DECLARE_WND_CLASS2 requiere un nombre explícito a la clase que se utiliza en esta macro y el no provoca el error en la /permissive-flag.
De lo contrario, es idéntica a esta macro [DECLARE_WND_CLASS](#declare_wnd_class).
   
##  <a name="a-namedeclarewndsuperclassa--declarewndsuperclass"></a><a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS  
 Permite especificar los parámetros de una clase. Coloque esta macro en la clase de control de un control ActiveX ATL.  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>Parámetros  
 `WndClassName`  
 [in] El nombre de la ventana de la clase que superclase será `OrigWndClassName`. Si **NULL**, ATL generará un nombre de clase de ventana.  
  
 `OrigWndClassName`  
 [in] El nombre de una clase de ventana existente.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro permite especificar el nombre de una clase de ventana que le superclase de una clase de ventana existente. [CWndClassInfo](cwndclassinfo-class.md) administra la información de la superclase.  
  
 `DECLARE_WND_SUPERCLASS`implementa la función estática siguiente:  
  
 [!code-cpp[127 NVC_ATL_Windowing](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 De forma predeterminada, [CWindowImpl](cwindowimpl-class.md) utiliza la [DECLARE_WND_CLASS](#declare_wnd_class) macro para crear una ventana basada en una clase de ventana nueva. Especificando el `DECLARE_WND_SUPERCLASS` macro en un `CWindowImpl`-clase derivada, la clase de ventana se basará en una clase existente pero utilizará el procedimiento de ventana. Esta técnica se denomina creación de superclases.  
  
 Además de utilizar la `DECLARE_WND_CLASS` y `DECLARE_WND_SUPERCLASS` macros, puede invalidar la [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) función con su propia implementación.  

  
 Para obtener más información acerca de cómo utilizar ventanas en ATL, vea el artículo [clases de ventana de ATL](../../atl/atl-window-classes.md).  
  
##  <a name="a-namedeclarewndclassexa--declarewndclassex"></a><a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX  
 Permite especificar el nombre de una clase de ventana existente en el que se basará la nueva clase de ventana. Coloque esta macro en la clase de control de un control ActiveX ATL.  
  
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
 Esta macro permite especificar los parámetros de la clase de una nueva clase de ventana, cuya información se administrarán por [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS_EX`define la nueva clase de ventana mediante la implementación de la función estática siguiente:  
  
 [!code-cpp[127 NVC_ATL_Windowing](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 Si desea utilizar los estilos predeterminados y el color de fondo, utilice la [DECLARE_WND_CLASS](#declare_wnd_class) macro. Para obtener más información acerca de cómo utilizar ventanas en ATL, vea el artículo [clases de ventana de ATL](../../atl/atl-window-classes.md).  
  
## <a name="see-also"></a>Vea también  
 [Macros](atl-macros.md)










