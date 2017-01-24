---
title: "Utilizar ensamblados comprobables con SQL Server (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ensamblados comprobables [C++], con SQL Server"
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar ensamblados comprobables con SQL Server (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los procedimientos almacenados extendidos, empaquetados como bibliotecas de vínculos dinámicos \(archivos DLL\), constituyen una manera de extender la funcionalidad de SQL Server a través de funciones desarrolladas con [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  Estos procedimientos se implementan como funciones en los archivos DLL.  Además de las funciones, los procedimientos almacenados extendidos también pueden definir [tipos definidos por el usuario](../cpp/classes-and-structs-cpp.md) y [funciones de agregado](http://msdn.microsoft.com/es-es/de255454-f45e-4281-81f9-bc61893ac5da) \(como SUM o AVG\).  
  
 Cuando un cliente ejecuta un procedimiento de este tipo, SQL Server busca el archivo DLL asociado a él y lo carga.  SQL Server llama al procedimiento almacenado extendido solicitado y lo ejecuta en un contexto de seguridad especificado.  A continuación, el procedimiento almacenado extendido pasa conjuntos de resultados y devuelve parámetros al servidor.  
  
 [!INCLUDE[sqprsqlong](../dotnet/includes/sqprsqlong_md.md)] proporciona extensiones a Transact\-SQL \(T\-SQL\) para que se puedan instalar ensamblados comprobables en SQL Server.  El conjunto de permisos de SQL Server especifica el contexto de seguridad, con los siguientes niveles:  
  
-   Modo no restringido: el código se ejecuta bajo su responsabilidad; no tiene por qué tener seguridad de tipos comprobable.  
  
-   Modo seguro: el código se ejecuta con seguridad de tipos comprobable; se compila con \/clr:safe.  
  
 El modo seguro requiere que los ensamblados ejecutados tengan seguridad de tipos comprobable.  
  
 Para crear y cargar un ensamblado comprobable en SQL Server, utilice los comandos de Transact\-SQL CREATE ASSEMBLY y DROP ASSEMBLY como se indica a continuación:  
  
```  
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH   
  PERMISSION_SET <permissions>  
DROP ASSEMBLY <assemblyName>  
```  
  
 El comando PERMISSION\_SET especifica el contexto de seguridad y puede tener los valores UNRESTRICTED, SAFE o EXTENDED.  
  
 Además, puede utilizar el comando CREATE FUNCTION para enlazar a nombres de método de una clase:  
  
```  
CREATE FUNCTION <FunctionName>(<FunctionParams>)  
RETURNS returnType  
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]  
```  
  
## Ejemplo  
 El script SQL siguiente \(por ejemplo, "MyScript.sql" con nombre\) carga un ensamblado en SQL Server y pone a disposición un método de una clase:  
  
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
  
 Los scripts SQL se pueden ejecutar interactivamente en el Analizador de consultas SQL o en la línea de comandos con la utilidad sqlcmd.exe.  La línea de comandos siguiente conecta a MyServer, utiliza la base de datos predeterminada, utiliza una conexión de confianza, especifica MyScript.sql y genera MyResult.txt.  
  
```  
sqlcmd –S MyServer -E –i myScript.sql –o myResult.txt  
```  
  
## Vea también  
 [Cómo: Migrar a \/clr:safe](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)   
 [Clases y structs](../cpp/classes-and-structs-cpp.md)