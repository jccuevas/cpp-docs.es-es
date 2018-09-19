---
title: Conversión boxing (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3b9898b4a640d2f3aa4e38ceb621521ffb301fed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105896"
---
# <a name="boxing-ccli"></a>Conversión boxing (C++/CLI)
La conversión boxing es el proceso de convertir un tipo de valor al tipo `object` o a cualquier tipo de interfaz que implementa el tipo de valor. Cuando common language runtime (CLR) cuadros de un tipo de valor, ajusta el valor de un `System.Object` y lo almacena en el montón administrado. La conversión unboxing extrae el tipo de valor del objeto. La conversión boxing es implícita y la conversión unboxing es explícita.  
  
## <a name="related-articles"></a>Artículos relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)|Describe cómo solicitar explícitamente la conversión boxing en una variable.|  
|[Cómo: Usar gcnew para crear tipos de valor y usar la conversión boxing implícita](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Muestra cómo utilizar `gcnew` para crear un tipo de valor con conversión boxing que puede colocarse en el montón administrado, recolección.|  
|[Cómo: Aplicar la conversión unboxing](../dotnet/how-to-unbox.md)|Muestra cómo aplicar la conversión unboxing y modificar un valor.|  
|[Conversiones estándar y conversión boxing implícita](../dotnet/standard-conversions-and-implicit-boxing.md)|Muestra que el compilador elige una conversión estándar a través de una conversión que requiere la conversión boxing.|  
|[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|El artículo de nivel superior para la programación de .NET en la documentación de Visual C++.|