---
title: Clase CResourceException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs: C++
helpviewer_keywords: CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 497ced5337a44bb0d72be734cfea35a30ead383b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cresourceexception-class"></a>Clase CResourceException
Se genera cuando Windows no puede encontrar o asignar un recurso solicitado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CResourceException::CResourceException](#cresourceexception)|Construye un objeto `CResourceException`.|  
  
## <a name="remarks"></a>Comentarios  
 Calificación adicional no es necesaria o posible.  
  
 Para obtener más información sobre el uso de `CResourceException`, vea el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cresourceexception"></a>CResourceException::CResourceException  
 Construye un objeto `CResourceException`.  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>Comentarios  
 No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Para obtener más información sobre las excepciones, vea el artículo [control de excepciones en MFC](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](cexception-class.md)   
 [Gráfico de jerarquías](../hierarchy-chart.md)


