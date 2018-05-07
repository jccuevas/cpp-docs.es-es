---
title: Clase CMemoryException | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12971af6bed7c04c6f6f214f0b583a4f7e6eb7a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmemoryexception-class"></a>Clase CMemoryException
Representa una condición de excepción de memoria insuficiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](#cmemoryexception)|Construye un objeto `CMemoryException`.|  
  
## <a name="remarks"></a>Comentarios  
 Calificación adicional no es necesaria o posible. Las excepciones de memoria se inician automáticamente **nueva**. Si escribe sus propias funciones de memoria, utilizando `malloc`, por ejemplo, a continuación, que es responsables de producir excepciones de memoria.  
  
 Para obtener más información sobre `CMemoryException`, vea el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException  
 Construye un objeto `CMemoryException`.  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>Comentarios  
 No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Esta función global puede correctamente en una situación de falta de memoria, ya que construye el objeto de excepción en la memoria previamente asignada. Para obtener más información sobre el procesamiento de excepciones, vea el artículo [excepciones](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](cexception-class.md)   
 [Gráfico de jerarquías](../hierarchy-chart.md)



