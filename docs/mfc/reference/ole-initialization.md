---
title: Inicialización de OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 330701c4fcc75d40e782d25baa55044b88852f50
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337802"
---
# <a name="ole-initialization"></a>Inicialización de OLE
Antes de que una aplicación puede usar servicios del sistema OLE, debe inicializar la DLL del sistema OLE y compruebe que los archivos DLL son la versión correcta. El `AfxOleInit` función inicializa la DLL del sistema OLE.  
  
### <a name="ole-initialization"></a>Inicialización de OLE  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|Inicializa las bibliotecas OLE.| 
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Llame a esta función en el objeto de aplicación `InitInstance` función para habilitar la compatibilidad con la contención de controles OLE.| 


## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer
Llame a esta función en el objeto de aplicación `InitInstance` función para habilitar la compatibilidad con la contención de controles OLE.  
   
### <a name="syntax"></a>Sintaxis    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los controles OLE (ahora denominados controles de ActiveX), consulte [temas de Control ActiveX](../mfc-activex-controls.md).  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  

  
##  <a name="afxoleinit"></a>  AfxOleInit  
 Inicializa la compatibilidad con OLE para la aplicación.  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ejecuta correctamente; 0 si se produce un error en la inicialización, posiblemente porque se han instalado versiones incorrectas de los archivos DLL del sistema OLE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para inicializar la compatibilidad con OLE para una aplicación MFC. Cuando se llama a esta función, tienen lugar las acciones siguientes:  
  
-   Inicializa la biblioteca COM en el apartamento actual de la aplicación de llamada. Para obtener más información, consulte [OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134).  
  
-   Crea un objeto de filtro de mensajes, implementar el [IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740) interfaz. Este filtro de mensajes puede obtenerse con una llamada a [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).  
  
> [!NOTE]
>  Si **AfxOleInit** se llama desde una DLL de MFC, la llamada se producirá un error. El error se produce porque la función supone que, si se llama desde un archivo DLL, la aplicación de llamada inicializó previamente el sistema OLE.  
  
> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) en su `InitInstance` invalidar, especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED). Para obtener más información, vea el artículo PRB: aplicación MFC deja de responder al inicializar la aplicación como un multiproceso apartamento (828643) en [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
