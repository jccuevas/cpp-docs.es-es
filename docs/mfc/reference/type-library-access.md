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
- type libraries, accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8a3fbcf66036ef3df3bd34b5182dac8af3dfccef
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="type-library-access"></a>Acceso a la biblioteca de tipos
Bibliotecas de tipos exponen las interfaces de un control OLE a otras aplicaciones compatibles con OLE. Cada control OLE debe tener una biblioteca de tipos si una o más interfaces deben exponerse.  
  
 Las macros siguientes permiten un control OLE proporcionar acceso a su propia biblioteca de tipos:  
  
### <a name="type-library-access"></a>Acceso a la biblioteca de tipos  
  
|||  
|-|-|  
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Declara un `GetTypeLib` función miembro de un control OLE (utilizado en la declaración de clase).|  
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementa un `GetTypeLib` función miembro de un control OLE (debe utilizarse en la implementación de la clase).|  
  
##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB  
 Declara el `GetTypeLib` función miembro de la clase del control.  
  
```   
DECLARE_OLETYPELIB(class_name)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase del control relacionadas con la biblioteca de tipos.  
  
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
 El nombre de la clase del control relacionadas con la biblioteca de tipos.  
  
 *tlid*  
 El número de Id. de la biblioteca de tipos.  
  
 `wVerMajor`  
 El número de versión principal de biblioteca de tipos.  
  
 `wVerMinor`  
 El número de versión secundaria de biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro debe aparecer en el archivo de implementación para cualquier clase de control que utiliza la `DECLARE_OLETYPELIB` (macro).  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
   
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

