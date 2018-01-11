---
title: Acceso a datos mediante ADO.NET (C++ / CLI) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fb7d184ebdb537c02b79a412d69a4bdcaabde424
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="data-access-using-adonet-ccli"></a>Acceso a datos mediante ADO.NET (C++/CLI)
ADO.NET es la API de .NET Framework para el acceso a datos y proporciona la eficacia y facilidad de uso no coincidente por las soluciones de acceso de datos anterior. Esta sección describen algunos de los problemas que afectan a ADO.NET que son únicos para los usuarios de Visual C++, como calcular referencias a tipos nativos.  
  
 ADO.NET se ejecuta bajo Common Language Runtime (CLR). Por lo tanto, cualquier aplicación que interactúe con ADO.NET también deberá estar destinada CLR. Sin embargo, eso significa que las aplicaciones nativas no puedan usar ADO.NET. Estos ejemplos muestran cómo interactuar con una base de datos ADO.NET desde código nativo.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Serializar cadenas ANSI para ADO.NET (C++/CLI)](../dotnet/how-to-marshal-ansi-strings-for-adonet-cpp-cli.md)  
  
 [Cómo: Serializar cadenas BSTR para ADO.NET (C++/CLI)](../dotnet/how-to-marshal-bstr-strings-for-adonet-cpp-cli.md)  
  
 [Cómo: Serializar cadenas Unicode para ADO.NET (C++/CLI)](../dotnet/how-to-marshal-unicode-strings-for-adonet-cpp-cli.md)  
  
 [Cómo: Serializar cadenas ANSI para ADO.NET (C++/CLI)](../dotnet/how-to-marshal-a-variant-for-adonet-cpp-cli.md)  
  
 [Cómo: Serializar una matriz SAFEARRAY de ADO.NET (C++/CLI)](../dotnet/how-to-marshal-a-safearray-for-adonet-cpp-cli.md)  
  
## <a name="related-sections"></a>Secciones relacionadas  
  
|Sección|Descripción|  
|-------------|-----------------|  
|[ADO.NET](/dotnet/framework/data/adonet/index)|Proporciona información general sobre ADO.NET, un conjunto de clases que exponen servicios de acceso a datos al programador. NET.|  
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)