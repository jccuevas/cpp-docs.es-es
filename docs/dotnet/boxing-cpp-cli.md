---
title: Conversión boxing (C++ / c++ / CLI) | Microsoft Docs
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
ms.openlocfilehash: 4c513b0148e2553440e02f9b0d255a0d5750e2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372517"
---
# <a name="boxing-ccli"></a>Conversión boxing (C++/CLI)

Conversión boxing es el proceso de convertir un tipo de valor al tipo `object` o a cualquier tipo de interfaz implementado por el tipo de valor. Cuando un tipo de valor de los cuadros de common language runtime (CLR), ajusta el valor en un `System.Object` y lo almacena en el montón administrado. La conversión unboxing extrae el tipo de valor del objeto. La conversión boxing es implícita y la conversión unboxing es explícita.

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)|Describe cómo solicitar explícitamente la conversión boxing en una variable.|
|[Cómo: Usar gcnew para crear tipos de valor y usar la conversión boxing implícita](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Se muestra cómo usar `gcnew` para crear un tipo de valor con conversión boxing que se puede colocar en el montón administrado, la recolección.|
|[Cómo: Aplicar la conversión unboxing](../dotnet/how-to-unbox.md)|Muestra cómo aplicar la conversión unboxing y modificar un valor.|
|[Conversiones estándar y conversión boxing implícita](../dotnet/standard-conversions-and-implicit-boxing.md)|Muestra que el compilador elige una conversión estándar a través de una conversión que requiere la conversión boxing.|
|[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|El artículo de nivel superior para la programación de .NET en la documentación de Visual C++.|