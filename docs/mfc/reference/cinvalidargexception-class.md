---
title: Clase CInvalidArgException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
dev_langs:
- C++
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03f9bea1c9e5e88856bbf5a5aa2e824a2c99963c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cinvalidargexception-class"></a>Clase CInvalidArgException
Esta clase representa una condición de excepción de argumento no válido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CInvalidArgException : public CSimpleException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|El constructor.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CInvalidArgException` objeto representa una condición de excepción de argumento no válido.  
  
 Para obtener más información sobre el control de excepciones, consulte la [CException (clase)](../../mfc/reference/cexception-class.md) tema y [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException  
 El constructor.  
  
```  
CInvalidArgException();
```  
  
### <a name="remarks"></a>Comentarios  
 No utilice este constructor directamente; Llame a la función global **AfxThrowInvalidArgException**.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSimpleException (clase)](../../mfc/reference/csimpleexception-class.md)
