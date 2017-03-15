---
title: Clase CUserException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [C++], stopping
- exceptions, throwing
- CUserException class
- errors [C++], trapping
- operations [C++]
- throwing exceptions, stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 23
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 8548ffa7ad9032e174d650e210a70a29b0e3f19d
ms.lasthandoff: 02/24/2017

---
# <a name="cuserexception-class"></a>Clase CUserException
Se inicia para detener una operación de usuario final.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CUserException : public CSimpleException  
```  
  
## <a name="remarks"></a>Comentarios  
 Utilice `CUserException` cuando desee utilizar el mecanismo de excepción catch y throw de las excepciones específicas de la aplicación. "Usuario" en el nombre de clase puede interpretarse como "Mi usuario hizo algo excepcional que debo controlar".  
  
 Un `CUserException` generalmente se produce después de llamar a la función global `AfxMessageBox` para notificar al usuario que ha fallado una operación. Al escribir un controlador de excepciones, controle la excepción, especialmente desde que el usuario normalmente ya ha informado de error. El marco de trabajo produce esta excepción en algunos casos. Para producir un `CUserException` usted mismo, notificar al usuario y, a continuación, llame a la función global `AfxThrowUserException`.  
  
 En el ejemplo siguiente, una función que contengan operaciones que no se avisa al usuario y genera un `CUserException`. La función de llamada detecta la excepción y encarga de especialmente:  
  
 [!code-cpp[NVC_MFCExceptions&#24;](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]  
  
 Para obtener más información sobre el uso de `CUserException`, vea el artículo [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CException (clase)](../../mfc/reference/cexception-class.md)

