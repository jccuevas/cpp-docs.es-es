---
title: Definir procedimientos almacenados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 769f2bf2c0ef6c2c92b4c0468569e91d399cea59
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808451"
---
# <a name="defining-stored-procedures"></a>Definir procedimientos almacenados

Antes de llamar a un procedimiento almacenado, primero debe definir, mediante el [DEFINE_COMMAND](../../data/oledb/define-command.md) macro. Al definir el comando, denotar los parámetros con un signo de interrogación (?) como marcador de parámetro:  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
La sintaxis (el uso de llaves etc.) utilizada en los ejemplos de código de este tema es específica de SQL Server. La sintaxis que usan en los procedimientos almacenados puede variar según el proveedor que utilice.  
  
A continuación, en la asignación de parámetros, especifique los parámetros que utilizan el comando, enumerar los parámetros en el orden que aparecen en el comando:  
  
```cpp  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
El ejemplo anterior define un procedimiento almacenado conforme avanza. Normalmente, para una reutilización eficiente de código, una base de datos contiene un conjunto de procedimientos almacenados predefinidos con nombres como "Ventas por año" o "dt_adduserobject". Puede ver sus definiciones mediante el Administrador corporativo de SQL Server. Como se indica a continuación llamarlos (la colocación de la '?' parámetros dependen de la interfaz del procedimiento almacenado):  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
A continuación, declare la clase de comando:  
  
```cpp  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
Por último, llame al procedimiento almacenado `OpenRowset` como sigue:  
  
```cpp  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
Tenga en cuenta también que puede definir un procedimiento almacenado mediante el atributo de la base de datos [db_command](../../windows/db-command.md) como sigue:  
  
```cpp  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>Vea también  

[Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)