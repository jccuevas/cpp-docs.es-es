---
title: "Procesamiento de excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO (objetos de acceso a datos), excepciones"
  - "macros de excepción"
  - "excepciones, iniciar funciones MFC"
  - "excepciones, procesar"
  - "macros, control de excepciones"
  - "MFC, excepciones"
  - "excepciones OLE, MFC (funciones)"
  - "funciones de finalización, MFC"
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
caps.latest.revision: 16
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procesamiento de excepciones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando un programa se ejecuta, varias condiciones irregulares y errores denominados “las excepciones” pueden aparecer.  Éstos pueden incluir la ejecución memoria insuficiente, los errores de asignación de recursos, y de error de buscar archivos.  
  
 La biblioteca Microsoft Foundation Class utiliza un esquema excepción\- que administra que se modela estrechamente después de que se propuesto por el comité de normas ANSI para C\+\+.  Un controlador de excepciones se debe configurar antes de llamar a una función que pueda encontrar una situación anómala.  Si la función encuentra una condición irregular, produce una excepción y el control se pasa al controlador de excepciones.  
  
 Varias macros incluidas con la biblioteca Microsoft Foundation Class configurar los controladores de excepciones.  Otras funciones globales ayudan a producir excepciones especializadas y a finalizar los programas, en caso necesario.  Estas macros y funciones globales se dividen en las categorías siguientes:  
  
-   [Macros de excepción](#_mfc_exception_macros), que estructura el controlador de excepciones.  
  
-   [funciones Excepción\- que producen](#_mfc_exception.2d.throwing_functions), que generan excepciones de tipos específicos.  
  
-   [Funciones de finalización](#_mfc_termination_functions), que producen la finalización del programa.  
  
 Para obtener ejemplos y más detalles, vea el artículo [Excepciones](../../mfc/exception-handling-in-mfc.md).  
  
### Macros de excepción  
  
|||  
|-|-|  
|[TRY](../Topic/TRY.md)|Elija un bloque de código para el procesamiento de la excepción.|  
|[CATCH](../Topic/CATCH.md)|Elija un bloque de código para detectar una excepción de bloque anterior de **TRY** .|  
|[CATCH\_ALL](../Topic/CATCH_ALL.md)|Elija un bloque de código para detectar todas las excepciones de bloque anterior de **TRY** .|  
|[AND\_CATCH](../Topic/AND_CATCH.md)|Elija un bloque de código para detectar tipos de excepción adicionales de bloque anterior de **TRY** .|  
|[AND\_CATCH\_ALL](../Topic/AND_CATCH_ALL.md)|Elija un bloque de código para detectar todos los demás tipos de excepción adicionales lanzados en un bloque anterior de **TRY** .|  
|[END\_CATCH](../Topic/END_CATCH.md)|Finaliza **CATCH** o el bloque de código último de `AND_CATCH` .|  
|[END\_CATCH\_ALL](../Topic/END_CATCH_ALL.md)|Finaliza el bloque de código último de `CATCH_ALL` .|  
|[THROW](../Topic/THROW%20\(MFC\).md)|Produce una excepción especificada.|  
|[THROW\_LAST](../Topic/THROW_LAST.md)|Produce la excepción actualmente controla el controlador externo siguiente.|  
  
### Funciones Excepción\- que producen  
  
|||  
|-|-|  
|[AfxThrowArchiveException](../Topic/AfxThrowArchiveException.md)|Produce una excepción del archivo.|  
|[AfxThrowFileException](../Topic/AfxThrowFileException.md)|Produce una excepción del archivo.|  
|[AfxThrowMemoryException](../Topic/AfxThrowMemoryException.md)|Produce una excepción de memoria insuficiente.|  
|[AfxThrowNotSupportedException](../Topic/AfxThrowNotSupportedException.md)|Produce una excepción no admitida.|  
|[AfxThrowResourceException](../Topic/AfxThrowResourceException.md)|Produce una excepción recurso\-no\- encontró Windows.|  
|[AfxThrowUserException](../Topic/AfxThrowUserException.md)|Produce una excepción en una acción usuario\- encargado del programa.|  
  
 MFC proporciona dos funciones excepción\- que producen específicamente para las excepciones VIEJAS:  
  
### Funciones VIEJAS de excepción  
  
|||  
|-|-|  
|[AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md)|Produce una excepción dentro de una función de automatización OLE.|  
|[AfxThrowOleException](../Topic/AfxThrowOleException.md)|Produce una excepción\).|  
  
 Para admitir excepciones de base de datos, las clases de base de datos proporcionan dos clases de excepción, `CDBException` y `CDaoException`, y las funciones globales para admitir los tipos de excepción:  
  
### Funciones de excepción de DAO  
  
|||  
|-|-|  
|[AfxThrowDAOException](../Topic/AfxThrowDaoException.md)|Produce [CDaoException](../../mfc/reference/cdaoexception-class.md) del propio código.|  
|[AfxThrowDBException](../Topic/AfxThrowDBException.md)|Produce [CDBException](../../mfc/reference/cdbexception-class.md) del propio código.|  
  
 MFC proporciona la siguiente función de finalización:  
  
### Funciones de finalización  
  
|||  
|-|-|  
|[AfxAbort](../Topic/AfxAbort.md)|Denominado para finalizar una aplicación cuando un error irrecuperable aparece.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException Class](../../mfc/reference/cexception-class.md)