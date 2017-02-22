---
title: "CDBException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDBException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBException class"
  - "database exceptions [C++]"
  - "errores [C++], base de datos"
  - "exceptions [C++], base de datos"
  - "clases ODBC [C++], excepciones"
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDBException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una condición de excepción que surge de las clases de base de datos.  
  
## Sintaxis  
  
```  
  
class CDBException : public CException  
  
```  
  
## Members  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDBException::m\_nRetCode](../Topic/CDBException::m_nRetCode.md)|Contiene un código de retorno de ODBC, de **RETCODE**escrito.|  
|[CDBException::m\_strError](../Topic/CDBException::m_strError.md)|Contiene una cadena que describe el error en términos alfanuméricos.|  
|[CDBException::m\_strStateNativeOrigin](../Topic/CDBException::m_strStateNativeOrigin.md)|contiene una cadena que describe el error en términos de códigos de error devueltos por ODBC.|  
  
## Comentarios  
 La clase incluye dos miembros de datos públicos que puede utilizar para determinar la causa de la excepción o mostrar un mensaje de texto que describe la excepción.  los objetos de`CDBException` son construidos y error producidos por las funciones miembro de las clases de base de datos.  
  
> [!NOTE]
>  Esta clase es una de las clases de Open Database Connectivity MFC \(ODBC\).  Si en su lugar utiliza las nuevas clases \(DAO\) de Objetos de acceso a datos, utilice [CDaoException](../../mfc/reference/cdaoexception-class.md) en su lugar.  Todos los nombres de clase DAO ofrecen “CDao” como prefijo.  Para obtener más información, vea el artículo [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 Las excepciones son casos de ejecución anómala que implican condiciones fuera del control del programa, como origen de datos o errores de E\/S de red.  Los errores que puede esperar que vean en el curso normal de ejecutar el programa normalmente no se consideran las excepciones.  
  
 Puede tener acceso a estos objetos dentro del ámbito de una expresión de **CATCH** .  También puede producir los objetos de `CDBException` del propio código con la función global de `AfxThrowDBException` .  
  
 Para obtener más información sobre el control de excepciones normalmente o sobre los objetos de `CDBException` , vea los artículos [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md) y [excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## Requisitos  
 **encabezado:** afxdb.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [AfxThrowDBException](../Topic/AfxThrowDBException.md)   
 [CRecordset::Update](../Topic/CRecordset::Update.md)   
 [CRecordset::Delete](../Topic/CRecordset::Delete.md)   
 [CException Class](../../mfc/reference/cexception-class.md)