---
title: Tipo de acceso a la biblioteca | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 8f05738c02fd70fde5fc2d92c5ee1e823747797c
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="type-library-access"></a>Acceso a la biblioteca de tipos
Bibliotecas de tipos exponen las interfaces de un control OLE para otras aplicaciones compatibles con OLE. Cada control OLE debe tener una biblioteca de tipos si una o más interfaces que se van a exponer.  
  
 Las macros siguientes permiten un control OLE proporcionar acceso a su propia biblioteca de tipos:  
  
### <a name="type-library-access"></a>Acceso a la biblioteca de tipos  
  
|||  
|-|-|  
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Declara un `GetTypeLib` función miembro de un control OLE (debe usarse en la declaración de clase).|  
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementa un `GetTypeLib` función miembro de un control OLE (debe usarse en la implementación de la clase).|  
  
##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB  
 Declara el `GetTypeLib` función miembro de la clase del control.  
  
```   
DECLARE_OLETYPELIB(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control relacionada con la biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Use esta macro en el archivo de encabezado de la clase de control.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB  
 Implementa el control `GetTypeLib` función miembro.  
  
```   
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase de control relacionada con la biblioteca de tipos.  
  
 *tlid*  
 El número de Id. de la biblioteca de tipos.  
  
 `wVerMajor`  
 El número de versión principal de biblioteca de tipos.  
  
 `wVerMinor`  
 El número de versión secundaria de biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que utiliza la `DECLARE_OLETYPELIB` macro.  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
   
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

