---
title: Clase CSimpleException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleException
dev_langs:
- C++
helpviewer_keywords:
- CSimpleException class
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
caps.latest.revision: 19
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5612d76a2351b9898b8ffe082844686d21fcd7a0
ms.lasthandoff: 02/24/2017

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
|[CSimpleException::GetErrorMessage](#geterrormessage)|Proporciona texto sobre un error que se ha producido.|  
  
## <a name="remarks"></a>Comentarios  
 `CSimpleException`es la clase base para excepciones de MFC recursos críticos y controla la propiedad e inicialización de un mensaje de error. Las siguientes clases utilizan `CSimpleException` como su clase base:  
  
|||  
|-|-|  
|[Clase CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Excepción de memoria insuficiente|  
|[Clase CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Solicitudes de una operación no admitida|  
|[Clase CResourceException](../../mfc/reference/cresourceexception-class.md)|Recursos de Windows no encuentra o no se puede crear|  
|[Clase CUserException](../../mfc/reference/cuserexception-class.md)|No se encontró la excepción que indica un recurso|  
|[Clase CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Excepción que indica un argumento no válido|  
  
 Porque `CSimpleException` es una clase base abstracta, no puede declarar un `CSimpleException` objeto directamente. En su lugar, debe declarar objetos derivados, como los de la tabla anterior. Si va a declarar su propia clase derivada, utilice las clases anteriores como modelo.  
  
 Para obtener más información, consulte el [clase CException](../../mfc/reference/cexception-class.md) tema y [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  
  
##  <a name="a-namecsimpleexceptiona--csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>CSimpleException::CSimpleException  
 El constructor.  
  
```  
CSimpleException();  
explicit CSimpleException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAutoDelete`  
 Especifique **TRUE** si la memoria para el `CSimpleException` se ha asignado el objeto en el montón. Esto hará que el `CSimpleException` objeto que se eliminará cuando el **eliminar** función miembro se llama para eliminar la excepción. Especifique **FALSE** si la `CSimpleException` objeto está en la pila o es un objeto global. En este caso, el `CSimpleException` objeto no se podrá eliminar cuando el **eliminar** se llama la función miembro.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente no necesitará llamar directamente a este constructor. Una función que produce una excepción debe crear una instancia de un `CException`-clase derivada y llamar a su constructor, o bien debe generar uso de MFC a las funciones, como [AfxThrowFileException](exception-processing.md#afxthrowfileexception), para producir un tipo predefinido.  
  
##  <a name="a-namegeterrormessagea--csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>CSimpleException::GetErrorMessage  
 Llame a esta función miembro para proporcionar el texto sobre un error que se ha producido.  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszError`  
 Puntero a un búfer que recibirá un mensaje de error.  
  
 `nMaxError`  
 El número máximo de caracteres que puede contener el búfer, incluida la **NULL** terminador.  
  
 `pnHelpContext`  
 La dirección de un **UINT** que recibirá el identificador de contexto de ayuda. Si **NULL**, no se devolverá ningún ID.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, 0 si el texto del mensaje de error de no está disponible.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)   
 [Control de excepciones](../../mfc/exception-handling-in-mfc.md)




