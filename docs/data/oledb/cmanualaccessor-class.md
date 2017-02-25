---
title: "CManualAccessor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CManualAccessor"
  - "ATL.CManualAccessor"
  - "CManualAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CManualAccessor (clase)"
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CManualAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un tipo de descriptor de acceso diseñado para el uso avanzado.  
  
## Sintaxis  
  
```  
class CManualAccessor : public CAccessorBase  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|Agrega una entrada de enlace a las columnas de salida.|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|Agrega una entrada de parámetro al descriptor de parámetro.|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|Asigna memoria para las estructuras de enlace de columna e inicializa los miembros de datos de columna.|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|Asigna memoria para las estructuras de enlace de parámetro e inicializa los miembros de datos de parámetro.|  
  
## Comentarios  
 Mediante `CManualAccessor`, puede especificar el parámetro y representar el enlace de columna mediante llamadas de función en tiempo de ejecución.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor \(Clase\)](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)