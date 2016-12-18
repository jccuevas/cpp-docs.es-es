---
title: "Conversi&#243;n boxing (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversi&#243;n boxing (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La conversión boxing es el proceso de convertir un tipo de valor al tipo `object` o a cualquier tipo de interfaz que es implementado por el tipo de valor.  Cuando los cuadros de \(CLR\) de Common Language Runtime un tipo de valor, se ajustan el valor en `System.Object` y se almacenan en el montón administrado.  La conversión unboxing extrae el tipo de valor del objeto.  La conversión boxing es implícita y la conversión unboxing es explícita.  
  
## Artículos relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)|Describe cómo aplicar explícitamente la conversión boxing en una variable.|  
|[Cómo: Usar gcnew para crear tipos de valor y usar la conversión boxing implícita](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Muestra cómo utilizar `gcnew` para crear un tipo de valor de conversión boxing que puede estar en el montón administrado, basura\- obtenida.|  
|[Cómo: Aplicar la conversión unboxing](../dotnet/how-to-unbox.md)|Muestra cómo unbox y modificar un valor.|  
|[Conversiones estándar y conversión boxing implícita](../dotnet/standard-conversions-and-implicit-boxing.md)|Muestra una conversión estándar es elegida por el compilador sobre una conversión que requiere la conversión boxing.|  
|[Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|El caso de nivel superior de .NET que programa en la documentación de Visual C\+\+.|