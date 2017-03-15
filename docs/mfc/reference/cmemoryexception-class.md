---
title: Clase CMemoryException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException class
- memory exceptions
- exceptions, memory type
- C++ exception handling, memory
- memory, exception handling
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
caps.latest.revision: 20
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 87be1b16d546791d24bbffa62207ec9ccb350139
ms.lasthandoff: 02/24/2017

---
# <a name="cmemoryexception-class"></a>Clase CMemoryException
Representa una condición de excepción de memoria insuficiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](#cmemoryexception)|Construye un objeto `CMemoryException`.|  
  
## <a name="remarks"></a>Comentarios  
 Calificación adicional no es necesaria ni posible. Memoria excepciones automáticamente **nueva**. Si escribe sus propias funciones de memoria, uso `malloc`, por ejemplo, es responsable de producir excepciones de memoria.  
  
 Para obtener más información sobre `CMemoryException`, vea el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="a-namecmemoryexceptiona--cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException::CMemoryException  
 Construye un objeto `CMemoryException`.  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>Comentarios  
 No utilice este constructor directamente, pero en su lugar llame a la función global [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Esta función global puede realizarse en una situación de falta de memoria ya construye el objeto de excepción de memoria asignado previamente. Para obtener más información sobre el procesamiento de excepciones, vea el artículo [excepciones](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [CException (clase)](cexception-class.md)   
 [Gráfico de jerarquía](../hierarchy-chart.md)




