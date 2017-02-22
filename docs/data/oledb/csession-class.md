---
title: "CSession (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSession"
  - "ATL::CSession"
  - "ATL.CSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSession (clase)"
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CSession (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una sesión única de acceso a la base de datos.  
  
## Sintaxis  
  
```  
class CSession  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Abort](../../data/oledb/csession-abort.md)|Cancela \(null\) la transacción.|  
|[Cerrar](../../data/oledb/csession-close.md)|Cierre la sesión.|  
|[Confirmar](../../data/oledb/csession-commit.md)|Confirma la transacción.|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|Devuelve información relativa a una transacción.|  
|[Abrir](../../data/oledb/csession-open.md)|Abre una nueva sesión del objeto de origen de datos.|  
|[StartTransaction](../../data/oledb/csession-starttransaction.md)|Inicia una nueva transacción para esta sesión.|  
  
## Comentarios  
 Una o más sesiones pueden estar asociadas a cada conexión de proveedor \(origen de datos\), representada por un objeto de [CDataSource](../../data/oledb/cdatasource-class.md) .  Para crear un nuevo `CSession` para `CDataSource`, llame a [CSession::Open](../../data/oledb/csession-open.md).  Para iniciar una transacción de base de datos, `CSession` proporciona el método de `StartTransaction` .  Una vez que se inicia una transacción, puede confirmar a ella con el método de **Confirmar** , o se cancela mediante el método de **Anular** .  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [CatDB](../../top/visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)