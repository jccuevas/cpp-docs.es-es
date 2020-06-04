---
title: Definir procedimientos almacenados
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 9bab086bf6982eae5779d3199cfd2ac2c8efe77f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211009"
---
# <a name="defining-stored-procedures"></a>Definir procedimientos almacenados

Antes de llamar a un procedimiento almacenado, primero debe definirlo mediante la macro [DEFINE_COMMAND](../../data/oledb/define-command.md) . Al definir el comando, denote los parámetros con un signo de interrogación (?) como marcador de parámetro:

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
```

La sintaxis (el uso de llaves, etc.) utilizada en los ejemplos de código de este tema es específica de SQL Server. La sintaxis que se usa en los procedimientos almacenados puede variar según el proveedor que se use.

A continuación, en la asignación de parámetros, especifique los parámetros que usó en el comando, enumerando los parámetros en el orden en que se producen en el comando:

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param
END_PARAM_MAP()
```

En el ejemplo anterior se define un procedimiento almacenado tal y como se va. Normalmente, para una reutilización eficaz del código, una base de datos contiene un conjunto de procedimientos almacenados predefinidos con nombres como `Sales by Year` o `dt_adduserobject`. Puede ver sus definiciones mediante SQL Server Enterprise Manager. Puede llamarlos como se indica a continuación (la ubicación del *?* los parámetros dependen de la interfaz del procedimiento almacenado):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
```

A continuación, declare la clase de comando:

```cpp
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>
```

Por último, llame al procedimiento almacenado en `OpenRowset` como se indica a continuación:

```cpp
CSession m_session;

HRESULT OpenRowset()
{
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);
}
```

Tenga en cuenta también que puede definir un procedimiento almacenado mediante el atributo de base de datos [db_command](../../windows/db-command.md) como se indica a continuación:

```cpp
db_command("{ ? = CALL dbo.dt_adduserobject }")
```

## <a name="see-also"></a>Consulte también

[Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)
