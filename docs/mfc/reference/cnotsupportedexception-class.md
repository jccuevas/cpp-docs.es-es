---
title: Clase CNotSupportedException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4013b26e3c07d6ec2a729bf9868db48923e35f86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cnotsupportedexception-class"></a>Clase CNotSupportedException
Representa una excepción que es el resultado de una solicitud de una característica no compatible.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Construye un objeto `CNotSupportedException`.|  
  
## <a name="remarks"></a>Comentarios  
 Calificación adicional no es necesaria o posible.  
  
 Para obtener más información sobre el uso de `CNotSupportedException`, vea el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException  
 Construye un objeto `CNotSupportedException`.  
  
```  
CNotSupportedException();
```  
  
### <a name="remarks"></a>Comentarios  
 No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). Para obtener más información sobre el procesamiento de excepciones, vea el artículo [control de excepciones en MFC](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](cexception-class.md)   
 [Gráfico de jerarquías](../hierarchy-chart.md)


