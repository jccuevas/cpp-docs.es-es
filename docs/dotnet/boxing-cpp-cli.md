---
title: Conversión boxing (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: df0e220c4f744e78aa5bedce4f956b726f524ff4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208842"
---
# <a name="boxing-ccli"></a>Conversión boxing (C++/CLI)

La conversión boxing es el proceso de convertir un tipo de valor al tipo `object` o a cualquier tipo de interfaz implementado por el tipo de valor. Cuando el Common Language Runtime (CLR) de un tipo de valor, ajusta el valor en un `System.Object` y lo almacena en el montón administrado. La conversión unboxing extrae el tipo de valor del objeto. La conversión boxing es implícita y la conversión unboxing es explícita.

## <a name="related-articles"></a>Artículos relacionados

|Título|Descripción|
|-----------|-----------------|
|[Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)|Describe cómo solicitar explícitamente la conversión boxing en una variable.|
|[Cómo: Usar gcnew para crear tipos de valor y usar la conversión boxing implícita](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Muestra cómo utilizar `gcnew` para crear un tipo de valor con conversión boxing que se puede colocar en el montón administrado, de recolección de elementos no utilizados.|
|[Cómo: Aplicar la conversión unboxing](../dotnet/how-to-unbox.md)|Muestra cómo hacer una conversión unboxing y modificar un valor.|
|[Conversiones estándar y conversión boxing implícita](../dotnet/standard-conversions-and-implicit-boxing.md)|Muestra que el compilador elige una conversión estándar en una conversión que requiere conversión boxing.|
|[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Artículo de nivel superior para la programación de .NET en la C++ documentación visual.|
