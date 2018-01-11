---
title: Definir procedimientos almacenados | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3aea2503fe08c5cd7e81afd0c185f48082d41e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="defining-stored-procedures"></a>Definir procedimientos almacenados
Antes de llamar a un procedimiento almacenado, primero debe definir, mediante el [DEFINE_COMMAND](../../data/oledb/define-command.md) macro. Al definir el comando, denote los parámetros con un signo de interrogación (?) como marcador de parámetro:  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 Tenga en cuenta que la sintaxis (el uso de llaves etc.) que se utilizan en los ejemplos de código de este tema es específica de SQL Server. La sintaxis que se utiliza en los procedimientos almacenados puede variar según el proveedor que utilice.  
  
 A continuación, en la asignación de parámetros, especifique los parámetros que usan en el comando, enumerar los parámetros en el orden en que se producen en el comando:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 En el ejemplo anterior se define un procedimiento almacenado a medida que pasa. Normalmente, para una reutilización eficiente del código, una base de datos contiene un conjunto de procedimientos almacenados predefinidos con nombres tales como "Sales by Year" o "dt_adduserobject". Puede ver sus definiciones mediante el Administrador corporativo de SQL Server. Como se indica a continuación llamarlos (la colocación de la '?' parámetros depende de la interfaz del procedimiento almacenado):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 A continuación, declare la clase de comando:  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor> >  
```  
  
 Por último, llame al procedimiento almacenado `OpenRowset` como se indica a continuación:  
  
```  
CSession m_session;  
HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor> >::Open(m_session);  
}  
```  
  
 Tenga en cuenta también que puede definir un procedimiento almacenado mediante el atributo de base de datos [db_command](../../windows/db-command.md) como se indica a continuación:  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>Vea también  
 [Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)