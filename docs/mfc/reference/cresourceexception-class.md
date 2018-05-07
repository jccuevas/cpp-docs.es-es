---
title: Clase CResourceException | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fdbfb29b00eaac40b4da2b78753df6a0596764f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cresourceexception-class"></a>Clase CResourceException
Se genera cuando Windows no puede encontrar o asignar un recurso solicitado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
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
  
##  <a name="cresourceexception"></a>  CResourceException::CResourceException  
 Construye un objeto `CResourceException`.  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>Comentarios  
 No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Para obtener más información sobre las excepciones, vea el artículo [control de excepciones en MFC](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](cexception-class.md)   
 [Gráfico de jerarquías](../hierarchy-chart.md)


