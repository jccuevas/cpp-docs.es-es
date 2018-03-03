---
title: Clase CUserException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4613f2ba06ffa697df219172b98a5cf193c1f3b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cuserexception-class"></a>Clase CUserException
Se inicia para detener una operación de usuario final.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CUserException : public CSimpleException  
```  
  
## <a name="remarks"></a>Comentarios  
 Usar `CUserException` cuando desee usar el mecanismo de excepción catch y throw de las excepciones específicas de la aplicación. "Usuario" en el nombre de clase puede interpretarse como "Mi usuario hacía algo excepcional de que se necesita administrar".  
  
 A `CUserException` generalmente se produce después de llamar a la función global `AfxMessageBox` para notificar al usuario que ha fallado una operación. Cuando se escribe un controlador de excepciones, controlar la excepción especial, puesto que el usuario normalmente ya ha informado de error. El marco de trabajo produce esta excepción en algunos casos. Para producir un `CUserException` usted mismo, notificar al usuario y, a continuación, llame a la función global `AfxThrowUserException`.  
  
 En el ejemplo siguiente, se advierte al usuario una función que contengan operaciones que pueden producir un error y produce una `CUserException`. La función de llamada detecta la excepción y la controla, especialmente:  
  
 [!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]  
  
 Para obtener más información sobre el uso de `CUserException`, vea el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)
