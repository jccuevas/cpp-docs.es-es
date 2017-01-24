---
title: "CDaoException Class | Microsoft Docs"
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
  - "CDaoException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoException class"
  - "colecciones, DAO (errores)"
  - "DAO (objetos de acceso a datos), excepciones"
  - "errores [C++], DAO"
  - "Errors collection, DAO"
  - "excepciones, in MFC DAO classes"
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una condición de excepción que surge de las clases de base de datos MFC basadas en objetos \(DAO\) de acceso a datos.  
  
## Sintaxis  
  
```  
class CDaoException : public CException  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoException::CDaoException](../Topic/CDaoException::CDaoException.md)|Crea un objeto `CDaoException`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoException::GetErrorCount](../Topic/CDaoException::GetErrorCount.md)|Devuelve el número de errores en la colección de errores del motor de base de datos.|  
|[CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md)|Devuelve información de error sobre un objeto del error en la colección de errores.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoException::m\_nAfxDaoError](../Topic/CDaoException::m_nAfxDaoError.md)|Contiene un código de error extendido para cualquier error en las clases DAO de MFC.|  
|[CDaoException::m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md)|Un puntero a un objeto de [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) que contiene información sobre un objeto error de DAO.|  
|[CDaoException::m\_scode](../Topic/CDaoException::m_scode.md)|El valor de [SCODE](../Topic/CDaoException::m_scode.md) asociado al error.|  
  
## Comentarios  
 La clase incluye miembros de datos públicos que puede utilizar para determinar la causa de la excepción.  los objetos de`CDaoException` son construidos y error producidos por las funciones miembro de las clases de base de datos de DAO.  
  
> [!NOTE]
>  Las clases de base de datos de DAO son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos de DAO tienen el prefijo “CDao”.  Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO.  las clases MFC basadas en DAO son generalmente más capaces que las clases MFC basadas en ODBC; las clases DAO pueden tener acceso a los datos, incluidos mediante controladores ODBC, a través de su propio motor de base de datos.  Las operaciones admiten DAO de lenguaje de definición de datos de \(DDL\) las clases también, como tablas de suma mediante las clases, sin tener que llamar a DAO directamente.  Para obtener información sobre las excepciones producidas por las clases ODBC, vea [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Puede tener acceso a objetos de excepción dentro del ámbito de una expresión de [CATCH](../Topic/CATCH.md) .  También puede producir los objetos de `CDaoException` del propio código con la función global de [AfxThrowDaoException](../Topic/AfxThrowDaoException.md) .  
  
 en MFC, todos los errores de DAO se expresan como excepciones, de `CDaoException`escrito.  Cuando se detecta una excepción de este tipo, puede utilizar funciones miembro de `CDaoException` para recuperar información de cualquier objeto error DAO almacenado en la colección de errores del motor de base de datos.  Mientras cada error, uno o más objetos de error se colocan en la colección de errores.  \(La colección contiene normalmente sólo un objeto error; si se utiliza un origen de datos ODBC, lo más probable obtener objetos error múltiple.\) Cuando una operación de DAO genera un error, se borra la colección de errores, y el nuevo objeto de error se coloca en la colección de errores.  Las operaciones de DAO que no generan un error no tienen ningún efecto en la colección de errores.  
  
 Para los códigos de error de DAO, vea el archivo DAOERR.H.  Para obtener información relacionada, vea el tema “errores de Trappable” en la Ayuda de DAO.  
  
 Para obtener más información sobre el control de excepciones normalmente o sobre los objetos de `CDaoException` , vea los artículos [control de excepciones \(MFC\)](../../mfc/exception-handling-in-mfc.md) y [excepciones: Excepciones de base de datos](../../mfc/exceptions-database-exceptions.md).  El segundo artículo contiene código de ejemplo que muestra el control de excepciones en DAO.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [CException Class](../../mfc/reference/cexception-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)