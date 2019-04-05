---
title: Definir procedimientos almacenados
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 0f4c4ad84abf2a5de2cdf09e7064396ea01eeebe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035051"
---
# <a name="defining-stored-procedures"></a>Definir procedimientos almacenados

Antes de llamar a un procedimiento almacenado, primero debe definir, mediante el [DEFINE_COMMAND](../../data/oledb/define-command.md) macro. Al definir el comando, denotar los parámetros con un signo de interrogación (?) como marcador de parámetro:

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
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

El ejemplo anterior define un procedimiento almacenado conforme avanza. Normalmente, para una reutilización eficiente de código, una base de datos contiene un conjunto de procedimientos almacenados predefinidos con nombres como `Sales by Year` o `dt_adduserobject`. Puede ver sus definiciones mediante el Administrador corporativo de SQL Server. ¿Como se indica a continuación llamarlos (la posición de la *?* parámetros dependen interfaz del procedimiento almacenado):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
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

[Utilizar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)