---
title: Clase CSimpleException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
dev_langs: C++
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70ed8ecc43f8467ca4e0bdc0856b32f3510d85a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="csimpleexception-class"></a>Clase CSimpleException
Esta clase es una clase base para excepciones MFC de recursos críticos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class AFX_NOVTABLE CSimpleException : public CException  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleException::CSimpleException](#csimpleexception)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleException::GetErrorMessage](#geterrormessage)|Proporciona información sobre un error que se ha producido.|  
  
## <a name="remarks"></a>Comentarios  
 `CSimpleException`es la clase base para excepciones de MFC de recursos críticos y controla la propiedad y la inicialización de un mensaje de error. Las siguientes clases utilizan `CSimpleException` como su clase base:  
  
|||  
|-|-|  
|[CMemoryException (clase)](../../mfc/reference/cmemoryexception-class.md)|Excepción de memoria insuficiente|  
|[CNotSupportedException (clase)](../../mfc/reference/cnotsupportedexception-class.md)|Solicitudes de una operación no admitida|  
|[CResourceException (clase)](../../mfc/reference/cresourceexception-class.md)|Recursos de Windows no se encuentra o no puede crear|  
|[CUserException (clase)](../../mfc/reference/cuserexception-class.md)|No se encontró la excepción que indica un recurso|  
|[CInvalidArgException (clase)](../../mfc/reference/cinvalidargexception-class.md)|Excepción que indica un argumento no válido|  
  
 Dado que `CSimpleException` es una clase base abstracta, no puede declarar un `CSimpleException` objeto directamente. En su lugar, se deben declarar objetos derivados, como los de la tabla anterior. Si va a declarar su propia clase derivada, utilice las clases anteriores como un modelo.  
  
 Para obtener más información, consulte el [CException (clase)](../../mfc/reference/cexception-class.md) tema y [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="csimpleexception"></a>CSimpleException::CSimpleException  
 El constructor.  
  
```  
CSimpleException();  
explicit CSimpleException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAutoDelete`  
 Especifique **TRUE** si la memoria para el `CSimpleException` objeto se ha asignado en el montón. Esto hará que la `CSimpleException` objeto que se eliminará cuando el **eliminar** función miembro se llama para eliminar la excepción. Especifique **FALSE** si la `CSimpleException` objeto está en la pila o es un objeto global. En este caso, el `CSimpleException` objeto no se podrá eliminar cuando el **eliminar** se llama la función miembro.  
  
### <a name="remarks"></a>Comentarios  
 General, nunca se necesita llamar directamente a este constructor. Una función que produce una excepción debe crearse una instancia de un `CException`-clase derivada y llamar a su constructor, o bien debe usar uno de lo MFC iniciar funciones, como [AfxThrowFileException](exception-processing.md#afxthrowfileexception), se producirá un tipo predefinido.  
  
##  <a name="geterrormessage"></a>CSimpleException::GetErrorMessage  
 Llame a esta función miembro para proporcionar el texto sobre un error que se ha producido.  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszError`  
 Un puntero a un búfer que recibirá un mensaje de error.  
  
 `nMaxError`  
 El número máximo de caracteres que puede contener el búfer, incluido el **NULL** terminador.  
  
 `pnHelpContext`  
 La dirección de un **UINT** que va a recibir el identificador de contexto de ayuda. Si **NULL**, no se devolverá ningún identificador.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; en caso contrario, devuelve 0 si ningún error de texto del mensaje está disponible.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Control de excepciones](../../mfc/exception-handling-in-mfc.md)



