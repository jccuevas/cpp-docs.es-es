---
title: Usar ensamblados comprobables con SQL Server (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dfe64e627fd3ca37ab1e1d2d820cafaf3a6a4258
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199970"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Utilizar ensamblados comprobables con SQL Server (C++/CLI)
Procedimientos almacenados extendidos, empaquetados como bibliotecas de vínculos dinámicos (DLL), proporcionan una forma de ampliar la funcionalidad de SQL Server a través de funciones desarrolladas con Visual C++. Los procedimientos almacenados extendidos se implementan como funciones en archivos DLL. Además de las funciones, también pueden definir los procedimientos almacenados extendidos [tipos definidos por el usuario](../cpp/classes-and-structs-cpp.md) y [funciones de agregado](https://msdn.microsoft.com/de255454-f45e-4281-81f9-bc61893ac5da) (como SUM o AVG).  
  
 Cuando un cliente ejecuta un procedimiento almacenado extendido, SQL Server busca el archivo DLL asociado con el procedimiento almacenado extendido y carga el archivo DLL. SQL Server llama al procedimiento almacenado extendido solicitado y lo ejecuta en un contexto de seguridad especificado. El procedimiento almacenado extendido, a continuación, los conjuntos de resultados de las pasadas y devuelve parámetros al servidor.  
  
 SQL Server proporciona extensiones a Transact-SQL (T-SQL) para que pueda instalar a los ensamblados comprobables en SQL Server. El conjunto de permisos de SQL Server especifica el contexto de seguridad, con los siguientes niveles de seguridad:  
  
-   Modo no restringido: ejecutar código bajo su propia responsabilidad; código no tiene que ser de tipos comprobable.  
  
-   Modo seguro: ejecutar puede comprobar el código de seguridad de tipos; compilar con/CLR: safe.  
  
 Modo seguro requiere que los ensamblados ejecutados tengan seguridad de tipos comprobable.  
  
 Para crear y cargar un ensamblado comprobable en SQL Server, use los comandos CREATE ASSEMBLY y DROP ASSEMBLY de Transact-SQL como sigue:  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 El comando PERMISSION_SET especifica el contexto de seguridad y puede tener los valores UNRESTRICTED, SAFE o EXTENDED.  
  
 Además, puede usar el comando CREATE FUNCTION para enlazar a los nombres de método en una clase:  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## <a name="example"></a>Ejemplo  
 El siguiente script SQL (por ejemplo, "MyScript.sql" con nombre) carga un ensamblado en SQL Server y pone a disposición un método de una clase:  
  
```  
-- Create assembly without external access  
drop assembly stockNoEA  
go  
create assembly stockNoEA  
from   
'c:\stockNoEA.dll'  
with permission_set safe  
  
-- Create function on assembly with no external access  
drop function GetQuoteNoEA  
go  
create function GetQuoteNoEA(@sym nvarchar(10))  
returns real  
external name stockNoEA:StockQuotes::GetQuote  
go  
  
-- To call the function  
select dbo.GetQuoteNoEA('MSFT')  
go  
```  
  
 Secuencias de comandos SQL se pueden ejecutar interactivamente en el analizador de consultas SQL o en la línea de comandos con la utilidad sqlcmd.exe. La siguiente línea de comandos se conecta a MyServer, utiliza la base de datos de forma predeterminada, usa una conexión de confianza, introduce MyScript.sql y genera MyResult.txt.  
  
```  
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt  
```  
  
## <a name="see-also"></a>Vea también  
 [Cómo: migrar a/CLR: safe (C++ / c++ / CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Clases y structs](../cpp/classes-and-structs-cpp.md)