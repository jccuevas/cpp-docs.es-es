---
title: Utilizar ensamblados comprobables con SQL Server (C++ / CLI) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d03d54dd52f95f3fbba35bb896594e90aa92e867
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>Utilizar ensamblados comprobables con SQL Server (C++/CLI)
Procedimientos almacenados extendidos, empaquetados como bibliotecas de vínculos dinámicos (DLL), proporcionan una manera de ampliar la funcionalidad de SQL Server a través de funciones desarrolladas con Visual C++. Los procedimientos almacenados extendidos se implementan como funciones en archivos DLL. Además de las funciones, pueden definir los procedimientos almacenados extendidos [tipos definidos por el usuario](../cpp/classes-and-structs-cpp.md) y [las funciones de agregado](http://msdn.microsoft.com/en-us/de255454-f45e-4281-81f9-bc61893ac5da) (como SUM o AVG).  
  
 Cuando un cliente ejecuta un procedimiento almacenado extendido, SQL Server busca el archivo DLL asociado con el procedimiento almacenado extendido y carga el archivo DLL. SQL Server llama al procedimiento almacenado extendido solicitado y lo ejecuta en un contexto de seguridad especificado. El procedimiento almacenado extendido, a continuación, conjuntos de resultados de pasadas y devuelven parámetros al servidor.  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)]Proporciona extensiones a Transact-SQL (T-SQL) para que pueda instalar a ensamblados comprobables en SQL Server. El conjunto de permisos de SQL Server especifica el contexto de seguridad, con los siguientes niveles de seguridad:  
  
-   Modo no restringido: ejecutar código bajo su responsabilidad; código no tiene que tener seguridad de tipos comprobable.  
  
-   Modo seguro: comprobable ejecutar código de seguridad de tipos; compilar con/CLR: safe.  
  
 Modo seguro requiere que los ensamblados ejecutados tengan seguridad de tipos comprobable.  
  
 Para crear y cargar un ensamblado comprobable en SQL Server, use los comandos de Transact-SQL CREATE ASSEMBLY y DROP ASSEMBLY como se indica a continuación:  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 El comando PERMISSION_SET especifica el contexto de seguridad y puede tener los valores UNRESTRICTED, SAFE o EXTENDIDOS.  
  
 Además, puede utilizar el comando CREATE FUNCTION para enlazar a los nombres de método en una clase:  
  
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
 [Cómo: migrar a/CLR: safe (C++ / CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Clases y structs](../cpp/classes-and-structs-cpp.md)