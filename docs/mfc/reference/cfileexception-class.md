---
title: "CFileException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFile class, exceptions of"
  - "CFileException class"
  - "excepciones, file type"
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CFileException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

representa una condición de excepción archivo\-relacionada.  
  
## Sintaxis  
  
```  
class CFileException : public CException  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileException::CFileException](../Topic/CFileException::CFileException.md)|Crea un objeto `CFileException`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileException::ErrnoToException](../Topic/CFileException::ErrnoToException.md)|Devuelve el código de la causa correspondiente a un número de error en tiempo de ejecución.|  
|[CFileException::GetErrorMessage](../Topic/CFileException::GetErrorMessage.md)|Recupera el mensaje que describe la excepción.|  
|[CFileException::OsErrorToException](../Topic/CFileException::OsErrorToException.md)|Devuelve un código de la causa correspondiente a un código de error del sistema operativo.|  
|[CFileException::ThrowErrno](../Topic/CFileException::ThrowErrno.md)|Produce una excepción de archivo basada en un número de error de tiempo de ejecución.|  
|[CFileException::ThrowOsError](../Topic/CFileException::ThrowOsError.md)|Produce una excepción de archivo basada en un número de error del sistema operativo.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFileException::m\_cause](../Topic/CFileException::m_cause.md)|Contiene código portable correspondiente a la causa de la excepción.|  
|[CFileException::m\_lOsError](../Topic/CFileException::m_lOsError.md)|Contiene el número de error relacionado del sistema operativo.|  
|[CFileException::m\_strFileName](../Topic/CFileException::m_strFileName.md)|Contiene el nombre del archivo de esta excepción.|  
  
## Comentarios  
 La clase de `CFileException` incluye miembros de datos públicos que contienen el código portable de la causa y el número de error funcionamiento\-sistema\-específico.  La clase también proporciona funciones miembro estáticas de las excepciones de archivo que producen y devolver los códigos de la causa de los errores del sistema operativo y los errores en tiempo de ejecución de C.  
  
 los objetos de`CFileException` se construyen y se producen en funciones miembro de `CFile` y en funciones miembro de clases derivadas.  Puede tener acceso a estos objetos dentro del ámbito de una expresión de **CATCH** .  Para la portabilidad, utilice sólo el código de la causa para obtener la causa de una excepción.  Para obtener más información sobre excepciones, vea el artículo [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Procesamiento de excepciones](../../mfc/reference/exception-processing.md)