---
title: "CException Class | Microsoft Docs"
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
  - "CException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchiveException class, clase base"
  - "CDaoException class, clase base"
  - "CDBException class, clase base"
  - "CException class"
  - "CFileException class, clase base"
  - "CInternetException class, clase base"
  - "CMemoryException class, clase base"
  - "CNotSupportedException class, clase base"
  - "COleDispatchException class, clase base"
  - "COleException class, clase base"
  - "CResourceException class, clase base"
  - "CUserException class"
  - "excepciones, classes for"
  - "macros, control de excepciones"
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
caps.latest.revision: 22
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base para todas las excepciones en la biblioteca Microsoft Foundation Class.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE CException : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CException::CException](../Topic/CException::CException.md)|Crea un objeto `CException`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CException::Delete](../Topic/CException::Delete.md)|elimina un objeto de `CException` .|  
|[CException::ReportError](../Topic/CException::ReportError.md)|Informes un mensaje de error en un cuadro de mensaje al usuario.|  
  
## Comentarios  
 Dado que `CException` es una clase base abstracta no pueden crear objetos de `CException` directamente; debe crear objetos de clases derivadas.  Si necesita crear dispone `CException`\- la clase de estilo, utilice una de las clases derivadas enumeradas anteriormente como modelo.  Asegúrese de que la clase derivada también use `IMPLEMENT_DYNAMIC`.  
  
 Las clases derivadas y sus descripciones se muestran a continuación:  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|una clase base para las excepciones recurso\-críticas de MFC|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Condición de excepción de argumento no válido|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|excepción de memoria insuficiente|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Solicitud de una operación no compatibles|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|excepción específica de los archivos|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|excepción específica de los archivos|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Recursos de Windows no encontrado no pueden crearse|  
|[COleException](../../mfc/reference/coleexception-class.md)|Excepción\)|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|Excepción de la base de datos \(es decir, condiciones de excepción procedente de las clases de base de datos MFC basadas en Open Database Connectivity\)|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Excepción OLE de envío \(automatización\)|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|Excepción que indica que un recurso no se encontró|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Excepción del objeto de acceso a datos \(es decir, condiciones de excepción procedente de las clases DAO\)|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Excepción de internet \(es decir, condiciones de excepción procedente de las clases de internet\).|  
  
 Estas excepciones se utilizadas con macros de [THROW](../Topic/THROW%20\(MFC\).md), de [THROW\_LAST](../Topic/THROW_LAST.md), de [INTENTO](../Topic/TRY.md), de [CATCH](../Topic/CATCH.md), de [AND\_CATCH](../Topic/AND_CATCH.md), y de [END\_CATCH](../Topic/END_CATCH.md) .  Para obtener más información sobre excepciones, vea [Procesamiento de excepciones](../../mfc/reference/exception-processing.md), o vea el artículo [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md).  
  
 Para detectar una excepción específica, utilice la clase derivada adecuada.  Para detectar todos los tipos de excepciones, utilice `CException`, y utilice [CObject:: IsKindOf](../Topic/CObject::IsKindOf.md) para distinguir entre `CException`\- clases derivadas.  Observe que `CObject::IsKindOf` sólo funciona para las clases declaradas con la macro de [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md) , aprovechar de comprobación de tipo dinámico.  Cualquier `CException`\- la clase derivada que cree debe utilizar la macro de `IMPLEMENT_DYNAMIC` , también.  
  
 Puede enviar los detalles sobre excepciones al usuario llamando a [GetErrorMessage](../Topic/CFileException::GetErrorMessage.md) o [ReportError](../Topic/CException::ReportError.md), dos funciones miembro que funcionen con ninguna de las clases derivadas de los entity\_CException.  
  
 Si se detecta una excepción por una de las macros, el objeto de `CException` se elimina automáticamente; no lo elimine personalmente.  Si una excepción se detecta mediante una palabra clave de **Catch** , no se elimina automáticamente.  Vea el artículo [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md) para obtener más información sobre cuándo se debe eliminar un objeto de exeption.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CException`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Procesamiento de excepciones](../../mfc/reference/exception-processing.md)   
 [Cómo se hago: ¿Cree mis clases de excepción personalizadas de Own?](http://go.microsoft.com/fwlink/?LinkId=128045)