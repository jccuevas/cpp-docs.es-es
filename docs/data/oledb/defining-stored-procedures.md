---
title: "Definir procedimientos almacenados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB, procedimientos almacenados"
  - "procedimientos almacenados, definir"
  - "procedimientos almacenados, OLE DB"
  - "procedimientos almacenados, sintaxis"
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Definir procedimientos almacenados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Antes de llamar a un procedimiento almacenado se debe definir con la macro [DEFINE\_COMMAND](../../data/oledb/define-command.md).  Cuando defina el comando, denote los parámetros con un signo de interrogación \(?\) como marcador de parámetros:  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 Observe que la sintaxis utilizada en este tema \(el uso de llaves, etc.\) en los ejemplos de código es específica de SQL Server.  La sintaxis que utilice en sus procedimientos almacenados puede variar según el proveedor que utilice.  
  
 A continuación, en el mapa de parámetros, especifique los parámetros que utilizó en el comando, enumerándolos en el mismo orden que figuran en el comando:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 El ejemplo anterior define un procedimiento almacenado a medida que se genera.  Normalmente, para una reutilización eficiente del código, la base de datos contiene un conjunto de procedimientos almacenados predefinidos con nombres tales como "Sales by Year" o "dt\_adduserobject". Puede ver sus definiciones con SQL Server Enterprise Manager.  Se invocan como sigue \(la posición de los parámetros '?' depende de la interfaz del procedimiento almacenado\):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 A continuación, declare la clase de comando:  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor> >  
```  
  
 Por último, llame al procedimiento almacenado en `OpenRowset` como sigue:  
  
```  
CSession m_session;  
HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor> >::Open(m_session);  
}  
```  
  
 Observe también que se puede definir un procedimiento almacenado con el atributo de base de datos [db\_command](../../windows/db-command.md) de la manera siguiente:  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## Vea también  
 [Utilizar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)