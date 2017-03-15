---
title: "Inicialización de OLE | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
caps.latest.revision: 13
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 5c2d8a1552b8cd546b7e22683fe9f73bbc54df5c
ms.lasthandoff: 02/24/2017

---
# <a name="ole-initialization"></a>Inicialización de OLE
Antes de que una aplicación puede utilizar los servicios del sistema OLE, debe inicializar los archivos DLL del sistema OLE y compruebe que los archivos DLL son la versión correcta. El **AfxOleInit** función inicializa la DLL del sistema OLE.  
  
### <a name="ole-initialization"></a>Inicialización de OLE  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|Inicializa las bibliotecas OLE.|  
  
##  <a name="a-nameafxoleinita--afxoleinit"></a><a name="afxoleinit"></a>AfxOleInit  
 Inicializa la compatibilidad con OLE para la aplicación.  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se ejecuta correctamente; 0 si se produce un error en la inicialización, posiblemente porque se han instalado versiones incorrectas de los archivos DLL del sistema OLE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para inicializar la compatibilidad con OLE para una aplicación MFC. Cuando se llama a esta función, tienen lugar las acciones siguientes:  
  
-   Inicializa la biblioteca COM en el apartamento actual de la aplicación de llamada. Para obtener más información, consulte [OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134).  
  
-   Crea un objeto de filtro de mensajes, implementar la [IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740) interfaz. Este filtro de mensajes puede obtenerse con una llamada a [AfxOleGetMessageFilter](http://msdn.microsoft.com/library/36cca011-4775-4086-b471-5557a87b266c).  
  
> [!NOTE]
>  Si **AfxOleInit** se llama desde una DLL de MFC, la llamada producirá un error. El error se produce porque la función supone que, si se llama desde un archivo DLL, la aplicación de llamada inicializó previamente el sistema OLE.  
  
> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) en su `InitInstance` invalidar, especifique `COINIT_APARTMENTTHREADED` (en lugar de `COINIT_MULTITHREADED`). Para obtener más información, vea el artículo PRB: aplicación MFC deja de responder cuando se inicializa la aplicación como un multiproceso apartamento (828643) en [http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h

## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

