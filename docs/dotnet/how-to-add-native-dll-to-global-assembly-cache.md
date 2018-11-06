---
title: 'Cómo: Agregar un archivo DLL nativo a la memoria caché global de ensamblados'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: 1b11ebfae704ca1529113a00b463df728c85fe60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641368"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Cómo: Agregar un archivo DLL nativo a la memoria caché global de ensamblados

Puede colocar un archivo DLL nativo (no COM) en la caché Global de ensamblados.

## <a name="example"></a>Ejemplo

**/ASSEMBLYLINKRESOURCE** le permite incrustar un archivo DLL nativo en un ensamblado.

Para obtener más información, consulte [/ASSEMBLYLINKRESOURCE (vincular a recursos de .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)