---
title: "CUserException Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUserException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserException class"
  - "errores [C++], interceptar"
  - "excepciones, iniciar"
  - "operations [C++]"
  - "operations [C++], detener"
  - "producir excepciones, stopping user operations"
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUserException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se produce para detener una operación del usuario final.  
  
## Sintaxis  
  
```  
class CUserException : public CSimpleException  
```  
  
## Comentarios  
 Utilice `CUserException` cuando desee utilizar el mecanismo de excepción throw\/catch de las excepciones específicas de la aplicación. "  El usuario” en el nombre de clase puede interpretarse como “mi usuario hace algo pendiente que necesito controlar”.  
  
 `CUserException` se produce normalmente después de llamar a la función global `AfxMessageBox` para notificar al usuario que hay un error en una operación.  Cuando se escribe un controlador de excepciones, controle la excepción especialmente puesto que han notificado al usuario normalmente ya de error.  El marco de trabajo produce esta excepción en algunos casos.  Para iniciar `CUserException` personalmente, avise al usuario y llame a la función global `AfxThrowUserException`.  
  
 En el ejemplo siguiente, una función que contiene operaciones que pueden fallar avisa al usuario y producen `CUserException`.  La función de llamada detecta la excepción y la controla especialmente:  
  
 [!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/CPP/cuserexception-class_1.cpp)]  
  
 Para obtener más información sobre cómo utilizar `CUserException`, vea el artículo [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [AfxMessageBox](../Topic/AfxMessageBox.md)   
 [AfxThrowUserException](../Topic/AfxThrowUserException.md)   
 [Cómo se hago: ¿Cree mis clases de excepción personalizadas de Own?](http://go.microsoft.com/fwlink/?LinkId=128045)